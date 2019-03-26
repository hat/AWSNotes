* IAM
  * Database authentication: MySQL and PostgreSQL no password needed can use auth token
* Cloudwatch
  * Recieves and aggregates data every 5 minutes by default
* Amazon Aurora
  * Relational Database
* CIDR Block IP Addresses
  * Total IP Addresses available: Subtract 32 with the mask number, raise to power of 2
* Amazon Kinesis
  * Can load streaming data to S3, Redshift, Elasticsearch, and Splunk
* Migrate on-premise network public IPs
  * Create Route Origin Authority (ROA)
* S3 Deletion Protection
  * Enable versioning
  * Enable MFA Delete
* AMI Cross Region
  * AMIs are per region so must be copied from region to region
* SAML vs Web Identity Federation
  * SAML allows AD access
  * WIF allows popular clients (Facebook, Google, Twitter, etc..)
* RDS Enhanced Monitoring
  * Provides % of CPU bandwidth and total memory used
* SQS Processing
  * EC2 must initialize the delete process after processing the Queue
* Workload Management (WLM)
  * Can run up to 5 concurrent queries
* Enhanced VPC Routing
  * Allows features such as VPC security groups, NACLs, VPC Endpoints, IGs, DNS Servers, etc...
* EC2 Spot-Instance Pricing
  * If Amazon terminate in first hour it's free of charge: $0
* API Gateway
  * Provides throttling that is customizable
  * Allws caching by setting cache and size
* Enhanced Monitoring
  * Feature of RDS
* Auto Scaling
  * Removes EC2 instance with oldest launch configuration
* Amazon MQ
  * Supports industry-standard APIs and protocols
* AWS Lambda Deployment Configuration Types
  * Canary: traffic is shifted in two increments
  * Linear: traffic isshifted in equal increments with an equal number of minutes between each
  * All-at-once: All traffic is shifted from previous Lambda function to updated at once
* Encryption at Rest by Default
  * Storage Gateway
  * Glacier
* ELB Security Features
  * Perfect Forward Secrecy: unique random session key for seurity; supported by CloudFront and ELB
* AWS Shared Responsobility Model
  * AWS manages the security of the following assets
    * Facilities
    * Physical Security of Hardware
    * Network Infastructure
    * Virtualization Infastructure
* Attach Network Interface Card (ENI) to logical component
    * Hot attach: when it's running
    * Warm attach: when it is stopped
    * Cold attach: when instance is being launched
* AWS AppSync
    * Uses DynamoDB to keep shared data updated in real-time
* EC2 Low Latency - Placement Groups
    * Placement Groups:
      * Cluster: clusters instances into low-latency groups in single AZ
      * Spread: spreads instances across underlying hardware
* S3 Server Side Encryption
    * Use SSE with S3-Managed Keys
    * Use SSE with AWS KMS-Managed Keys
    * Use SSE with Customer-Provided Keys
* VPC Peering Configurations NOT suppoerted
    * Overlapping CIDR blocks
    * Transitive Peering
    * Edge to Edge Routing through Gateway or Private Connection
* Volume IOPS
  * 50:1 is maximum provisioned IOPs per volume; ex: 10 GiB volume up to 500 IOPS