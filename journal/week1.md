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

## Database setup

Steps

- Installed and test dynamodb via AWS ClI, added to docker-compose.yml file
- Installed and tested postgresql. Required adding light server to init in gitpod.yml file and verifying via command psql -Upostgres -h localhost


## Homework Challenges
- Ran the backend-flask Dockerfile as a script using : docker build -t "backend-devtest:Dockerfile" . 
    - That created an image named backend-devtest using the Dockerfile previously built out and placed it in the current directory
- Successfully tagged and pushed docker image to DockerHub (public repo : bworks/aws_bootcamp)
    - docker tag <image id> <hub-user>/<repo-name>:tagname
    - docker commit <container id> <hub-user>/<repo-name>:tagname
    - docker push <hub-user>/<repo-name>:tagname
- Added healthchecks to docker compose file for both frontend & backend. Verified backend is working, frontend is not because I didn't run npm install before docker compose up command. 
- Installed Docker on local machine, logged in, clone github repo to local vscode, ran npm install for frontend, updated pip, and was able to get all containers running on local machine via docker compose and were displayed in Docker GUI. 
- Launched a t2.micro instance on AWS, configured basic SG to allow SSH, used EC2-Connect to ssh into the EC2 instance, install yum, installed docker, pulled a 'Hello World' docker image, and executed docker run 'hello-world' image successfully!