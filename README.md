# Dockerizing 2048 Game with Nginx

This Dockerfile allows you to containerize the popular 2048 game using Nginx as the web server. Follow the instructions below to create a Docker image and deploy it to Amazon Elastic Beanstalk.

## Prerequisites

Make sure you have the following installed on your system:

- Docker: [Get Docker](https://docs.docker.com/get-docker/)
- AWS CLI: [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- Elastic Beanstalk CLI: [Install EB CLI](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html)

## Build Docker Image

1. Clone the repository containing the Dockerfile:

    ```bash
    git clone https://github.com/fernandomarins/2048-game
    ```

2. Navigate to the directory containing the Dockerfile:

    ```bash
    cd your/repo
    ```

3. Build the Docker image:

    ```bash
    docker build -t 2048-game .
    ```

## Test Locally

1. Run the Docker container locally:

    ```bash
    docker run -p 80:80 2048-game
    ```

2. Open your web browser and navigate to [http://localhost:80](http://localhost:80) to play the 2048 game.

## Deploy to Amazon Elastic Beanstalk

1. Log in to your AWS account using the AWS CLI:

    ```bash
    aws configure
    ```

2. Initialize Elastic Beanstalk in your project directory:

    ```bash
    eb init -p docker
    ```

3. Create an environment and deploy the application:

    ```bash
    eb create 2048-environment
    ```

4. Access your deployed application:

    ```bash
    eb open
    ```
    
5. Finish your deployed application:

    ```bash
    eb terminate 2048-environment
    ```

## Cleanup

After testing, don't forget to stop and remove the local Docker container:

```bash
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
