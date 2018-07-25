# Custom Docker Images

## Introduction

A source of difficulty when developing applications is creating the perfect environment on one's machine to run said application. However, by using Docker, you can set up the perfect environment to run your application. Dockerfiles define the environment within a container, a runtime instance of an image. An image is an executable package that cointains an application's code, runtime, libraries, environment variables, and configuration files. A Dockerfile can use an image, such as Ubuntu, and define the environment on top of the image. Thus, we can run an app in, for example, an Ubuntu container with all the necessary dependencies installed, as defined in our Dockerfile. These instructions follow the creation of a Dockerfile for testing a calculator app, available [here], and are based off of [this](https://docs.docker.com/get-started/part2/#introduction) Docker documentation.

## Prerequisites

* Docker: Install your preferred version of Docker [here](https://docs.docker.com/install/) and use the [official Docker getting started guide](https://docs.docker.com/get-started/) to familiarize yourself with Docker.
* Docker account: Set up a Docker account [here](https://cloud.docker.com/).

## Create a Custom Docker Image

### Create Empty Directory

Create an empty directory and navigate into that directory within your command line.

``` shell
cd [EMPTY_DIRECTORY]
```

### Create `Dockerfile`

Within that directory, create a file called `Dockerfile`. This is where you will define the environment of your container.

### Open `Dockerfile`

Open `Dockerfile` in an editor of your choice.

### Fill `Dockerfile`

Fill the Dockerfile while following the format below. A very short example Dockerfile is beneath the format. The [FROM instruction](https://docs.docker.com/engine/reference/builder/#from) initializes a new build stage and sets the base image. The [RUN instruction](https://docs.docker.com/engine/reference/builder/#run) runs a command within our docker container. For more reference on instructions and information on Docker syntax, click [here](https://docs.docker.com/engine/reference/builder/#usage).

#### Format

``` Dockerfile
# Comment
INSTRUCTION arguments
```

#### Example

``` Dockerfile
#Use an official Ubuntu runtime as a parent image
FROM ubuntu

#Say hello
RUN echo "Hello world!"
```

### Build Image

Now that you have a Dockerfile with instructions, it's time to build your image. Run the below command, inserting your own tag for the image. **Note the period after the image tag**.

``` shell
docker build -t [LOCAL_IMAGE_TAG] .
```

### Confirm Image Existence

Once your image is done building, you can confirm that it is in your machine’s local Docker image registry with the below command.

``` shell
docker image ls
```

### Log in to Docker

To share your image, log in to docker with the below command.

``` shell
docker login
```

### Tag Image

Before uploading your image, you should give it a tag for Docker Hub using the following command. An example of a repository name and tag could be `dockertesting:latest`. If no tag is given, Docker will tag the image with `latest` by default.

``` shell
docker tag [LOCAL_IMAGE_TAG] [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]
```

### Publish Image

Publish the image with below command.

``` shell
docker push [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]
```

Now your image is accessible from online and can be pulled at any time. The next set of instructions explain how you can use your Docker image in CircleCI.

## CircleCI and Custom Docker Images

CircleCI supports the use of custom Docker images, and the CircleCI documentation on customizing Docker images for CircleCI can be found [here](https://circleci.com/docs/2.0/custom-images/).

### Add Docker Image to Job

If you have built and pushed a custom Docker image, you can use it in your CircleCI job by adding the image path to the Docker executor in your job.

```YAML
job:
  build:
    docker:
      - image: [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]
```

The information in brackets can be found by visiting your image on [Docker Hub](https://hub.docker.com/) and selecting your repository. The Docker pull command will be on the repository page, and you can find your tag under the Tags tab.

### CircleCI Image as Base Image

You can also build your custom Docker image on top of a CirlceCI image. Say you want to use the `circleci/android:api-25-alpha` image, but you need to add more dependencies. You can create a Dockerfile and begin it with the following.

```Dockerfile
FROM circleci/android:api-25-alpha
```

Now you can add your instructions to set up an environment within a CircleCI container. The next section breaks down an exmaple Docker image used with CircleCI to build and upload an app to MoQuality.

## CircleCI and Custom Docker Image for MoQuality App

MoQuality has created a [Github repository](https://github.com/moquality/plugins) with all the necessary files to build and upload a calculator app to MoQuality by using CircleCI and a custom Dockerfile. Our Dockerfile uses Ubuntu as our parent image and installs dependencies such as Gradle to build the app. The Docker image path is `jragonemq/mqubuntutest:latest`. Before beginning, create an app on MoQuality that you can use to test the upload properties of this build. It does not matter what apk file you upload upon creation of the app.

### MoQuality's Example `Dockerfile`

The following is the code behind the `jragonemq/mqubuntutest:latest` Dockerfile. This creates an environment for running the calculator app on top of an Ubuntu parent image. We are essentially filling a fresh Ubuntu container with our dependencies. The comments explain what each set of instructions is doing. However, understanding each instruction is less important than understanding what these instructions accomplish holistically: they build the environment.

``` Dockerfile
#Use an official Ubuntu runtime as a parent image
FROM ubuntu

#Set user to root
USER root

#Update apt-get and install dependencies
RUN apt-get -y update && apt-get install -y wget bzip2 unzip gcc nodejs npm openjdk-8-jdk git sudo curl

#Install Gradle
RUN wget https://services.gradle.org/distributions/gradle-4.1-bin.zip
RUN mkdir /opt/gradle
RUN unzip -d /opt/gradle gradle-4.1-bin.zip
#Define environment variable
ENV PATH=$PATH:/opt/gradle/gradle-4.1/bin
RUN gradle -v

#Install Android tools for sdkmanager
RUN mkdir /android-sdk
RUN wget https://dl.google.com/android/repository/sdk-tools-darwin-3859397.zip
RUN unzip -d /android-sdk sdk-tools*.zip
ENV ANDROID_HOME=/android-sdk
ENV PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/tools/bin:$ANDROID_HOME/tools/platform-tools:$ANDROID_HOME/build-tools/26.0.2

#Accept all licenses and install dependencies
RUN yes | sdkmanager --licenses
RUN sdkmanager "platforms;android-22"
RUN sdkmanager "build-tools;26.0.2"

#Copy Android
COPY android-8.0.0 android
ENV PATH="/android:$PATH"
```

### Create Empty Directory for Git Repo

Create an empty directory and `cd` into it.

``` shell
cd [EMPTY_DIRECTORY]
```

### Clone MoQuality Repository

Clone MoQuality's example repository using `git clone`.

``` shell
git clone https://github.com/moquality/plugins.git
```

### `config.yml` Contents

Within the hidden `.circleci` folder is the `config.yml` file. In this file are steps which build the app using `gradle build`, [install the mq-cli](circleci.md#instructions), and [login and upload the app to MoQuality](circleci.md#instructions).

``` YAML hl_lines="24 26"
version: 2
jobs:
  build:
    docker:
      - image: jragonemq/mqubuntutest:latest
    environment:
      JVM_OPTS: -Xmx3200m
    steps:
      - checkout
      - run:
          name: Build app
          command: gradle build
      - run:
          name: Install mq-cli
          command: |
            curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
            sudo apt-get install -y nodejs
            sudo chown -R $(whoami) /usr/lib/node_modules /usr/bin
            npm -g config set user root
            npm install -g mq-cli
      - run:
          name: Login and Upload to MoQuality
          command: |
            mq login -a [API_KEY]
            mq user
            mq upload -f app/build/outputs/apk/debug/app-debug.apk -a [APP_ID]
            mq apps
```

### Edit `config.yml`

By the `mq login` and `mq upload` commands, highlighted above, fill in [API_KEY] and [APP_ID] with the API key of your account and app Id of your app, respectively. To find your API key, run `mq login` in your command line and follow the prompts to log in to your account. Next, run `mq user` to display user information. Your API key will be in the list of returned information. To find your app Id, log in with `mq login` and run `mq apps` to see a list of your apps. Find your app in the list and locate the app Id in the same row.

Using the above instructions and [CircleCI MQ CLI integration documentation](circleci.md), we have created our own custom Dockerfile, integrated it with CircleCI, and integrated the CircleCI with MoQuality.