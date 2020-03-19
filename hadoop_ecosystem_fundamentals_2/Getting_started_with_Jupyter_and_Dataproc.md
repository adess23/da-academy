# Set up Jupyter Notebook on Dataproc

## Installing the Cloud SDK Docker image

For more information, click [here](https://cloud.google.com/sdk/docs/downloads-docker).

1. To use the image of the latest Cloud SDK release

```bash
~$ docker pull gcr.io/google.com/cloudsdktool/cloud-sdk:latest
latest: Pulling from google.com/cloudsdktool/cloud-sdk

50e431f79093: Pull complete
6005b060ba7d: Pull complete
c49059196e30: Pull complete
Digest: sha256:fd9985597827057effdb04fd1b07db9463f4a00ac24684cd3726c05e146eafa1
Status: Downloaded newer image for gcr.io/google.com/cloudsdktool/cloud-sdk:latest
gcr.io/google.com/cloudsdktool/cloud-sdk:latest
```

2. Verify the installation (if you've pulled the latest version) by running:

```bash
~$ docker run gcr.io/google.com/cloudsdktool/cloud-sdk:latest gcloud version

Google Cloud SDK 284.0.0
alpha 2020.03.06
app-engine-go
app-engine-java 1.9.78
app-engine-python 1.9.88
app-engine-python-extras 1.9.88
beta 2020.03.06
bigtable
bq 2.0.54
cbt
cloud-datastore-emulator 2.1.0
core 2020.03.06
datalab 20190610
gsutil 4.48
kubectl 2020.03.06
pubsub-emulator 0.1.0
```

3. Authenticate with the gcloud command-line tool by running:

```bash
docker run -ti --name gcloud-config gcr.io/google.com/cloudsdktool/cloud-sdk gcloud auth login
Go to the following link in your browser:

    https://accounts.google.com/o/oauth2/auth?...


Enter verification code: ********

You are now logged in as [none@none.com].
Your current project is [None].  You can change this setting by running:
  $ gcloud config set project PROJECT_ID
```

Once you've authenticated successfully, credentials are preserved in the volume of the gcloud-config container.

For simplicty create an alias by running:

```bash
alias mycloudsdk='docker run --rm --volumes-from gcloud-config -v ~/:/home/shared gcr.io/google.com/cloudsdktool/cloud-sdk'
```

4. List your projects by running:

```bash
docker run --rm --volumes-from gcloud-config gcr.io/google.com/cloudsdktool/cloud-sdk gcloud projects list

PROJECT_ID              NAME              PROJECT_NUMBER
winter-campaign-262200  My First Project  783709003945
```

Set the project name as a variable

```bash
PROJECT_NAME="winter-campaign-262200"
```

5. Set your current project by running:

```bash
docker run --rm --volumes-from gcloud-config gcr.io/google.com/cloudsdktool/cloud-sdk gcloud config set project $PROJECT_NAME

Updated property [core/project].
```

## Create GS Bucket

Set the bucket name and create the bucket

```bash
BUCKET_NAME="pvalle-jupyter-dataproc"
```

```bash
~$ docker run --rm --volumes-from gcloud-config gcr.io/google.com/cloudsdktool/cloud-sdk gsutil mb -p $PROJECT_NAME -c standard -l us-central1 gs://$BUCKET_NAME

Creating gs://pvalle-jupyter-dataproc/...
```

List my existing buckets by running:

```bash
~$ mycloudsdk gsutil ls gs://$BUCKET_NAME
```

## Uploading data to GS bucket

If you need to upload data to the created GS bucket, the alias created above can help. It mounts the home folder of the host system on the `/home/shared` directory inside the docker image.

You can confirm this by running this command:

```bash
mycloudsdk ls /home/shared
```

You should see all the files in your host system's home folder.

You can upload any file in your home folder by referring to it as it was in the `/home/shared` directory of the container.
So you can upload a file like so:

```bash
$ mycloudsdk gsutil cp /home/shared/README.md gs://$BUCKET_NAME
```

Sample output of this command:
```
Copying file:///home/shared/README.md [Content-Type=text/markdown]...
- [1 files][    8.0 B/    8.0 B]
Operation completed over 1 objects/8.0 B.
```

However this will *not* show up in your jupyter notebook. In order to do that, you have place files in `gs://$BUCKET_NAME/notebooks/jupyter`, like so:

```bash
$ mycloudsdk gsutil cp /home/shared/README.md gs://$BUCKET_NAME/notebooks/jupyter
```

Sample output of this command:
```
Copying file:///home/shared/README.md [Content-Type=text/markdown]...
/ [1 files][    8.0 B/    8.0 B]
Operation completed over 1 objects/8.0 B.
```


## Create a Cluster and install the Jupyter component

```bash
CLUSTER_NAME="pvalle-dataproc-cluster"
```

```bash
mycloudsdk gcloud beta dataproc clusters create $CLUSTER_NAME \
	--optional-components=ANACONDA,JUPYTER \
	--image-version=1.3 \
	--enable-component-gateway \
	--region=us-central1 \
	--num-workers=2 \
	--master-machine-type=n1-standard-1 \
	--worker-machine-type=n1-standard-1 \
	--bucket=$BUCKET_NAME \
	--tags=bigdata
```

List all your cluster by running:

```bash
~$ gcloud beta dataproc clusters list --region='us-central1'

NAME                     WORKER_COUNT  PREEMPTIBLE_WORKER_COUNT  STATUS   ZONE           SCHEDULED_DELETE
pvalle-dataproc-cluster  2                                       RUNNING  us-central1-c
```

## Open the Jupyter notebook in your local browser

See [Viewing and Accessing Component Gateway URLs](https://cloud.google.com/dataproc/docs/concepts/accessing/dataproc-gateways#viewing_and_accessing_component_gateway_urls) to click Component Gateway links on the Cloud Console to open the Jupyter notebook and JupyterLab UIs running on the cluster's master node in your local browser.

## Cleanup process

1. Remove Dataproc cluster

```bash
mycloudsdk gcloud beta dataproc clusters delete $CLUSTER_NAME --region='us-central1'
```

2. Remove GS bucket

```bash
mycloudsdk gsutil rm -r gs://$BUCKET_NAME
```

