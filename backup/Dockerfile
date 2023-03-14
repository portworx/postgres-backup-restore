FROM alpine:3.15
LABEL maintainer="Praveen Perera <praveen@avencera.com>"

ENV WORKDIR /backup
WORKDIR $WORKDIR

RUN apk update

# install pg_dump and python
RUN apk add --no-cache postgresql-client \
    python3 \
    py3-pip \
    py3-crcmod

## Install AWS CLI
RUN pip install --upgrade pip
RUN pip install awscli
RUN pip install certifi --upgrade
RUN pip install setuptools --upgrade

# cleanup
RUN rm -rf /var/cache/apk/*

ENV POSTGRES_DATABASE **None**
ENV POSTGRES_HOST **None**
ENV POSTGRES_PORT 5432
ENV POSTGRES_USER **None**
ENV POSTGRES_PASSWORD **None**
ENV POSTGRES_EXTRA_OPTS ''
ENV S3_ACCESS_KEY_ID **None**
ENV S3_SECRET_ACCESS_KEY **None**
ENV S3_BUCKET **None**
ENV S3_REGION us-west-1
ENV S3_PATH 'backup'
ENV S3_ENDPOINT **None**
ENV S3_S3V4 no
ENV SCHEDULE **None**

ADD run.sh run.sh
ADD backup.sh backup.sh

# Run as an arbitrary non-root user for security reasons.
ENV USER 88735
RUN adduser -D $USER
RUN chown --recursive $USER $WORKDIR
USER $USER

CMD ["sh", "run.sh"]
