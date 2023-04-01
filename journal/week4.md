# Week 4 — Postgres and RDS

## Videos Watched
- AWS Cloud Project Week 4
- Week 4 SQL RDS
- Week 4 Cognito Post Confirmation Lambda
- Week 4 Creating Activities

## Steps for PostgreSQL
- Provision an RDS instance using PostgreSQL. 
- export & gp env PROD_CONNECTION_URL
- Also needed to modify the inbound ruels of the RDS instance VPC security groups, created a bash script that also runs from gitpod.yml (used Gitpod IP - curl ifconfig.me) because Gitpod IP address can change. 
- Created bash scripts to easily create, drop, seed, and connect to database

## Implement PostgreSQL Client
- added psycopg binary and pool to backend-flask/requirements.txt (run pip3 install -r requirements.txt)
- Programmatically update a security group rule. 
- Updated docker-compose.yml file with connection url
- replaced mock endpoint with real api endpoint in backend-flas/services/home_activities.py

## AWS Lambda for Cognito Post Confirmation
- In the AWS RDS prod table, when a new users is signed up, the user should be inserted into the table. Here we implemented an AWS Lambda that runs in the default VPC and commits the code to RDS. 
- This required setting up proper permissions for the lambda code, AWSLambdaExecutionRole in IAM
- THen changed the backend to CONNECTION_URL: "${PROD_CONNECTION_URL}" in docker-compose.yml
- Checking Cloudwatch helped debug SQL errors

## Creating Activities
- After creating the RDS instance, we needed to work with some json data from Postgres and debug some parameter issues. 
- Created create.sql, home.sql, and object.sql 
- finally able to successfully post messages on home page!
  

### Still needs work:
- Still getting a parameter error (handle and message are inputted in the wrong spots). 
- 3.20 - Fixed bugs!  Updated Activity Form component on pages/HomeFeedPage.js in frontend to pass the user_handle prop, updated the fetch request body to include the user_handle in components/ActivityForm.js, and assigned the user_handle variable following the other variables format in app.py api/activities route. All working now and posts are displaying correctly when signed in as user!!!  
- These changes ensured the the user_handle prop is passed correctly and included in the fetch request.  The server can now retrieve it from the request payload!
