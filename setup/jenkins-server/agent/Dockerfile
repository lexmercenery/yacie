FROM openjdk:8
LABEL maintainer="lexmercenery@gmail.com"

ENV MD5 63b3733b875ab4615e91e911a7d5fd45

RUN mkdir -p /var/jenkins_home \
 && useradd -d /var/jenkins_home/worker -u 1000 -m -s /bin/bash jenkins \
 && curl -o /bin/swarm-client.jar -SL http://repo.jenkins-ci.org/releases/org/jenkins-ci/plugins/swarm-client/3.4/swarm-client-3.4.jar \
 && echo "$MD5  /bin/swarm-client.jar" | md5sum -c - \
 && apt-get update \
 && apt-get install --no-install-recommends bzip2 \
 && rm -rf /var/lib/apt/lists/*

COPY docker-entrypoint.sh /
RUN chmod +x docker-entrypoint.sh
WORKDIR /var/jenkins_home/worker

USER jenkins
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["java", "-jar", "/bin/swarm-client.jar", "-fsroot", "/var/jenkins_home/worker/"]



