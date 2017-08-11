FROM jenkins/jenkins:lts
LABEL maintainer="lexmercenery@gmail.com"

RUN /usr/local/bin/install-plugins.sh \
    active-directory \
    blueocean \
    copyartifact \
    docker-plugin \
    docker-workflow \
    gitlab-plugin \
    htmlpublisher\
    sonar \
    nodejs \
    pipeline-utility-steps \
    selenium \
    seleniumhtmlreport \
    slack \
    swarm \
    testng-plugin \
    thinBackup \
    workflow-aggregator

EXPOSE 4444

