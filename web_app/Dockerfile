#For webapp development
FROM biolockj/webapp
RUN rm -r $BLJ/web_app/*
COPY . $BLJ/web_app/
ENV PROJECT_DIRS=$BLJ/web_app

# Add AWS
ARG DEBIAN_FRONTEND=noninteractive
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get update && apt-get install -y \
 python-dev \
 python-pip \
 python-tk
# install AWS CLI
RUN pip install awscli --upgrade
RUN aws --version

# Add git
RUN apt-get update && \
  apt-get install -y git \
  curl \
  vim

#RUN rm /package.json
#RUN rm /app.js
#if the new BLJ webapp doesn't pull the latest webapp, run these
# docker build --tag amyerke/webapp --no-cached .
# if mike updates his:
# docker pull biolockj/webapp && docker build --tag amyerke/webapp .
WORKDIR $BLJ/web_app/

# Install Malcolm's repo
#git clone https://github.com/mjzapata/AWSBatchGenomicsStack