# AWS

## AWS Practice Quizzes

<a href="https://www.udemy.com/">__UDEMY__</a>

<a href="https://www.whizlabs.com/">__WHIZLABS__</a>

<a href="https://quizlet.com/">__QUIZLET__</a>

## Overview
[Identity Access Management](#iam101)

[S3](#s3101)

[EC2](#ec2)

[Route 53](#route53)

[Databases on AWS](#database)

## Support Plans

* Basic - Free
* Developer - 29/mo
* Business - 100+/mo


	
## Identity Access Management 101<a name="iam101"></a>

**IAM** - allows you to manage users & roles

* Central control of AWS
* Shared access
* Granular permissions
* Identitity Federation
* Multi-factor
* Temporary access
* Custom password rotation policy
* Supports PCI DDS Compliance

**Key Terms**

* Users
* Groups
* Roles - assign to AWS Resources
* Policies - user and group policies in JSON
	
**Notes**

* IAM accounts are all global and not set to region
* New users have no permissions on creation
* New users have access key id & secret key for API

## S3_101<a name="s3101"></a>

**S3** - Object-based storage for files (block based is for servers)

* Allows uploading of files 0-5tb
* Unlimited storage paid by Gb
* Files stored in buckets (folder in the cloud)
* Each bucket has universal namespace (must be unique)
* URL https://s3-region.amazonaws.com/bucket_name
* 200 code upon sucess
* Some latency of writing of PUTS
* Simple key-value store
* Each s3 file contains version id and metadata
* Built for 99.99% availability (eleven nines durability)

**BASICS**

* Tiered storage
* Lifecycle management, versioning, and encryption
* Secure with ACLs and Bucket Policies

**Storage Tiers/ Classes**

* S3 Standard: 2 facilities concurrent loss
* S3 IA: Infrequently Accessed (low access/high speed) lower fee with retrieval fee
* S3 One Zone - IA: multiple availability one resilience not needed
* Glacier - Very cheap, archival only (standard 3-5 hours for restore)

___
* Retreival Fee. only waived in S3 Standard Tier

**S3 Tranfer Acceleration**

* fast, easy, secure transfers over long distances from S3 bucket

**S3 Versioning**

* Stores all versions even delete once enabled, can not be disabled
* Intregrates with Lifecycle rules
* Versioning MFA delete available

**CloudFront CDN**

* Uses edge locations to deliver content quicker
* Allows read & write access
* Allows S3 bucket to be set to inaccesible accept for Cloudfront access
* Geo-Restrictions - whitelist or blacklist of countries
* Invalidations - stops caching on edge locations

**S3 Security & Encryption**

* Default all S3 buckets private
* Bucket policies and ACLs for access control
* Logging available
* Encryption in Transit SSL/ TSL
* Encryption At Rest
  * **Server-Side**
  *  SSE-S3: S3 Managed keys; each object encrypted w/ 256 bit key w/ master key
  *  SSE-KMS: AWS Key Management Service; provides auto trail log
  *  SSE-C: Server side encryption with custom keys
  *  **Client-Side**
  *  Customer provided key encryption before upload

**Storage Gateway**

* Connects on premise storage to cloud-based storage
* Storage Gateway appliance available as VM
* Four Types
  * File Gateway (NFS): Ownership, permissions, timestamps saved; flat files stored directly on S3
  * Volumes Gateway (iSCSI): stored and cached volumes; can be stored as Amazon EBS(Elastic Block Store) Snapshots
  * iSCSI Stored Volumes: Asynchronous backup of physical storage; 1gb to 16tb; dataset on site backups on S3
  * iSCSI Cached Volumes: S3 main storage; requenctly accessed physical on site; 1gb to 32tb; backups on site main storage on S3
  * Tape Gateway (VTL): backup and archive solution; supported by VeeAM, Netbackup, Backup Exec

**Snowball**

* Replace Import/Export Disk where you would send your own disks
* Three types: Snowball, Snowball Edge, Snowmobile
* Snowball: helps transport data in/out of AWS with appliance not network; storage only, 80TB, simple, fast, secure
* Snowball Edge: 100tb of data and onboard storage & compute capacity; AWS hardware on premise with Lambda, compute capacity, etc...
* Snowmobile: semi-truck with petabyte/exabyte levels of data, 100pb per capacity, about 6 months to transfer

**S3 Transfer Acceleration**

* Uses Cloudfront Edge Network to upload files to S3 Buckets
* Disctint URL to upload to S3

**S3 Static Website**

* Make folder publicly accessible
* Make files publicly accessible with bucket policy
* Set properties to static website hosting
* *Great to use as it has dynamic load balancing etc...

**Notes**

* S3 is object based storage
* Files can be 0-5tb
* Unlimited storage
* Stored in buckets
* S3 is universal namespace (bucket names must be unique)
* Read after Write consistency of PUTS and DELETES
* Classes and Tiers
* Read <a href="https://aws.amazon.com/s3/faqs/">S3 FAQ Page</a>
* 200 code upon succesful upload
* Encryption types (SSE-S3 SSE-KMS SSE-C)
* By default all files are private

**S3 Summary Exam Study**

* URL: https://s3-region-name-amazonaws.com/bucketname
* Read after Write consistency of PUTS of new objects
* Eventual overwrites PUTS and DELETES (can take time)
* Storage Tiers/Classes
* S3 stores as key(name):value(data) with version ID and metadata
* Flat files only (no OS or DB)

## EC2_101<a name="ec2"></a>

**Summary**

* Elastic Compute Cloud
* Provides resizable compute capacity in cloud
* Four Pricing Models: On Demand, Reserved, Spot, Dedicated Hosts
* Spot instance if terminated by Amazon EC2 no charge, if you terminate must pay for complete hour instance ran
* FIGHT DR MC PX: remember all instance types
* All EBS Types: General Purpose SSD, Provisioned IOPS SSD, Throughput Optimized HDD, Cold HDD, Magnetic

**Pricing Option**

* On Demand: fixed rate by hour or second
	* low cost without up-front or long term commitment
	* For applications w/ short term/ spiky/ unpredictable workloads
	* Great for testing
* Reserved: contract for 1 or 3 years in length
	* Applications with steady state and predicatable usage
	* Applications with reserved capacity
	* Up front-payments up to 75% off on demand
	* Convertible RIs(reserved instances) up to 54% off on demand
	* Scheduled RIs for time frame you reserve
* Spot: bid for spot if you have flexible start and end
	* Flexible start and end times at very low prices
* Dedicated Hosts: physical EC2 server dedicated to your use -- allow you to use existing server-bound licenses
	* regulatory requirements that do not support multi-tenant virtualization
	* great for licensing
	* can be purchased on demand or reservation for up to 70% off on demand

**EC2 Instance Types**

* F1, I3, G3, H1, T2, D2, R4, M5, C5, P3, X1
* FIGHTDRMCPX

**EBS**

* Elastic Block Storage
* Storage volumes to attach to EC2 instances

**EBS Types**

* General Purpose SSD (GP2)
	* Ratio of 3 IOPs per GB up to 10000 IOPs and 3000 IOPS bursts
* Provisioned IOPS SSD (IO1)
	* Designed for I/O extensive for DBs
	* Use if need more than 10000 IOPS
	* Can provision up to 20000 IOPS/ volume
* Throughput Optimized HDD (ST1)
	* big data, data warehouses, log processing, can't be boot volume
* Magnetic
	* lowest cost per gig, ideal when data is accessed infrequently and low cost important

**EC2 Lab Notes**

* One subnet equals one availability zone
* Deleting EC2 instance __EBS volume deleted__ by __default__ unless unchecked
* ssh as ec2-user@10.10.10.10 -i Cert.pem
* Disable termination protection in actions to terminate instance
* __Default root volume can not be encypted__ without third party tool or AWS console/ API
* Additional volumes can always be encrypted
* Termination protection turned off by default
* EBS backed instance defaults to delete root EBS volume on termination

**Security Groups Lab**

* Any __change__ made to security group applied __immediately__
* Security groups are __stateful__ - will automatically be allowed outbound if allowed inbound
* Security groups __only allow__ don't deny so allowed multiple security groups
* All __inbound__ traffic __blocked by default__ / all outbound allowed
* __Infinite__ number of EC2 instances in Security Group
* Can't block specific IP addresses (must use Network ACLs)

**Upgrading EBS Volume Lab**

* Go to EC2/ Volumes
* Use snapshot to change availablity zone/ storage type etc...
* Create image from storage device to boot as new EC2 instance
* Standard can not modify the volume
* __Volumes__ exist on __EBS__ (Elastic Block Storage)
* Snapshots exist on S3
* Snapshot is point in time copy of volume
* Snapshot of root EBS volume for device should be taken with instance powered off (possible while running)
* Can create AMIs from volumes and snapshots
* Can change size and storage type of volumes on the fly
* Volumes same availability zone as the EC2 instance
* Snapshots of volumes encrypted automatically
* Volumes restored from encrypted snaps are encrypted by default
* Can share snapshots only if unencrypted

**Encrypt Root Device Volume Lab**

* Recommended to stop instance before taking snapshot of root device
* Able to encrypt snapshot after snapshot has been created
* Create AMI of encrypted volume to have encrypted root device

**AMI Types**

* Amazon Machine Image has two types: EBS backed / Instance Store backed
* AMI can be chose based on:
	* Region
	* Operating System
	* Architecture (32-bit vs 64-bit)
	* Launch Permissions
	* Storage for root device : Instance Store (Ephemeral Storage) or EMS backed
* Instance store instance can not be stopped, EBS can be stopped
* EBS based has more durability and faster provisioning times
* EBS Volumes: root device is Amazon EBS voume created by EBS snapshot
* Instance Store Volumes (Ephemeral Storage): root device volume created from template stored in S3
* Root volumes will be deleted on termination however with EBS can keep the root device volume if needed

**Load Balancer Theory**

* __Three types: Application, Network, Classic__
* __Application__ Load Balancer:
	* operate at layer 7
	* advanced and intelligent
	* intelligent and can reate advanced routing based on applications
* __Network__ Load Balancers:
	* load balances TCP traffic
	* Operate at layer 4
	* capable of handding millions of requests
* __Classic__ Load Balancers:
	* Elastic Load Balancer (old name)
	* Operate at Layer 7 and Layer 4
	* allowed X-forwared and sticky sessions
* Load balancing errors:
	* __504__: timed out error (application is having issues possibly scaling)
* X-Forwarded-For Header:
	* Header that stores public IP address
	* Forwards request from public IP to private IP address 124.12.3.231 -> 10.0.0.23
* __ELB Exam Tips__:
	* 3 types of load balancers
	* 504 error means gateway timed out
	* X-Forwarded-For header gives you IPv4 of end user

**Load Balancers and Health Check Lab**

* Instances monitored by ELB are reported as:
	* InService
	* OutofService
* Healthcheck checks instance by sending request
* Have DNS name, never given IP address
* Read ELB FAQ for Classis Load Balancers

**Cloud Watch EC2**

* Default EC2 Metrics
	* CPU
	* Disk
	* Network
	* StatusCheck
* CloudWatch Events
	* Create events linking all the systems based on parameters
* Cloud Watch Logs
	* Install widget to gather logs in central location
* __Cloud Watch Exam Tips__
	* Standard monitoring 5 mins
	* Detailed monitoring 1 min
	* Dashboards, alarms, events, logs
	* Cloud Watch vs Cloud Trail
		* Cloud Trail for auditing (monitor all of AWS like new user/ bucket/ etc...)
		* Cloud Watch for logging/ monitoring

**AWS Command Line Lab**

* Can run from EC2 instance or install tools locally
* ```aws configure``` set up AWS cli access
* credentials stored in home directory under .aws directory (not secure)

**Identity Access Management Roles Lab**

* Roles are created globally not by region
* Can attach and replace IAM roles of EC2 instances (new feature)
* Gives access to s3 or other permissions right away without secret access key
* Roles give better security

**S3 CLI & Regions**

* Can use command line to attach IAM Role or AWS webGUI

**Bash Scripting Lab**

* Bash scripts can be put into the EC2 configure instance and will run upon startup

    ```
        #!/bin/bash
        yum update -y
        yum install httpd -y
        service httpd start
        chkconfig httpd on #starts httpd on restart
     ```

**EC2 Instance Metadata**

* On EC2 instance: ```curl http://169.254.169.254/latest/metadata``` __remember url__
* Can use this to pipe and write to an S3 bucket which then starts a lambda function etc...

**Launch Configurations and Autoscaling Groups Lab**

* Must create __launch configuration before Auto Scaling Group__
* Most likely want all availability zones (subnets) for redundancy --spreads evenly by default

**EC2 Placement Groups**

* Two types of placement groups
    * Clustered Placement Group: Grouping of instances withing __single availability zone__, low network latency, high network throughput, or both
    * Spread Placement Groups: group of instances placed on distinct underlying hardware, recommended for applications that have small # of critical instances that should remain separate
* CPG can't span multiple Availability Zones, SPG can
* Placement Group name must be unique within AWS account
* Only certain instances can be launched in PG
* AWS recommends homogenous instances within PG
* Can't merge PGs
* Can't move existing instance into PG, can create an AMI for existing instance then launch new AMI

**EFS Lab**

* Elastic File System: file storage for EC2, storage capacity is elastic
* Features
    * Supports NFSv4
    * Only pay for storage in use (no provisioning)
    * Can scale to pentabytes
    * Supports thousands of concurrent NFS connections
    * Data stored across multiple AZs
    * Block based storage
    * Read After Write consistency
    * Can restrict at file and directory level

**Elastic File System Lab**

* Instances must be within same seurity groups as EFS

**Lambda Concepts**

* History: Data Center -> IAAS -> PAAS -> Containers -> Serverless
* Lambda released 2015
* What is Lambda: encapsulates Data Centers, Hardware, Assembly Code/ Protocols, High Level Languages, OSs, Application Layer/ AWS APIs
* AWS Lambda: compute service where you can upload code to create a Lambda function, don't have to worrry about OS, pathing, scaling, etc...
* Lambdas Two Uses:
    * Event-Driven Compute Service: AWS Lambda runs code in response to events like changes in S3, Dynamo DB, etc...
    * Compute Service to run code in response to HTTP requests using API Gateway or AWS SDKs
* Scales Up vs Scales Out
* Know Lambda API Gateway Event Trigger
* Python, Node.js, Java, C# original languages, now __any__ language
* Function must not take longer than 5 minutes to execute
* Lambda Pricing:
    * First 1 million requests free: $0.20 per 1 million thereafter
    * Duration: from execution to termination: rounds to nearest 100ms, charged $0.00001667 for every GB-second used

###### Lambda Summary: Exam Tips
* Lambda scales out not up automatically
* Lambda functions are independent; 1 event = 1 function
* Lambda is serverless
* Know what services are serverless! S3, DynamoDB, API Gateway, Lambda
* Lambda functions can trigger other lambda functions
* Architectures can get extremely complicated, AWS X-ray allows you to debug
* Lambda can do things globally
* Know your triggers
* Maximum Lambda execution duration 5 minutes

**What is Serverless?**

* Vendors take care of provisioning and management of servers
* Vendor responsible for capacity provisioning and automated scaling
* Moving away from servers and infastructure concerns is goal
* "No server is easier to manage than no server" - Werner Vogels

**EC2 SUMMARY EXAM TIPS**

* Know the differences between:
    * On Demand
    * Spot
    * Reserved
    * Dedicated Hosts
* Instance Types: FIGHT DR MC PX
* EBS Consists Of
    * SSD General Purpose - GP2 - Up to 10000 IOPS
    * SSD Provisioned IOPS - IO1 - More than 10000 IOPS
    * HDD Throughput Optimized - ST1 - frequently accessed workloads
    * HDD Cold - SC1 - less frequently accessed data
    * HDD Magnetic - Standard - can be bootable, cheap, infrequently accessed
    * Cannot mount 1 EBS volumes to multiple EC2 instances, use EFS
* EC2 Lab Exam Tips
    * Termination protection turned off by default
    * EBS volume deleted by default on termination
    * EBS-backed Root Volumes can be encrypted via AWS API or console
    * Volumes exist on EBS
    * Snapshots exist on S3
    * Can take snapshot of volume to store on S3
    * Snapshots are point in time copies of Volumes
    * Snapshots are incremental, only blocks that have changed are moved to S3
    * First snpashot may take some time
    * Snapshots of encrypted volumes encrypted automatically
    * Volumes restores from encrypted snapshots encrypted automatically
    * Can share unencrypted snapshots with other AWS accounts or public
    * To create snapshot for Amazon EBS recommended stop instance first
    * Instance store volumes cannot be stopped, if host fails data lost
    * EBS backed volumes can be stopped
    * Reboot of both instance store or EBS backed will not lose your data
    * With EBS Volume can keepthe root device volume upon termination
    * Snapshot on RAID:
      * Stop application from writing to disk
      * Flush all caches to the disk
      * Freeze file system
      * Unmount the RAID Array
      * Shut down associated EC2 instance
* Amazon Machine Images (AMI)
    * AMIs are regional
    * Can copy AMIs to other regions
* Monitoring
    * Standard monitoring = 5 minutes
    * Detailed monitoring = 1 minute
    * Cloudwatch for performance monitoring
    * CloudTrail for auditing
* Cloudwatch
  * Dashboards: Monitor AWS environment
  * Alarms: Set alarms to notify when thresholds hit
  * Events: Respond to state changes in AWS resources
  * Logs: Aggregate, monitor, and store logs
* Roles
  * Far more secure than storing access key and secret access key on EC2 instances
  * Roles can be asigned to EC2 instance after provisioning through CLI or console
  * Roles are universal - can be used in any region
* Instance Meta-data
  * Used to get information about instance
  * curl http://169.254.169.254/latest/meta-data/
  * curl http://169.254.169.254/latest/user-data/
* EFS Features
  * Supports NFSv4
  * Pay only for what is used
  * Scalable to pentabytes
  * Can support thousands of concurrent NFS connections
  * Data is stored actoss multiple Availability Zones
  * COnsistency is read after write
* Lambda
  * Takes care of provisioning and managing servers via code
  * Event-driven compute service running code in response to events; events could be changed to data in S3 or DynamoDB
  * Compute service to run code in response to HTTP requests using Amazon API Gateway or API calls using AWS SDKs
* Placement Groups:
  * Clustered Placement Group
  * Spread Placement Group


### Route 53<a name="route53"></a>

**Pre-Test Unknown Knowledge**

* Route 53 zone apex records (naked domain names)
* Geolocation vs Geo-proximity routing policy

**DNS 101**

* Start of Authority Record Contains:
  * name of server supplied data for zone
  * administrator of zone
  * current version of the data file
  * default number of seconds for time-to-live
* Name Server Records (NS Records)
* Naked Domain Name: nothing in front of the DNS name (example.com), www.* makes it invalid
* Types of Records
  * A Record: Address Record, translates name to IP address
  * CName: Canonical Name, resolve one DNS name to another, can't have a cname for naked domain, must be alias
  * Alias Record: Unique to Route 53, like cname, maps dns name to target (ELB, S3, etc...), can be used for naked domain name

*Exam Tips*
    * ELBs do not have pre-defined IPv4 address, resolve using DNS name
    * Understand difference between Cname and Alias Record
    * Given choice always use Alias Record over Cname
    * SOA Records: information in a DNS Zone
    * Alias Record: AWS created to help fix what Cname can not do, also maps Amazon DNS for S3 or EC2 IP changes
    * Common DNS Types: SOA Records, NS Records, A Records, CNames, MX Records, PTR Records

**Routing Policies on Route 53**

* Simple Routing
  * Default routing policy
  * Most commonly used when singe resource (one web server)
* Weighted Routing
  * Specify percentage of traffic hitting different servers
* Latency Routing
  * Route based on lowest network latency (fastes response time) for end user
  * Use EC2 or ELB resource record set
* Failover Routing
  * Active/Passive set up
  * Monitors the health of your primary site, fails over to secondary
* Geolocation Routing
  * Based on geographic location of user based on DNS query origination
* Multivalue Answers
  * Multiple IPs for same DNS name to help with load and health checks

**Route 53 Exam Tips**

    * Routing Policies Available
        * Simple Routing
        * Weighted Routing
        * Latency-based routing
        * Failover Routing
        * Geolocation Routing
        * Geoproximity Routing
        * Multivalue Answer Routing


### Databases on AWS<a name="database"></a>

**Pre-Test Unknown Knowledge**

* "Force" failover for RDS instance with multi-AZ
* RDS maximum backup retention period
* RDS database engines currently available
* Maximum size of RDS Provisioned IOPS - 16tb

**Databases 101**

* RDS - Relational Database: database, tables, rows, fields; must change table to add new field
  * AWS RDS: SQL Server, Oracle, MySQL, PostgreSQL, Amazon Aurora, MarioDB
* Non-Relational Database: no SQL, collection, document, key-value pairs
  * AWS DynamoDB
* Redshift OLAP: for business use to gather data
* Data Warehousing: Used for business intelligence, used for very large complex datasets (sales, performace targets)
  * Tools: Cognos, Jaspersoft, SQL Server Reporting Services, Oracle Hyperion, SAP NetWeaver
* OLTP vs OLAP Transactions
  * OLTP Online Transaction Processing: Pull up and order number and the date, address, delivery address, delivery status, etc...
  * OLAP Online Analytics Processing: Data warehousing databases
* Elasticache: Web service to easily deploy, operate, scale memory cache in cloud
  * Retrieve information a lot quicker with in memory
  * Supports Memcached and Redis

**Lab: RDS Instance**

* Security Group for RDS instance
  * Make sure inbound rules allow EC2 instance for correct port

**RDS BackU Ups, Multi-AZ, Read Replicas**

* Automated Backups
  * 2 types: Automated Backups, Database Snapshots
    * Automated
      * recover to any point in "retention period" 1- 35 days
      * daily snapshot and transaction logs throughout day
      * recovery most recent and apply transaction logs down to the second recovery
      * enabled by default and replicates size of RDS instance
      * during backup storage I/O may be suspended and may have elevated latency
      * 
* Snapshots
  * manually, stored even after RDS deletion

* Restoring Backups
  * Restoration creates new RDS instance with new RDS endpoint

* Encryption
  * Uses AWS Key Management Service (KMS)
  * Supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB, Aurora
  * Encrypts backups, read replicas, snapshots
  * Presently encrypting existing DB not supported; take snapshot, make copy, encrypt copy
* Multi-AZ
  * Have read copy in another AZ, if main DB fails rollover to synced read copy
  * If fails will make hostname (dns endpoint) redirect to active DB
  * For __disaster recovery only__
  * Available for SQL Server, Oracle, MySQL Server, PosgreSQL, MariaDB
* Read Replica
  * Allowed 5 read replicas per DB be default
  * Scaling Out
  * Allowed read replica of read replica (watch for latency)
  * Asynchronous replication of primary RDS, primarily for read-heavy workloads
  * Available for MySQL Server, PostgreSQL, MariaDB, Aurora
  * For __scaling__ not disaster recovery
  * Automatic backups must be on for read replica
  * Each read replica has unique DNS end point
  * Can have read replicas with Multi-AZ
  * Can create read replicas of Multi-AZ source DBs
  * Read replicas can be promoted to own DB
  * Can be in another region

**DynamoDB**

* Fast flexible NoSQL DB providing consistant millisecond latency at scale with key-value data models
* Stored on SSD, spread across 3 geographically distinct data centers
* __Eventual Consistent Reads__ (default): consistency normally one second
* __Strongly Consistent Reads__ results all writes succesful prior to read
* Pricing
  * Write Throughput $0.0065/ hour per 10 units
  * Read Throughput $0.0065/ hour per 50 units
  * Storage $0.25/ gb per month

**Redshift**

* Fast powerful, fully managed, petabyte-scale data warehouse
* Pricing
  * $0.25/ hour no commitment up to petabyte
  * Additional $1000 per terabyte a year
  * Compute Node Hours - 1 unit per node (not charged for leader node)
  * Backup
  * Data transfer within VPC
* Configuration
  * Single Node (up to 160Gb)
* Multi-Node
  * Leader Node (manages client connections and receives queries)
  * Compute Node (store data and perform queries) up to 128 compute nodes
* Columnar Data Storage (10 times faster)
  * Redshift organizes data by columns not rows
  * Queries are processed columnar, data stored sequentially, fewer I/Os, better performance, advanced compression scheme
* Massively Parallel Processing (10 times faster)
  * Automatically distributes data and query load across all nodes, easy to add nodes to data warehouse, maintain fast query
* Redshift Security
  * Encrypted in transit using SSL
  * Encrypted at rest using AES-256
  * Default handles key management - can use HMS or AWS KMS if preferred
* Currently available in only 1 AZ
* Can restore snapshots to new AZ in outage

**Elasticache**

* Web service to easily deploy, operate, and scale in-memory cache in the cloud
* Can significantly improve latency and throughput for many read-heavy applications or compute-instensive workloads
* Types of Elasticache
  * Memcached: Elasticache is protocol compliant with Memcached so should work seamlessly with application using Memcached
  * Redis: Popular open-source in-memory key-value that supports sets and lists, Elasticache supports master/slave replication and multi-AZ
* __Alleviates databases under a lot of stress/ load__
* Elasticache good for read heavy and not frequently changings DBs

**Aurora**

* MySQL compatible, relational, five times better performance than MySQL, 1/10th the price of commercial DBs
* Scaling: starts at 10GB, auto scales at 10GB increments to 64TB; compute can scale to 32vCPUs & 244GB memory
* 2 Copies of DB in each AZ, 3 minimum AZs, so 6 copies of data
* Can handleloss of two copies w/o affecting write availability and three copies w/o affecting read availability
* Self-healing: if data block or disk error, repaired automatically
* Aurora Replicas
  * Aurora Replicas (currently 15)
  * MySQL Read Replicas (currently 5)

**Database Summary: Quiz Review**
   
* Available DBs
  * RDS: primarily used for OLTP; SQL, MySQL, PostgreSQL, Oracle, Aurora, MariaDB
  * DynamoDB: no SQL
  * Redshift: OLAP
  * Elasticache: in memory cache; Memcached, Redis
* Multi-AZ: Synchronously replicates to allow failover
* Read Replica: Write to main read from multiple for speed
* Aurora: 6 copies of data, can handle data losses, self-healing
* DynamoDB: scale with no downtime, SSD storage, spread across 3 datacenters, different consistent reads
* Redshift: Single or Multi-node
* Elasticache: in-memory cache for speed, Memcached or Redis supported

### VPC Overview

**Overview**

* VPC (Virtual Private Cloud): virtual data center in the cloud
* Allows provisioning of logically isolated AWS Cloud to launch resources in a virtual network
* Usable IP ranges: 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16
* What VPC can do
  * Launch instances into subnet of choosing
  * Assign custom IP address ranges in each subnet
  * Configure routing tables between subnet
  * Create internet gateway and attach to VPC (only one per VPC)
  * Much better security control
  * Instance security groups
  * Subnet ACLs
* Default VPC vs Custom VPC
  * Default user friendly, created automatically
  * Default all subnets have route to internet
  * Both EC2 has public and private IP address
* VPC Peering
  * Allows one VPC to connect with another via private IP address
  * Behave as on same network
  * Can peer VPCs with other AWS account or VPCs in same AWS account
  * Always in star configuration (hub and spoke): much pair each VPC with one another for communication
* Exam Tips
  * Consists of IGWs (or VPGs), Route Tables, Network Access Control Lists, Subnets, Security Groups
  * 1 subnet = 1 Availability Zone
  * Security Groups are stateful (inbound & outbound), Network Access Control Lists are Stateless (inbound & outbound independent)
  * No transative peering

**Create a VPC Lab**

* Upon creating VPC by default also creates: Security Group, Network ACL, Routing Table --- Won't create: Subnet
* First 4 and Last 4 IP addresses of each subnet are reserved
  * 10.0.0.0: Network Address
  * 10.0.0.1: VPC Router
  * 10.0.0.2: VPC network range plus two
  * 10.0.0.3: Future Use
  * 10.0.0.255: Network Broadcast (no support for broadcast in VPC)
* Subnet by default belongs to main Route Table
* Create new Route Table to enable internet access
* Create route to 0.0.0.0/0 IPv4 ::/0 IPv6 for internet access
* Edit subnet to auto-assign public IP if Internet Access available to it
* Security groups don't span VPCs

**Network Address Translation**

* NAT Instance (fading out for NAT Gateway)
  * Must disable Source/Destination Checks to allow it to send and recieve traffic
  * Routing Table route all 0.0.0.0/0 to the NAT Instance
  * NAT Instance not the best at scaling or reliability
* NAT Gateway
  * Operates only on IPv4
  * Create in each AZ to ensure zone-independent architecture
* Egress Gateways
  * Operates only on IPv6
* NAT Instances vs NAT Gateways https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html
* NAT Instance Exam Tips
  * NAT Instance creation: disable source/destination check
  * NAT Instance must be in public subnet
  * Must be route out of private subnet to NAT instance
  * NAT instance traffic depends on instance size
  * Create high availability using Auto-Scaling Groups, different AZs, script for failover
  * Behind security group
* NAT Gateway Exam Tips
  * Preferred by Enterprise
  * Scale automatically to 10Gbps
  * No patching
  * Not assocaited with security groups
  * Automatically assigned public IP
  * Remember to update route tables and point to NAT Gateway
  * Have multiple AZs
  * More secure than NAT instance


**Access Control Lists**

* One ACL per subnet
* By default private ACL set to deny all
* Rule 100 for IPv4 Rule 101 for IPv6 - increment by 100
* Ephemeral Ports: must have some outbound open for connections - https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html#nacl-ephemeral-ports
* NACL Exam Tips
  * vpc comes default with network ACL, allows all outbound and inbound
  * Created VPC by default blocks all inbound and outbound
  * Each subnet must be associated with NACL
  * NACL can be associated to multiple subnets
  * Subnet can only be associated to one NACL
  * NACLs evaluate rules starting from least to greatest
  * NACLs are stateless: block and allow inbound & outbound separately
  * Can block IP Addresses using NACLs; not Security Groups

**Custom VPCs and ELBs**

* ELB must have at minimum two subnets specified

**VPC Flow Logs**

* Enables capturing of IP traffic to and from VPC, stored in CloudWatch logs
* Can be created at 3 levels
  * VPC
  * Subnet Network Interface Level
* VPC Flow Logs Exam Tips
  * Cannot enable flow logs for peered VPCs not in your account
  * Cannot tag a flow log
  * Cannot change configuration once created (Ex: can't associate different IAM role)
  * Not all traffic is monitored, below is negated
    * Amazon DNS server traffic
    * Windows instance Amazon Windows license activation
    * Traffic to/ from 169.254.169.254
    * DHCP traffic
    * Traffic to reserved IP address for dedicated VPC
* NAT vs Bastion
* Bastion host: "jumpbox", allows ssh connection through private network to private instance
* Two public subnets each with a Bastion with auto-scaling for high availability

**VPC End Points**

* Allows access to S3 or other services without going through public network
* Steps
  * create IAM role with access
  * Create endpoint
* Elastic Network Interface (ENI): serves as entry point for destined traffic

**AWS VCP - Summary**

* NAT Instances
  * When creating NAT instance Disable Source/Destination Check on Instance
  * Must be in public subnet
  * Must be route out of private to NAT instance
  * Amount of traffic depends on instance size
  * Behind a Security Group
* NAT Gateways
  * Preferred by enterprise
  * Scale automatically 10Gbps
  * No need to patch
  * Not associated with security groups
  * Automatically assigned public ip address
  * Remember update route tables
* Network ACLs
  * VPC automatically comes with default NACL, allows all outbound/ inbound
  * Custom NACLs by default denies all outbound/ inbound
  * Each subnet in VPC must be associated to NACL
  * NACL can have multiple subnets, subnet only one NACL
  * NACLs evaluate lowest to greatest rule number
  * Stateless: inbound & outbound rules can differ
  * Can block IP addresses
* Application Load Balancers
  * Must have 2 subnets
* VPC Flow Logs
  * Cannot enable flow logs for peered VPCs not in your account
  * Cannot tag a flow log
  * Cannot change configuration after flow log
  * Not all IP traffic monitored: Amazon DNS Server, Amazon Windows license activation, to and from 169.254.169.254, DHCP, VCP Reserved IP
* VPC Endpoints
  * Communicate to AWS Service without hitting internet only internal network


### Application Services

** SQS

* What is SQS - Simple Queue Service
  * Message Queue service,
  * distributed queue system
  * Queue: temporary repository for messages awaiting processing
  * __Pull based__ system, EC2 instance is pulling the job to process
  * Decouples the components of an application to run independently
  * Messages may contain 256 KB of text in any format
  * Any component can later retrieve the messages using Amazon SQS API
* Types of Queues
  * Standard Queue
    * default type
    * nearly unlimited number of transations/ second
    * guarantees delivered once
    * occasionaly more than one copy may be delivered out of order
    * best-effort ordering, not in order
  * FIFO Queues (First-In-First-Out)
    * deliver and process exactly once (no duplicates)
    * order is strictly preserved
    * limited to 300 transaction/ second
  * SQS Key Facts
    * SQS is pull-based not pushed-based
    * 256 kb in size
    * Can be kept from 1 minute to 14 days
    * default retention 4 days
    * SQS guarantees processed at least once
  * SQS Visibility Timeout
    * Becomes invisible when reader picks up message
    * If processed before visibility timeout then deletes otherwise goes back in queue
    * Default Visibility Timeout 30 seconds
    * Maximum timeout is 12 hours
  * SQS Long Pulling
    * Way to retrieve messages from queue
    * Short pulling returns immediately even if message queue is empty
    * Long Pulling doesn't return response until message arrives
    * Long Pulling can save money
  * SQS Exam Tips
    * Distributed Message Queueing system
    * Allows decoupling of components in application
    * Pull based, not push based
    * Standard an FIFO Queues

**SWF**

 * SWF Simple Workflow Service
   * Easily coordinate work across distributed application components
   * Tasks represent invocations of various processing steps performed by code, web service calls, scripts, human interaction
 * SWF Workers
   * Workers are programs that get tasks, process recieved tasks, and return results
 * SWF Decider
   * Program that controls the coordination of tasks, ordering, concurrency, scheduling according to application logic
 * SWF Workers & Deciders
   * Ensures tasks are assigned only once and are never duplicated
   * Maintains task state
 * SWF Domains
   * Workflow activity and execution are scoped to a domain
   * Register domain via AWS Management Console or Amazon SWF API RegisterDomain
   * Maximum Workflow can be one year (measured in seconds)
 * SWF vs SQS
   * SWF presents task-oriented API
   * SQS offers message-oriented API
   * SWF ensures no duplication
   * SQS need to handle duplicated messages and ensure only processed once

**SNS**

* SNS - Simple Notification Service
  * Easy to set up, operate, and send notifications
  * Follows publish-subscribe paradigm delivering with a push mechanism
  * Pay-as-you-go pricing
  * Simple APIs
  * __Pushes__ to Apple, Google, Windows devices, and Android devices in China with Baidu Cloud Push
  * ALso delivers to SMS, Amazon SQS, HTTP endpoints
  * To prevent from being lost all are stored reduntantly across multiple AZs
* SNS Topics
  * Group multiple receipients together to allow dynamically subscribable notifications
* SNS Benefits
  * Instantaneous push based delivery (no pulling)
  * AWS Console gives point and click
* SNS Pricing
  * $0.50 per 1 million Amazon SNS Requests
  * $0.06 per 100000 Notification deleveries via HTTP
  * $0.75 per 100 notification deliveries over SMS
  * $2.00 per 100000 notification deliveries via email

**Elastic Transcoder**

* Elastic Transcoder
  * Media Transcoder in the cloud
  * Pay based on minutes and resolution

**API Gateway**

* API Gateway
  * Fully managed service for developers to publish, maintain, monitor, and secure APIs at scale
  * Can create API that allows application to access data from back-end services
  * Log requests to CloudWatch
* API Caching
  * Cache API endpoint response
* CORS (Cross-Origin Resource Sharing)
  * Allows restricted resources to be requested from another domain (such as fonts)

**Kinesis 101**

* Application to send streaming data to in order to analyze and use
* Kineses Services
  * Kinesis Streams
    * 24hours to 7 days retention
    * Stores data in shard
    * Shards allow 5 transaction/second, max total read rate of 2 MB/ second, 1000 writes/ second, max data write rate of 1MB/ second
    * 
  * Kinesis Firehouse
  * Kinesis Analytics


### Whitepapers & The Well Architected Framework

**What Else Do I Need to Know**

* Read Architecting for the Cloud Whitepaper --- on AWS Study Guide
* Look over the AWS Well-Architected web page & Whitepapers

**Architecting for the Cloud Best Practices Whitepaper**

* Business Benefits
  * Upfront investnment, just-in-time infastructure, usage-based costing, time to market
* Techincal Benefits
  * Automation "Scriptable Infastructure", Autoscaling, effecient development lifecycle, improved testability, disaster recovery, overflow traffic
* Elasticity
  * Scaling Up vs Scaling Out
* Design For Failure
  * Assume things will fail and build for disaster -- use Chaos Monkey and Chaos Snail Tools
* Decouple Your Components
  * Use SQS, have asynchronous components
* Implement Elasticity
  * Proactice Cyclic Scaling: scaling that occurs at fixed intervals (daily, weekly, monthly, quarterly)
  * Proactive Ecent Scaling: scaling when big surge expected due to event
  * Auto-scaling Based on Demand: scaling based on metrics
* Secure Applications
  * check open ports, VPCs, etc...

**Intro to Well Architected Framework**

* 5 Pillars of Well-Architected Framework
  * Security
  * Reliability
  * Performance Effeciency
  * Cost Optimization
  * Operation Excellence
* General Design Principles
  * Stop guessing capacity needs, scale automatically
  * Test at production scale, use CloudFormation for example
  * Automate to make expirementation easier
  * Allow for evolutionary architectures
  * Data-Driven Architecture;use Cloudwatch to make choices
  * Use Game Days to simulate events in production

**Security Pillar**

* Design Principles
  * Apply security at all layers, Subnets, ACLs, Ports, Instances, etc...
  * Enable traceability
  * Automate security event responses
  * Automate best security practices
* AWS Shared Responsobility Model
  * Customer responsible for Platform, Applications, Access Management, Platform, OS, Network & Firewall, Encryption
  * AWS responsible for Physical Infastructure, Regions, Availability Zones, Racks, Compute, Storage, DBs, Networking
* Definition
  * Security
    * Data Protection: classify data to publicly available, only organization accessible, limited to groups in organization, encrypt when possible
      * AWS customers remain full control of data, use Key Management Service for encrytpion, S3 for durability, etc...
      * Versioning can protect again accidental harm
      * AWS never initiates movement of data between regions
      * Encrypt data-at-rest and data-in-transit
    * Privelege Management
      * ACLs, Role Based ACLS, Password Management
      * Protect acces of AWS root account
      * Roles and responsobilities for AWS Consoleand AWS
      * Limit access of applications, scripts, third-party tools and services
      * Manage keys and credentials
    * Infastructure Protection
      * Protect the VPC with security groups, ACLs, NACLs, etc...
      * Enforce networkand host-level boundary protection
      * Enforce AWS service level protection
      * Protect the integrity of the OSs on EC2 instances
    * Detective Controls
      * CloudTrail - monitor users/ changes to AWS environment
      * CloudWatch - monitor resource usage
      * Capture andanalyze AWS logs (CloudTrail is per region)
    * Key AWS Services
      * Security encrypt data in transit and at-rest: ELB, EBS, S3, RDS
      * Privelege Management: IAM, MFA
      * Infastructure Protection: VPCs, NACLs, Bastion Hosts, Public/ Private Subnets
      * Detective Controls: CloudTrail, CloudWatch

**Reliability Pillar**

* Design Principles
  * Test recovery procedures using tools such as Symian Army (Netflix)
  * Automatically recover from failure
  * Scale horizontally (multiple small resources rather than one large - scaling up)
  * Stop guessing capacity
* Definition
  * Foundations
    * most foundations are handled by AWS, however do not set practical service limits
    * Manage AWS service limits
    * Plan network topology
    * Escalation path for technical issues
  * Change Management
    * Monitor changes with tools such as CloudWatch and autoscaling
    * Execute change management
  * Failure Management
    * Always assume failures will occur
    * Back up data
    * Plan for recovery
  * AWS Services
    * Foundations:: IAM, VPC
    * Change Management: CloudTrail
  * Failure Management
    * CloudFormation, RDS Multiple AZ, test with tools yourself

**Performance Efficiency**

* Design Principles
  * Create services to allow easily usage of technologies
  * Go global in minutes with a few clicks, CloudFormation etc...
  * User server-less architectures
  * Experiment more often
* Definiton
  * Compute
    * Choose the right kind of EC2 instance or no servers at all with Lambda
    * Ensure you always have best instance type
    * Monitor instances post launch
    * Ensure quantity matches demand
  * Storage
    * Factors: access method (block, file, object), Pattern of Access, Throughput required, Frequency of Access, Frequency of Update, Availability and Durability
    * Select best storage solution
  * Databases: No-SQL, RDS
    * No-SQL vs SQL
  * AWS Services
    * Compute: Autoscaling
    * Storage: EBS, S3, Glacier
    * Database: RDS, DynamoDB, Redshift
    * Space-Time Trade-Off: Cloudfront, Elasticache, Direct Connect, RDS Read Replicas, etc...


**Cost Optimization**

* Design Principles
  * Transparently attribute expenditure: separate costs based on department
  * Use managed services
  * Trade capital expense for operating expense
  * Avoid data center costs
* Definition
  * Matched supply and demand
    * Optimally align supply with demand, autoscaling/ serverless
    * Match capacity, do not exceed
    * Optimize AWS resources
    * Correct instance type for processes
    * Use biling alerts and tags
    * Decommission resources that are no longer needed, such as test environments
    * Research new services for better performance and spending
    * Services such as Trusted Advisor
* Key AWS Services
  * Matched Supply & Demand: Autoscaling
  * Cost-effective resources: EC2, AWS Trusted Advisor
  * Expenditure Awareness: Cloudwatch Alarms, SNS
  * Optimizing over Time: AWS Blog, AWS Trusted Advisor

**Operational Excellence**

* Design Principles
  * Perform operations with code
  * Align operations to business objectives
  * Regular, small, incrememntal changes
  * Test for unexpected events
* Definition
  * Preparation
    * Workloads should have: Runbooks - guidance for daily tasks, Playbooks - guides to unexpected events
    * Configuration management
  * Operations
    * Standardized and routine with small changes preferred
    * Set up CI/CD
    * Routine operations should be automated
    * Set alarms and SNS notifications for events
* AWS Services
  * Prepapration: AWS Config, AWS Service Catalog, Auto Scaling, SQS
  * Operations: CodeCommit, CodeDeploy, CodePipeline, CodeStar, AWS SDKs, CloudTrail
  * Responses: CloudWatch, SNS
  * Etc: Cloudformation, Tagging


## Exam Tips Based on Student Feedback

**Review Material**
* Amazon Kinesis
  * Used to consumebig data
  * Process large amount of data
    * Redshift for business intelligence
    * Elastic Map Reduce for Big Data Processing

* EC2 EBS Backedvs Instance Store
  * EBS backed volumes are persistent - lives on it's own outside of EC2 instance
  * Instance Store backed volumes are ephemeral (terminate with EC2)
  * EBS can be detached and reattached to other EC2 instances
  * EBS Volumes can be stopped and data will persist
  * Instance Store volumes can not be stopped, if EC2 instance is stopped all data is lost
  * EBS Backed = Store Data Long Term

* OpsWorks
  * Orchestration Service that uses Chef
  * Terms dealing with "chef" "recipes" "cook books"

* Elastic Transcoder**
  * Media transcoder in the cloud
  * Provides transcoding presets for popular output formats
  * Pay based on minutes transcoded and resolution

* SWF Actors
  * Workflow Starters: Application that kickstarts a workflow (e-commerce placing an order, searching for bus times, etc...)
  * Deciders: Control flow of activity tasks, if finished or failed what is next execution
  * Activity Workers: Carry out the activity t

* Get Public IP
  * curl or wget http://169.254.169.254/latest/meta-data/

**Organizations & Consolidated Billing**

* AWS Organization
  * Consolidate multiple AWS accounts into an organization to create and centrally manage
  * Two Feature Sets
    * Consolidated Billing
    * All Features
  * Allows Policies to different OUs
* Consolidated Billing
  * Break down billing by accounts
  * Limit 20 accounts bydefault
  * Allows all environments (test, dev, production) to use one billable account for payment structure of services
  * Saves money
  * Paying account should be used for billing only
  * CloudTrail is per AWS account and enabled per region
  * Can consolidate logs using S3 bucket
    * Turn on CloudTrail in paying account
    * Create bucket policy to allow account access
    * Turn on CloudTrail in other accounts and use bucket in paying account
* Consolidated Billing Exam Tips:
  * Allows volume discounts on all accounts
  * Unused reserved EC2 instances applied per group
  * Cloudtrail is per account and per region basis but can be aggregated to single bucket in paying account
  * Service Control Policy (SCP) on group overrides IAM policy

**Cross Account Access**

* Allows multi-account or multi-role access withing AWS Management Console
* Steps
  * Identify our account numbers
  * Create group in IAM-Dev
  * Create user in IAM-Dev
  * Log in to Production
  * Create policy
  * Create Cross Account Role
  * Apply newly created plicy to Developer Account
  * Create new inline policy
  * Apply it to Developer group
  * Login as John
  * Switch Accounts

**Tagging & Resource Groups**

* Tags: Key-Value pairs attached to AWS resources, metadata, can sometimes be inherited
* Resource Groups: Groups of resources sharing one or more tags
  * Types of Resource Groups
    * Classic Resource Groups: global basis for resource groups
    * AWS Systems Manager: resources on per region basis, allow automation
  * Tags are case sensitive
  * Tag everything for easy access and searchability

**VPC Peering**

* Connection between two VPCs routing traffic using private IPs
* VPCs can pair with same AWS account or another AWS account within __Single Region__
* Not a gateway or VPN conection, no single point of failure or bandwith bottleneck
* Wont work with overlapping CIDR block (IP ranges)
* Must be directly peered for communication

**Direct Connect**

* Establish dedicated network connection from on premise to AWS
* Reduce cost when using large volumes of traffic, increase bandwith
* VPN Connection vs Direct Connect
  * VPN quick configuration, DC need planning
  * VPN great for low to moderate bandwith, DC allows high bandwith
  * VPN internet-based connectivity and may disconnect frequently, DC not using internet instead private network
  * Direct Connect is private line between AWS Direct Connect Facility to your network
* Direct Connect Connections
  * 10Gbps or 1Gbps available
  * Sub 1Gbps available through AWS Direct Connect Partners
  * Uses Ethernet VLAN trunking (802.1Q)

**Security Token Service (STS)**

* Grants users limited and temporary AWS resources
* Three resources allowed:
  * Federation (typically Active Directory)
    * Uses SAML, no IAM required
  * Federation Mobile Apps
    * Uses Facebook, Amazon, Google, or other OpenIDs providers log ins
  * Cross Account Access
    * Allows one AWS account access to resources in another
  * Terms
    * Federation: combining orjoining users in one domain to another
    * Identity Broker: take identity from A to point B
    * Identity Store: Services like AD, Facebook, Google, etc...
    * Identities: End users
* Active Directory and STS: AD authenticates first, browser receives SAML assertion, AWS uses SAML to sign into AWS Console

**Workspaces**

* VDI Cloud-based replacement for traditional desktop
* Works from many supported devices and with AD credentials
* Windows 7 experience provided by Windows Server 2008 R2
* Workspaces are persistent
* D:\ backed up every 12 hours

**Elastic Container Service (ECS) - What is Docker**

* Docker allows you to build, test, and deploy applications quickly
* Virtualization vs Containerization
  * Virtualization uses all of the virtual components
  * Containerization only includes application and dependencies
* ECS uses EC2 as a container management service

**Elastic Container Service (ECS) - What is ECS**

* Regional service that schedules the placement of containers across clusters
* ECS eliminates need to operate cluster management configuration
* Manage ETL (Extract Transform Load) workloads, build application architectures on microservice model
* Registry (ECR): Registry for docker files much like DockerHub
* ECS Clusters: Logical grouping of container instances, region specific
* ECS Sheduling: Checks specified number of tasks are running and healthy
* ECS Container Agent: Allows container images to connect to cluster
* ECS Security: 
  * IAM Roles
    * EC2 uses IAM role to access ECS 
    * EC2 tasks use IAM role to access microservices and resources
  * Security groups attach at the instance-level
  * Can access and configure OS of EC2 instances in ECS cluster
* ECS Limits
  * Soft Limits
    * 1000 clusters per region
    * 1000 instances per cluster
    * 500 services per cluster
  * Hard Limits
    * One load balancer per service
    * 1000 tasks per service
    * Max 10 containers per task definition
    * Max 10 tasks per instance