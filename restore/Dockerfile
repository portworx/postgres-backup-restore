FROM alpine:3.15
LABEL maintainer="Praveen Perera <praveen@avencera.com>"

ENV WORKDIR /restore
WORKDIR $WORKDIR

## Install AWS CLI
# install pg_dump and python
RUN apk add --no-cache postgresql-client \
    python3 \
    py3-pip \
    py3-crcmod

## Install AWS CLI
RUN pip install awscli

ENV POSTGRES_DATABASE **None**
ENV POSTGRES_HOST **None**
ENV POSTGRES_PORT 5432
ENV POSTGRES_USER **None**
ENV POSTGRES_PASSWORD **None**
ENV S3_ACCESS_KEY_ID **None**
ENV S3_SECRET_ACCESS_KEY **None**
ENV S3_BUCKET **None**
ENV S3_REGION us-west-1
ENV S3_PATH 'backup'
ENV DROP_PUBLIC 'no'

ADD restore.sh restore.sh

ENV USER 88735
RUN adduser -D $USER
RUN chown --recursive $USER $WORKDIR
USER $USER

CMD ["sh", "restore.sh"]
