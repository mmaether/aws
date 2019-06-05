# AWS - 10,000 Feet Overview

## Summary

This readme file has all the notes I've written as going through the *AWS - 10,000 Feet Overview* lesson. This should be a good starting point of a higher level understanding of AWS and how it functions as a whole. There will not be any in-depth knowledge here.

## Security & Identity & Compliance

- Cloud HSM stores private and public keys. Very cool.
- Macie: Notice if personal details are in S3 buckets, e.g. credit cards.
- Certificate Manager
- Directory Service: Integrate Active Directory with AWS.
- Web Application Firewall: Stops SQL injections, firewall.
- Shield: By default in Cloudfront, load balancer. DDOS mitigation. ~$3,000/month
- Artifact: Download compliance reports, audits. SOC controls. PCI.

## Mobile Services
- Mobile Hub: Management console. If you have an app it sets up AWS services for you. Use SDK to connect mobile app to this backend.
- Pinpoint: Targeted push notifications to drive mobile engagement. If you're near a restaurant, you can send a push notification saying "Here's a coupon!"
- AWS AppSync: Updates data in web and mobile data in realtime. Also off-time as soon as it reconnects. This is a newer feature.
- Device Farm: Testing apps on real devices. 
- Mobile Analytics: Analytics for mobile usage. 

## AR/VR
- Sumerian: Tools for AR/VR, in preview. Don't need to know how to build.

## Application Integration
- Step Functions: Allows you to manage Lambda functions. This is a newer feature.
- Amazon MQ: Message queues. 
- SNS: Notification service. Billing alarms. Email or phone.
- SQS: Decoupling infrastructure. Hold info in a queue, EC2 pulls and sends.
- SWF: If you order something, someone needs to find the product in the warehouse, people mark that they found it, etc. People can be involved.

## Customer Engagement
- Connect: Contact center as a service. Your own call center.
- Simple Email Service: Send large emails, scalable, cost effective.

## Business Productivity
- Alexa for Business: 
- Chime: Google hangouts or Zoom.
- Work Docs: A dropbox for AWS.
- Workmail: Office 365-ish. 

## Desktop & App Streaming
- Workspaces: Run work station in Amazon Cloud.
- AppStream 2.0: streaming applications from the cloud to your device. Similar to Citrix.

## Internet of Things
- iOT
- iOT Device Management 
- Amazon FreeRTOS
- Greengrass

## Game Development
- GameLift