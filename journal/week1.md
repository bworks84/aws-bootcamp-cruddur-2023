# Week 1 — App Containerization

Steps

- This week I created a new GitHub repo, well forked actually from the main AWS Bootcamp repo
- Launched the repo in Gitpod where I used VSCode in the browser
- Cloned the frontend and backend of the project this week to work on building containers for each
- I installed Docker and learned how to build, run, & remove a docker container
- Created Dockerfiles for each application (frontend & backend) and ensured both were running locally
- Created a docker-compose file to be able to build and run multiple containers at once
- Ensured CORS were set up properly...after a bit of troubleshooting. 

## Week 1 Create the Notification 

Steps

- Built out both the frontend and backend api endpoint
- Learned to use openAPI GUI
- Tested locally with new notification
- Fixed bug in backend so that frontend rendered correct notifications page and feed


## Homework Challenges
- Ran the backend-flask Dockerfile as a script using : docker build -t "backend-devtest:Dockerfile" . 
    - That created an image named backend-devtest using the Dockerfile previously built out and placed it in the current directory