# DynamoDB

## Provisioned Throughput

- Table must have provisioned read and write capacity units.
- Read Capacity Units (RCU): throughput for reads
- Write Capacity Units (WCU): throughput for writes
- Option to setup auto-scaling of throughput to meet demand.
- Throughput can be exceeded temporarily using "burst credit"
- If burst credit are empty, you'll get a "ProvisionedThroughputException"
- It's then advised to do an exponential back-off retry.

## Write Capacity Units

- One write capacity unit represents one write per second for an item up to 1 KB in size.
- If the items are larger than 1 KB, more WCU are consumed.
- Example 1: We write 10 objects per seconds of 2 KB each.
  - We need 2 * 10 = 20 WCU
- Example 2: We write 6 objects per second of 4.5 KB each.
  - We need 6 * 5 = 30 WCU (4.5 gets rounded to the upper KB)
- Example 3: We write 120 objects per minute of 2 KB each.
  - We need (120 / 60) * 2 = 4 WCU

## Strongly Consistent Read vs. Eventual Consistent Read

- Eventually Consistent Read: If we read just after a write, it's possible we'll get unexpected response because of replication.
- Strongly Consistent Read: If we read data just after a write, we will get the correct data.
- By default DynamoDB uses Eventually Consistent Reads, but Getltem, Query and Scan provide a "ConsistentRead" parameter you can set to True.

## Read Capacity Units 

- One read capacity unit represents one strongly consistent read per second, or two eventually consistent reads per second, for an item up to 4 KB in size.
- If the items are larger than 4 KB, more RCU are consumed. 
- Example 1: 10 strongly consistent reads per seconds of 4 KB each.
  - We need 10 * 4 KB / 4 KB = 10 RCU
- Example 2: 16 eventually consistent reads per seconds of 12 KB each
  - We need (16 / 2) * (12 / 4)  = 24 RCU
- Example 3: 10 strongly consistent reads per seconds of 6 KB each.
  - We need 10 * 8 KB / 4 = 20 RCU (we have to round up 6 KB to 8 KB)

## Partitions Internal

- Data is divided in partitions
- Partition keys go through a hashing algorithm to know to which partition they go to.
- To compute the number of partitions:
  - By capacity: (Total RCU / 3000) + (Total WCU / 1000)
  - By size: Total size / 10 GB
  - Total partitions = CEILING(MAX(Capacity, Size))
- **WCU and RCU are spread evenly between partitions**

## Throttling

- If we exceed our RCU or WCU, we get `ProvisionedThroughputExceededExceptions`
- Reasons:
  - Hot keys: one partition key is being read too many times (popular item for exam)
  - Hot partitions
  - Very large items: Remember RCU and WCU depends on size of items.
- Solutions:
  - Exponential back-off when exception is encountered (already in SDK)
  - Distribute partition keys as much as possible
  - If RCU issue, we can use DynamoDB Accelerator (DAX)

## Writing Data

- `PutItem`: Write data to DynamoDB (create data or full replace)
  - Consumes WCU
  - Can be used to update, but will do a full update. Rewrites everything.
- `UpdateItem`: Update data in DynamoDB (partial update of attributes)
  - Will only update the attributes that are updated.
  - Possibility to use Atomic Counters and increase them.
- `ConditionalWrites`
  - Accept a write / update only if conditions are respected, otherwise reject.
  - Helps with concurrent access to items
  - No performance impact
- `DeleteItem`
  - Delete an individual row
  - Ability to perform a conditional delete
- `DeleteTable`
  - Delete a whole table and all its items.
  - Much quicker deletion than calling `DeleteItem` on all items.

## Batching Writes

- `BatchWriteItem`
  - Up to 25 `PutItem` and/or `DeleteItem` in one call
  - Up to 16 MB of data written
  - Up to 400 KB of data per item
- Batching allows you to save latency by reducing the number of API calls done against DynamoDB.
- Operations are done in parallel for better efficiency.
- It's possible for part of a batch to fail, in which case we have to retry the failed items (using exponential back-off algorithm)

## Reading Data

- `GetItem`
  - Read based on primary key. Primary key = HASH or HASH-RANGE
  - Eventually consistnet read by default.
  - Option to use strongly consistent reads (more RCU - might take longer)
  - `ProjectionExpression` can be specified to include only certain attributes.
- `BatchGetItem`
  - Up to 100 items
  - Up to 16 MB of data
  - Items are retrieved in parallel to minimize latency.

## Query

- Query retruns items based on:
  - PartitionKey value (must be = operator)
  - SortKey value (=, <, <=, >, >=, Between, Begin) - optional.
  - `FilterExpression` to further filter (clinet side filtering)
- Returns:
  - Up to 1 MB of data
  - Or number of items specified in Limit.
- Able to do pagination on the results.
- Can query table, a local secondary index, or a global secondary index.

## Scan

- Scan the entire table and then filter out data. **Inefficient**
- Returns up to 1 MB of data - use pagination to keep on reading.
- Consumes a lot of RCU
- Limit impact using Limit or reduce the size of the result and pause.
- For faster performance, use parallel scans.
  - Multiple instances scan multiple partitions at the same time
  - Increases the throughput and RCU consumed
  - Limit the impact of parallel scans just like you would for scans.
- Can use a ProjectionExpression + FilterExpression (no change to RCU).
