# Deploying a Flask API

This is the Server Deployment, Containerization, and Testing project for [Udacity Full Stack Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004) course: .

In this project I have containerized and deployed a Flask API to a Kubernetes cluster using Docker, AWS EKS, CodePipeline, and CodeBuild.

The Flask app used for this project consists of a simple API with three endpoints:

- `GET '/'`: This is a simple health check, which returns the response 'Healthy'. 
- `POST '/auth'`: This takes a email and password as json arguments and returns a JWT based on a custom secret.
- `GET '/contents'`: This requires a valid JWT, and returns the un-encrpyted contents of that token. 

The app relies on a secret set as the environment variable `JWT_SECRET` to produce a JWT. The built-in Flask server is adequate for local development, but not for production, so the production-ready [Gunicorn](https://gunicorn.org/) server is used for deploying the app.

## Dependencies

- Docker Engine
    - Installation instructions for all OSes can be found [here](https://docs.docker.com/install/).
    - For Mac users, if you have no previous Docker Toolbox installation, you can install Docker Desktop for Mac. If you already have a Docker Toolbox installation, please read [this](https://docs.docker.com/docker-for-mac/docker-toolbox/) before installing.
 - AWS Account
     - An AWS account can be created by signing up [here](https://aws.amazon.com/#).
     
## Project Steps

Completing the project involved several steps:

1. Writing a Dockerfile for a simple Flask API
2. Building and testing the container locally
3. Creating an EKS cluster
4. Storing a secret using AWS Parameter Store
5. Creating a CodePipeline pipeline triggered by GitHub checkins
6. Creating a CodeBuild stage which will build, test, and deploy the project code
