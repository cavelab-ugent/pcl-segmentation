# FROM  nvcr.io/nvidia/pytorch:23.04-py3

FROM python:3.8-slim-buster

# install environment dependencies
RUN apt-get update -yqq \
    && apt-get install -yqq --no-install-recommends git libgl1 libx11-6\
    build-essential gcc freetds-dev freetds-bin\
    && apt-get -q clean \
    apt install nvidia-cudnn

# set the working directory
WORKDIR /project

# copy files to the image
COPY ./requirements.txt .

# install requirements
RUN python -m pip install --upgrade pip wheel setuptools\
    && pip install ez_setup \
    && pip install -r requirements.txt --no-cache-dir \
    && rm -r /root/.cache

# Install development packages
# RUN git clone https://github.com/woutervdbroeck/Open3D-ML \ 
#     && pip install -e ./Open3D-ML 

# RUN pip install git+https://github.com/cavelab-ugent/pcl-segmentation
    
# Run shell commands
# CMD ["jupyter-lab", "--ip", "0.0.0.0", "--allow-root"]