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

# Data Modeling Video
Single Table Design is a data modelling technique in which all related data is stored in a single database table. We do it with DynamoDB for the Direct Messaging System in our Cruddur application. Here, data access can be break down into four patterns:

   1. Pattern A for showing messages. Users can see a list of messages that belong to a message group.
   2. Pattern B for showing message groups. Users can see a list of message groups so they can check the other persons they have been talking to.
   3. Pattern C for creating a new message in a new message group.
   4. Pattern D for creating a new message in an existing message group.


 # DynamoDB Security Considerations - Ashish
 - Learned about DynamoDB: creating tables, adding tags, indexes
 - Security best practices: 
    - Charged based on WCU and RCU. 
    - Use VPC endpoints: use AWS VPC to create private network from your app or lambda to a DynamoDB instance. This helps prevent unauthorized access to the instance from the public internet. 
    - AWS Organizations SCP - manage DynamoDB Table deletion, creating, region lock. 
    - CloudTrail is enabled and monitoring to trigger alerts on malicious DynamoDB behavior by an identity in AWS. 
    - AWS Config rules enabled in the account and region of DynamoDB. 

## Steps
### PostgreSQL
1. Implemented Bash Scripts for DBs
    - Created 3 folders for storing utility commands for PostgreSQL db (backend-flask/bin/db), DynamoDB (backend-flask/bin/ddb), AWS RDS (backend-flask/bin/rds) and AWS Cognito (backend-flask/bin/cognito)
    - These commands help automate the creation, updating, dropping, and seeding of db data
2. Added boto3 into backend-flask/requirements.txt, which is an AWS SDK module for Python that helps with creating, configuring, and managing AWS services like DynamoDB. 
3. Added pip3 install -r requirements.txt in gitpod.yml to load upon startup
4. PostgreSQL required seeding with default users ('Brown', and 'Bayko'), but I later went back and added my confirmed user from Cognito, which has a uuid.   
   - From there bash scripts like list-users and update-cognito-user-ids helped verify that the local db was updating with the correct data to avoid potential errors. 
   - We also set the CONNECTION_URL in docker-compose.yml
   - ./bin/db/connect help to verify and update data manually like loading another MOCK user, Londo Centari, for new message creation later

### DynamoDB
1. The following bash scripts helped to quickly create a DynamoDb table, drop, and load data. As well as look at seed data conversations/attributes
   - schema-load - created a table (needed to use this script very often for debugging and reloading)
   - drop - required table name, necessary for relaoding data
   - seed - loaded large conversation data with user attributes. (It was necessary to change my_handle from andrewbrown to 'rob', matching my cognito data. This overlook during the video caused me several days delay)
   - scan - scanned items in teh table cruddur-messages
   - patterns/get-conversations: list messages associated with seed data and gave useful dynamodb info like read/write capacity
   - patterns/list-conversations: list messages groups nad print the consumed capacity. (My name began showing up in this conversation instead of default seed users after many days of troubleshooting and utilizing discord channel)

### Implement Conversations with DynamoDB Local
1. Updated/created routes and functions in the backend to get messages and message groups from DynamoDb instead of heard-coded data. Changed passing handle to message_group_uuid;
2. Updated authentication in frontend (and learned that signing in and out helped with 500 error...alot)
3. Implemented creating new message for DynamoDB

### Conclusion
1. New users appear in app, can join group message and type a new message which is posted and saved to group chat. 
2. Users can also start there own chat which posts and saves. 
3. Learned a lot about authentication error de-bugging, databases and the need to created, seed, and verify db database several times throughout each session. 
