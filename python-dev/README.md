# python-dev

This will run jupyterlab on port 8888 with password "junyeop".

Base docker image is [`python:3.9-slim-bullseye`](https://hub.docker.com/_/python).

The following Python packages are installed.
- boto3
- dask
- pymongo
- jupyterlab

Usage:

    docker-compose up
