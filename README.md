# Python docker image for raspberry pi

This container is designed to match the `python:3.5` container as closely as
possible to be used as a base image for creating a
[Home Assistant](https://home-assistant.io) image.

## Building
Running the following command inside the `3.5` directory will build the image:
```
docker build -t blakeblackshear/rpi-python:3.5 .
```
