# Week 3 — Decentralized Authentication

## Watched
Amazon Cognito Security Best Practices - https://www.youtube.com/watch?v=tEJIeII66pY&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=40. 
AWS Cloud Bootcamp (Week 3) - https://www.youtube.com/watch?v=9obl7rVgzJw&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=40. 
Week 3 Cognito Custom Pages - https://www.youtube.com/watch?v=T4X4yIzejTc&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=41. 
Week 3 Cognito JWT Server Side Verify - https://www.youtube.com/watch?v=d079jccoG-M&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=42. 
Week 3 - Exploring JWTs - https://www.youtube.com/watch?v=nJjbI4BbasU&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=43. 
Week 3 - Improving UI Contrast and Implement CSS Variables for Theming - https://www.youtube.com/watch?v=m9V4SmJWoJU&. list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=44

## Steps
 - Provision via ClickOps a Amazon Cognito User Pool
 - Install and configure Amplify client-side library for Amazon Cognito
 - Implement API calls to Amazon Coginto for custom login, signup, recovery and forgot password page
    1. Needed significant troubleshooting to get token errors cleared
 - Show conditional elements and data based on logged in or logged out
 - Verify JWT Token server side to serve authenticated API endpoints in Flask Application
 - Utilized logger a lot to trouble shoot Cognito JSON web token server side setup 


#### Homework
?


#### Notes
1. Different kinds of authentication - OAuth, OpenID Connect, Username/Passwd, SAML/SS & Identity Provider, Traditional physical badge
    1. Oauth - open-standard auth protocol that gives 3rd party apps secure designated access
        1. Ex: Tell Facebook its ok that Instagram accesses your profile
    2. OpenID - allows you to use an existing account to sign in to multiple websites, without needing to create new passwords. 
    3. SAML - security assertion markup language - xml based open standard for transferring identity data between two parties: an IdP and a service provider. 
        1. IdP performs auth and passes users’ identity/auth to service provider
        2. Trusts the IdP and authorizes the given users access
2. Decentralized Auth - Only want to use and store one username and password to log onto multiple sites
3. AWS Cognito - provides authentication, authorization, and user management  for your web and mobile apps. 
    1. User Pool - user directories that provide sign-up/in options for app users
    2. Identity Pool - allows an app for to access other AWS resources through temp credentials
4. User Lifecycle Management - strategic and tactical approach to onboard a user, implement a process that enables users to perform tasks through multiple devices and services on the network, and finally off board the user.
5. Token lifecycle management - handling the different states of the token from creation to expiry

###### Best Practices - User
Identity pool - least privilege rule for the roles. 
AWS Cognito - should only be in the AWS region that you are legally allowed to hold user data in. 
Utilize AWS Organizations/Groups. 
AWS CloudTrail is enabled & monitored to trigger alerts on malicious Cognition behavior by an identity in AWS. 

###### Best Practices - App
Should use industry standard for Authentication and Authorization (SAML, OpenID Connect, OAuth2.0, etc). 
Role based access using principle of least privilege. 
Token lifecycle management and where to keep tokens (client or server). 
Encryption in transit for API calls. 
