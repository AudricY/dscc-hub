# Docker Quick Tutorial

## What is Docker

Docker is a useful tool that allows you to package your app/ program and run it with a single command. Docker has two components, Docker images and Docker containers. Containers acts as a self contained app while images are the templates the container uses to run, whether it be your python script or programs/ databases found online

## How do I use Docker

### Install Docker Hub

Go to https://hub.docker.com/ and create an account, this account would be used frequently later on so keep in mind what username and password you use. Make sure to download Docker Desktop as well to run your containers.

### Making your images

Docker images can be made locally or taken online, you can even upload them online to docker hub which is where you would find images as well. To start making images, you need to make a dockerfile, to create it, just name the file dockerfile. Don’t forget to add the docker extension if you are using visual studio code.

```
FROM openjdk:11-jdk
ENV APP_HOME=/app
RUN pip install --no-cache-dir -r requirements.txt
WORKDIR ./app
COPY . .
EXPOSE 8080
CMD ["python", "app.py"]
```

Looking at our example, let's go through what each component does.

- FROM: allows you to choose a new build stage from a base image, usually you can go with a lightweight image like alpine, do specify the version and not latest as updates to the image may lead to incompatibility in the app.
- ENV: dictates the environment, it's not necessary for setting up the python environment as you would be installing a requirements.txt later on
- RUN: runs commands needed before running the actual script
  WORKDIR is the directory containing all the necessary files for your image
- COPY: helps you select what files you need form WORKDIR
  EXPOSE: for exposing port, usually not necessary
- CMD: main command to run your image

With the dockerfile setup, now we can make the image. To make it simpler, in your terminal, change the directory to the directory where your dockerfile is located.

1. Run the command to build the image

   ```
   docker build -t my-username/my-image:v1.0 .
   ```

   The “-t” is to tag the image, include the username you have for your docker hub, you can even set the versions of your images but that is not necessary. The “.” at the end is the directory of the dockerfile so you can change it if not in said directory.

2. (Optional) Push image to docker hub with the following command
   ```
   docker image push my-username/my-image:v1.0
   ```
   This pushes the image to dockerhub to allow you to grab the image even if it is not on the local machine, useful if you want to reuse the same image for different apps

### Containerisation

Building and running containers, especially with multiple images can be done with a dockercompose.yaml file. Here is an example of one

```
version: "3.1"
services:
  flaskapp:
      build: .
      ports:
        - "3000:3000"
      depends_on:
        - app-database
      restart: always

  app-database:
    image: postgres:latest
    ports:
      - "5432:5432"
    environment:
      POSTGRES_DB: app-database
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```

There are a lot of moving parts to a dockercompose file, and the format for making each image changes, as such only some parts would be covered.

- “version” is the version of dockercompose used
- “services” houses the images that would be used
- “restart: always ” would restart the image when it fails
- “depends_on” indicates which image the target image is reliant on

If you’d noticed, “app-database” has parameter called “image:postgres:latest”, this is because “app-database” is the name of the image used within the dockercompose file while “image:” pulls the actual image either from online or locally.

### Running the Dockercompose File

Now that the dockercompose file is built, we can run the app in a container with a single command:

```
docker compose up -d
```

This command downloads and runs the images specified in the dockercompose file. “-d” runs it as detached such that your terminal would not be filled with debug logs.

To terminate the container, run the following command:

```
docker compose down -v
```

This command terminates the container. “-v” clears the volumes used by specified images in the dockercompose file
