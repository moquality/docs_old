# Custom Docker Images

## Introduction

A source of difficulty when developing applications is creating the perfect environment on one's machine to run said application. However, by using Docker, you can set up the perfect environment to run your application. Dockerfiles define the environment within a container, a runtime instance of an image. An image is an executable package that cointains an application's code, runtime, libraries, environment variables, and configuration files. A dockerfile can use an image, such as ubuntu, and define the environment on top of the image. Thus, we can run an app in, for example, an ubuntu container with all the necessary dependencies installed, as defined in our dockerfile. These instructions follow the creation of a dockerfile for testing a calculator app, available here, and are based off of [this](https://docs.docker.com/get-started/part2/#introduction) docker documentation.

## Prerequisites

* Docker: Install your preferred version of Docker [here](https://docs.docker.com/install/).
* Docker account: Set up a Docker account [here](https://cloud.docker.com/).

## Instructions

### Create a Custom Docker Image

1. **Create an empty directory** and navigate into that directory within your command line.

        $ cd [EMPTY_DIRECTORY]

2. Within that directory, **create a file called `Dockerfile`**. This is where you will define the environment of your container.

3. Open `Dockerfile` in an editor of your choice.

4. Fill the dockerfile while following the format below. A very short example dockerfile is beneath the format. For reference on the usage of docker syntax, click [here](https://docs.docker.com/engine/reference/builder/#usage).

**Format**

``` Dockerfile
# Comment
INSTRUCTION arguments
```

**Example**

``` Dockerfile
#Use an official ubuntu runtime as a parent image
FROM ubuntu

#Say hello
RUN echo "Hello world!"
```

5. Now that you have a dockerfile with instructions, it's time to build your image. Run the below command, inserting your own tag for the image. Note the period after the image tag.

        $ docker build -t [LOCAL_IMAGE_TAG] .

6. Once your image is done building, you can confirm that it is in your machine’s local Docker image registry with the below command.

        $ docker image ls

7. To share your image, log in to docker with the below command.

        $ docker login

8. Before uploading your image, give it a tag for Docker Hub using the following command. An example of a repository name and tag could be `dockertesting:latest`.

        $ docker tag [LOCAL_IMAGE_TAG] [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]

9. Publish the image with below command.

        $ docker push [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]

Now your image is accessible from online and can be pulled at any time. The next set of instructions explain how you can use your docker image in CircleCI.

### CircleCI and Custom Docker Images

### Custom Docker Image for Example MoQuality App

1. Paste the following into your dockerfile. This dockerfile creates an environment for running the Calculator app on top of our ubuntu container. Note that the RUN instruction is akin to running a command within the command line. We are essentially filling a fresh ubuntu container with our dependencies and running a shell script when the container launches. Read the comments to understand what the instructions are doing.

``` Dockerfile
#Use an official ubuntu runtime as a parent image
FROM ubuntu

#Update apt-get and install dependencies
RUN apt-get -y update && apt-get install -y wget bzip2 unzip gcc nodejs npm openjdk-8-jdk git

#Install CircleCI
RUN wget -o /circleci https://circle-downloads.s3.amazonaws.com/releases/build_agent_wrapper/circleci && chmod +x /circleci

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

#Install MQ CLI and copy android
RUN npm install -g mq-cli
COPY android-8.0.0 android
ENV PATH="/android:$PATH"

#Copy shell script into container
COPY mqtest.sh mqtest.sh

#Run mqtest.sh when container launches
CMD ["sh", "mqtest.sh"]
```