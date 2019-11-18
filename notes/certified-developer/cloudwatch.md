# CloudWatch

- Metrics: Collect and track key metrics.
- Logs: Collect, monitor, analyze, and store log files.
- Events: Send notifications when certain events happen in your AWS.
- Alarms: React in real-time to metrics / events.

Provides metrics for *every* service in AWS.

- A metric is a variable to monitor (CPUUtilization, NetworkIn, etc.).
- Metrics belong to namespaces.
- Dimension is an attribute of a metric (instance ID, environment, etc.)
- Up to 10 dimensions per metric.
- Metrics have timestamps.
- Can create CloudWatch dashboards of metrics.

By default EC2 instances have metrics every 5 minutes. With detailed monitoring (for a cost) you get data every 1 minute.

## Custom Metrics

You can define and send your own custom metrics to CloudWatch.

- Ability to use dimensions (attributes) to segment metrics.
  - Instance.id
  - Environment.name
- Metric resolution
  - Standard: 1 minute
  - High Resolution: up to 1 second (StorageResolution API parameter) - higher cost.
