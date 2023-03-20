# Week 4 — Postgres and RDS

## Videos Watched
- AWS Cloud Project Week 4
- Week 4 SQL RDS
- Week 4 Cognito Post Confirmation Lambda
- Week 4 Creating Activities

## Steps
- Provision an RDS instance. 
- Temporarily stop an RDS instance. 
- Remotely connect to RDS instance. 
- Programmatically update a security group rule. 
- Write several bash scripts for database operations. 
- Operate common SQL commands. 
- Create a schema SQL file by hand. 
- Work with UUIDs and PSQL extensions. 
- Implement a postgres client for python using a connection pool. 
- Troubleshoot common SQL errors. 
- Implement a Lambda that runs in a VPC and commits code to RDS. 
- Work with PSQL json functions to directly return json from the database. 
- Correctly sanitize parameters passed to SQL to execute. 

### Still needs work:
- Still getting a parameter error (handle and message are inputted in the wrong spots). 
- ![Screenshot](/workspace/aws-bootcamp-cruddur-2023/journal/img/Screen Shot 2023-03-18 at 10.40.55 AM.png)
- 3.20 - Fixed bugs!  Updated Activity Form component on pages/HomeFeedPage.js in frontend to pass the user_handle prop, updated the fetch request body to include the user_handle in components/ActivityForm.js, and assigned the user_handle variable following the other variables format in app.py api/activities route. All working now and posts are displaying correctly when signed in as user!!!  
    - These changes ensured the the user_handle prop is passed correctly and included in the fetch request.  The server can now retrieve it from the request payload!
