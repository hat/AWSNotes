# Labs
https://s3-us-west-2.amazonaws.com/aws-well-architected-labs/Operations/100+-+Estate+&+Patch+management+Lab+guide.html
https://github.com/awslabs/aws-well-architected-labs/tree/master/Security
https://github.com/awslabs/aws-well-architected-labs/blob/master/Reliability/300%20-%20Testing%20for%20Resiliency%20of%20EC2%2C%20RDS%2C%20and%20S3/Lab%20Guide.md


# AWS Well-Architected Framework

* Pillars
* Design Principles
* Questions

## Why Well-Architected

* Build and deploy faster
* Lower and mitigate risks
* Make informed decisions
* Learn AWS Best Practices

## Pillars of AWS Well-Architected

* Operational Excellence
* Security
* Reliability
* Performance Efficiency
* Cost Optimization

## General Design Principles

* Elasticity: handle multiple capacity loads by expanding and shrinking automatically based on load
* Test Production Scale: AWS allows automation to spin up tests
* Automate: Should not be pointing and clicking in console to do things
* Evolutionary Achitectures: Allow for growth, needs, etc...
* Metrics: Measure to see if decisions worked; must be doing what it needs to do not just IP, CPU, etc...
* Game Days: As a group get together and find holes, optimizations, etc...

** ~275 services called for AWS Home Page
** ~27 services needed healthy to load Home Page w/o anything

## Benefits of AWS Well-Architected

* AWS Well-Architected Tool: Provides customers and partners w/ approach to review workloads
  * https://aws.amazon.com/well-architected: White-Paper, Free Online Training




### END OF INTRODUCTION



# Jon Steel, Technical Spacialist Account, Operation Excellence White Paper Author

# Operational Excellence

* Infastructure and Operations as code


# Lab 1 Notes

Tony-Admin
AWSWorkshop3!
https://tonyhendrick.signin.aws.amazon.com/console

###Systems Manager
   
* Allows connection to on-premise and cloud instances: works on EC2 and Amazon Linux by default
* Patch Manager: Test in test not in production... there is no way to validate for all OSs; reboot on patch manager


## Pavin Daysigh - Network Solutions Architect

### Lab 2 Notes - Application Security on AWS - https://github.com/awslabs/aws-well-architected-labs/tree/master/Security

* Credentials Report
  * Download CSV file from IAM to see users and permissions





-- Rodney Lester

# Lab 3 Notes
# Testing Resiliency and EC2, RDS, S3 --- Reliability Pillar

* Test recovery procedures
* Should scale horizontally rather than vertically
* Stop guessing capacity --- Ex: AOL built mobile communicator, 100 of millions of users, ended with 60,000, built for millions, overspent
* Manage change using automation

** Amazon failure tools

* Chaos Monkey: injects failures on instances/ containers
* Chaos Gorilla (deprecated): simulates an AZ failure
* Chaos Kong: simulates AWS Region failure

* Test your resiliency in a single AZ first and perfect it, very little companies actually need multiple AZ infastructure

* Automate recovery to save time and failure impact
* Solve multiple problems with one solution

* Can use AWS Sytems Manager and EC2 Run Command to inject falure without ssh keys
* Can write your own AZ Failure Simulation


*  Best practice to put only load balancer in IGW Routed Subnet

* Failover is easy, failback is more difficult
* Practice the fail scenarios


-- Shankar Ramachandran -- Solutions Architect

# Cost Optimization

* Replace cost with usage
* Customers must actively invest --- it's a long journey
* Well-Architected Cost Approach
  * Governance
  * Pricing Models
  * Billing Analysis
  * Cost Visualization
* Migrate out of Cloudwatch Billing Alert and switch to Budgets
* Put controls in place to avoid excess usage
* Cost does vary by region
* Using Athena and QuickSite and SQL queries on large data sets saves time/ compute power
* Amazon Quicksight when Cost Explorere is not showing enough info