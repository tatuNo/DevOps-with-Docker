FROM ubuntu:18.04

WORKDIR /usr

COPY ./script .

RUN apt-get update && apt-get install git -y

RUN apt-get install docker.io -y

RUN chmod +x script

ENTRYPOINT ["./script"]