# README

This repository documents the process of converting a frozen graph to a SavedModel and serve it via Tensorflow serving docker image.

## Documentation

The process is documented in a jupyter notebook - [Serving Object Detector Model via TF Serving.ipynb](Serving Object Detector Model via TF Serving.ipynb).
PDF format is also available [here](doc.pdf). 

## Final Docker Image

For demonstration purposes, a docker image has been created and hosted on Docker Hub. 
You can pull the docker image via this command.

```
docker pull as12production/sertis-object-detector:1.0
```

## Running the Docker Image

You can serve the image using the default ports by running this command.

```
docker run -it --rm -p 8500:8500 -p 8501:8501 --name sertis-detector --detach \
        -e MODEL_NAME=sertis-detector as12production/sertis-object-detector:1.0
```

## Testing the Prediction Service

A sample prediction can be executed by executing predict_via_rest_api.py script. Dependencies may have to be installed first.

```
python3 predict_via_rest_api.py
```

## Clean up

Be sure to shutdown the container.

```
docker stop sertis-detector  && docker rm sertis-detector
docker ps -a
```

Also remove any unused downloaded images to save your SSD space.
```
docker images
docker rmi [Image-ID]
```