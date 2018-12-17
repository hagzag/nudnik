FROM ubuntu:16.04

RUN apt-get update && apt-get -y install python python-pip dnsutils iputils-ping && apt-get clean all

RUN pip install nudnik

EXPOSE 5410

ENTRYPOINT [ "nudnik" ]
