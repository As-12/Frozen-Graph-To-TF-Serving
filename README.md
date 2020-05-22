# README

This is a notebook project documenting the process of converting a frozen graph file and serve it via Tensorflow serving,

## Documentation

Please see the notebook for documentation regarding this process - [Doc](https://github.com/As-12/Frozen-Graph-To-TF-Serving/blob/master/Serving%20Object%20Detector%20Model%20via%20TF%20Serving.ipynb).


## Final Docker Image

You can pull the docker image via this command.

```
docker pull as12production/sertis-object-detector:1.0
```

## Running the docker image

Serve the image using the default ports.

```
docker run -it --rm -p 8500:8500 -p 8501:8501 --name sertis-detector --detach \
        -e MODEL_NAME=sertis-detector as12production/sertis-object-detector:1.0
```

## Executing test code

A sample prediction can be executed by running. Prerequisites may have to be installed first.

```
python3 predict_via_rest_api.py
```

## Clean up

Be sure to shutdown the container and remove the image by executing these command.

```
docker stop sertis-detector  && docker rm sertis-detector
docker ps -a
```

Besure to remove the downloaded images.
```
docker images
docker rmi [Image-ID]
```
