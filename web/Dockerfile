FROM python:3.10

ARG version

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

RUN apt-get update && \
    apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install \
        default-mysql-client \
        libsasl2-dev \
        libssl-dev \
        libldap2-dev \
        git && \
    apt-get clean
    
RUN echo "$version"

RUN git clone https://github.com/LCBRU/image_study_merge.git /usr/src/app/
ADD gunicorn.conf /usr/src/app/gunicorn.conf

RUN pip install --no-cache-dir gunicorn
RUN pip install --no-cache-dir -r requirements.txt