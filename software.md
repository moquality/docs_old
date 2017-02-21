# Software

## python

We use Anaconda. Currently we will try to use as many packages from conda as possible. Get Anaconda for pyton 2.7 from [here](https://www.continuum.io/downloads).

## gcloud

To setup gcloud:
- Download [google-cloud-sdk](https://cloud.google.com/sdk/).
- You might have to export the env variable, ```export CLOUDSDK_ROOT_DIR={path_to_sdk}```. Then run the install script.
- See the list of gcloud components: ```gcloud components list```
- Install the components you will work with. Ex: ```gcloud components install docker-credential-gcr```

Create credentials:
- Go to the [Credentials page](https://console.cloud.google.com/apis/credentials?project=moquality-inc)
- Create a service account key. The file should be stored in JSON.
- Check all the services you need this key to work with.
- Store it in ~/.ssh and point env variable ```GOOGLE_APPLICATION_CREDENTIALS``` to it.
