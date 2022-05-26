# Sample dockerfile to show root user privileges
FROM ubuntu:latest
RUN apt-get update
RUN apt-get install -y python python3-pip wget
RUN pip install Flask
#Add a user with userid 8877 and name nonroot
RUN useradd -s /bin/bash -u 1001 nonroot
#Run Container as nonroot
USER nonroot
