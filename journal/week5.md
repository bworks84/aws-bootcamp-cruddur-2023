# Week 5 — DynamoDB and Serverless Caching

# Videos watched for Week 5
 - Watched Week 5 - Data Modelling (Live Stream). 
 - Watched Ashish's Week 5 - DynamoDB Considerations. 
 - Implement Schema Load Script. 
 - Implement Seed Script. 
 - Implement Scan Script. 
 - Implement Pattern Scripts for Read and List Conversations. 
 - Implement Conversations with DynamoDB. 
 - Implement DynamoDB Stream. 

 # DynamoDB - General: 
    - Amazon DynamoDB is a fully-managed, Serverless, key-value NoSQL database designed to run high-performance apps at any scale. DynamoDB offers built-in security, continuous backups, automated multi-region replication,   in-memory caching, and data import and export tools
	    - supports two primary keys: the partition key and the composite primary key. 
	    - partition key is a single attribute, composite primary key is a combo of 2 attributes named hash key and sort key. 

    1. Primary Key - when you create a table in DynamoDB, in addition to the table name, you must specify the primary key of the table. The primary key uniquely identifies each item in the table, so that no two items can have the same key. 
	    - Partition key - a simple primary key
	    - Composite primary key - partition + sort key 
    2.Partition key - entry point for querying the database and making the query more efficient than traditional SQL db. If used by itself, a partition key is the singular key that will be used to query the data in the db. 
	    - must be unique across the table (cannot have two items with the same partition key in the table)
	    - partition keys are immutable and partition key values of an item are also immutable
	    - naming of partition key is important for being the starting point for queries of the db.  (pk or id is common naming convention)
    3. Sort key - used to sort and order items in a partition. Known as a range attribute of an item, it helps to organize related info in a single location where it can be efficiently queried. 
    4. Composite primary key - partition key and sort key 
    5. GSI - are indexes that contain partition or composite partition and sort keys that can be different from the keys in the table on which the index is based. Considered global because queries on the index can span all items in a table, across all partitions

 # DynamoDB Security Considerations - Ashish
 - Learned about DynamoDB: creating tables, adding tags, indexes
 - Security best practices: 
    - Charged based on WCU and RCU. 
    - Use VPC endpoints: use AWS VPC to create private network from your app or lambda to a DynamoDB instance. This helps prevent unauthorized access to the instance from the public internet. 
    - AWS Organizations SCP - manage DynamoDB Table deletion, creating, region lock. 
    - CloudTrail is enabled and monitoring to trigger alerts on malicious DynamoDB behavior by an identity in AWS. 
    - AWS Config rules enabled in the account and region of DynamoDB. 

### Steps
1. Implemented Bash Scripts Schema Load, Seed, and Scan for DynamoDB
    - 