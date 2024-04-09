# Docker_Instructions

## Install Docker Desktop Application

- [Windows & Mac Instructions](https://docs.docker.com/docker-hub/quickstart/)
- [Linux Instructions](https://docs.docker.com/engine/install/ubuntu/)
- [Additional Setup for wsl/ubuntu on windows](a. https://docs.docker.com/desktop/wsl/)

## Backend

1. In the root of the backend folder create a file and give it the name Dockerfile
2. In the terminal run the command which node to get the version of node you are using
3. Specify the version on the first line (FROM node:18) :18 is the version
4. Look at the Dockerfile_backend file to see how my dockerfile is set up
5. If you are doing migrations on your database you might need to set up a script to ensure that the migrations are run and that it happens at the right time.
6. The script will be in the root of the backend folder and be titled entrypoint.sh. Look at the example file to see how it should be set up
7. Make sure that the script has permission to run by running this command in your terminal:
   ```sh
   chmod +x entrypoint.sh
   ```
8. Create a file titled .dockerignore in the root of your backend foler
9. in .dockerignore type node_modules

## Frontend

1. Create a file in the root of your frontend folder titles Dockerfile
2. Look at the dockerfile frontend example to see what it should contain
3. Make a file in the root of yuor frontend folder and name it .dockerignore
4. in the dockerignore file write node_modules

## Putting it all together

1. in the root of your project (at the same level that the frontend and backend folders are) create a new file and name it docker-compose.yml
2. Look in the docker-compose.yml file to get an idea of what it should contain
3. Take a look at the two objects titled environment, these are referencing the variables you have in your .env
   - Docker automatically refers to .env so you only need to list the name
   - in the very root of your app (same level as docker-compose.yml) make a new .env file
   - Make sure every variable refrenced in the docker-compose is in the .env file
4. Take a look at the db object
   - DATABASE_HOST needs to be the same as the title of this object
   - Before docker, my DATABASE_HOST was localhost, now its db
   - change the DATABASSE_HOST in the backend .env just to be safe.

## Running the application

- Docker MUST BE running before you run your app, so make sure you have the desktop app open
- run your app with
  ```sh
  docker-compose up --build
  ```
- you can access the frontend at localhost (rather than http://localhost:3000/ )
- You can access the backend at http://localhost:8000/
