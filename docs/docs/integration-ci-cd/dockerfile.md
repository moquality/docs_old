# Custom Docker Images

## Introduction

A source of difficulty when developing applications is creating the perfect environment on one's machine to run said application. However, by using Docker, you can set up the perfect environment to run your application. Dockerfiles define the environment within a container, a runtime instance of an image. An image is an executable package that cointains an application's code, runtime, libraries, environment variables, and configuration files. A Dockerfile can use an image, such as Ubuntu, and define the environment on top of the image. Thus, we can run an app in, for example, an Ubuntu container with all the necessary dependencies installed, as defined in our Dockerfile. These instructions follow the creation of a Dockerfile for testing a calculator app, available [here], and are based off of [this](https://docs.docker.com/get-started/part2/#introduction) Docker documentation.

## Prerequisites

* Docker: Install your preferred version of Docker [here](https://docs.docker.com/install/) and use the [official Docker getting started guide](https://docs.docker.com/get-started/) to familiarize yourself with Docker.
* Docker account: Set up a Docker account [here](https://cloud.docker.com/).

## Instructions

### Create a Custom Docker Image

1. **Create an empty directory** and navigate into that directory within your command line.

        $ cd [EMPTY_DIRECTORY]

2. Within that directory, **create a file called `Dockerfile`**. This is where you will define the environment of your container.

3. Open `Dockerfile` in an editor of your choice.

4. Fill the Dockerfile while following the format below. A very short example Dockerfile is beneath the format. The [FROM instruction](https://docs.docker.com/engine/reference/builder/#from) initializes a new build stage and sets the base image. The [RUN instruction](https://docs.docker.com/engine/reference/builder/#run) runs a command within our docker container. For more reference on instructions and information on Docker syntax, click [here](https://docs.docker.com/engine/reference/builder/#usage).

**Format**

``` Dockerfile
# Comment
INSTRUCTION arguments
```

**Example**

``` Dockerfile
#Use an official Ubuntu runtime as a parent image
FROM ubuntu

#Say hello
RUN echo "Hello world!"
```

5. Now that you have a Dockerfile with instructions, it's time to **build your image**. Run the below command, inserting your own tag for the image. **Note the period** after the image tag.

        $ docker build -t [LOCAL_IMAGE_TAG] .

6. Once your image is done building, you can confirm that it is in your machine’s local Docker image registry with the below command.

        $ docker image ls

7. To share your image, log in to docker with the below command.

        $ docker login

8. Before uploading your image, you should give it a tag for Docker Hub using the following command. An example of a repository name and tag could be `dockertesting:latest`. If no tag is given, Docker will tag the image with `latest` by default.

        $ docker tag [LOCAL_IMAGE_TAG] [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]

9. Publish the image with below command.

        $ docker push [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]

Now your image is accessible from online and can be pulled at any time. The next set of instructions explain how you can use your Docker image in CircleCI.

### CircleCI and Custom Docker Images

CircleCI supports the use of custom Docker images, and the CircleCI documentation on customizing Docker images for CircleCI can be found [here](https://circleci.com/docs/2.0/custom-images/). If you have built and pushed a custom Docker image, you can use it in your CircleCI job by adding the image to the Docker executor of your job.

```YAML
docker:
  - image: [DOCKER_USERNAME]/[REPOSITORY_NAME]:[TAG]
```

The information in brackets can be found by visiting your image on [Docker Hub](https://hub.docker.com/) and selecting your repository. The Docker pull command will be on the repository page, and you can find your tag under the Tags tab.

You can also build your custom Docker image on top of a CirlceCI image. Say you want to use the `circleci/android:api-25-alpha` image, but you need to add more dependencies. You can create a Dockerfile and begin it with the following.

```Dockerfile
FROM circleci/android:api-25-alpha
```

Now you can add your instructions to set up an environment within a CircleCI container. The next section breaks down an exmaple Docker image used to build and upload an app to MoQuality.

### Custom Docker Image for Example MoQuality App

MoQuality has created a [Github repository] with all the necessary files to build and upload an example app to MoQuality by using CircleCI and a custom Dockerfile. Our Dockerfile uses Ubuntu as our parent image and installs dependencies like Gradle to build the app and MQ CLI to upload it to MoQuality. We also make use of a shell script called mqtest.sh that is filled with the necessary Gradle and MQ CLI commands. 

1. Paste the following into your Dockerfile. This Dockerfile creates an environment for running the Calculator app on top of our Ubuntu parent image. Note that the RUN instruction is akin to running a command within the command line. We are essentially filling a fresh Ubuntu container with our dependencies and running a shell script when the container launches. Read the comments to understand what the instructions are doing.

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