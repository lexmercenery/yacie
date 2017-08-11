
# Yet Another Continuous Integration Environment set  

#### List of instances:
* Jenkins Master 
* Scalable jenkins swarm agent
* Scalable selenium grid nodes with chrome and firefox 
* Nexus3
* Sonarcube
* Postgresql database 
* Portainer 


**Jenkins Master**  
Based on latest LTS version of official [jenkins docker image](https://hub.docker.com/_/jenkins/).  
Tо preinstall extra plugins in to jenkins, paste Plugin ID to **Jenkins Master** dockerfile  
To attach jenkins agents, create user in jenkins credentials settings and write his credentials in to `jenkinsagent` variables.  
Added  variables: `TZ=Europe/Minsk` set yours, default is `UTC`. Workaround to view cucumber test reports in jenkins pages `ENV JAVA_ARGS="\"-Dhudson.model.DirectoryBrowserSupport.CSP`   
For more info, see official [readme](https://github.com/jenkinsci/docker/blob/master/README.md) 

**Jenkins Agent**  
Based on official [openjdk docker image](https://hub.docker.com/r/library/openjdk/) with installed [Jenkins Swarm client 3.4](http://repo.jenkins-ci.org/releases/org/jenkins-ci/plugins/swarm-client/3.4/)  
To scale jenkins agents, run `docker-compose scale jenkinsagent={number of replicas}`  
List of variables see on `docker-entrypoint.sh` by default you need to configure only username, password and master-address 

**Selenium Grid Nodes**  
Based on official selenium [chrome node image](https://hub.docker.com/r/selenium/node-chrome/) and [firefox node image](https://hub.docker.com/r/selenium/node-firefox/)  
After start you will have one chrome node with 5 browsers and FullHD screen resolution, and one firefox node with 3 browsers.  
See preinstall variables in `docker-compose.yml` [full variables list](https://github.com/SeleniumHQ/docker-selenium/blob/master/NodeBase/Dockerfile)     
To scale chrome nodes, run `docker-compose scale grchrome={number of replicas}`  
To scale firefox nodes, run `docker-compose scale grfirefox={number of replicas}`  
 
**Nexus Server**  
Run fom official [sonatype nexus3 docker image](https://hub.docker.com/r/sonatype/nexus3/)  
Sonatype Nexus is a repository manager with free support for popular formats.

**SonarQube Server**  
Run fom official [sonarqube docker image](https://hub.docker.com/_/sonarqube/) with additional postgesql database container  
SonarQube is an open source platform for continuous inspection of code quality.  

**Portainer**  
Run from official [portainer docker image](https://hub.docker.com/r/portainer/portainer/)  
Portainer is a lightweight management UI which allows you to easily manage your Docker host or Swarm cluster.  
More info [official site](https://portainer.io/)
 
 
#### How to use:  

 execute`docker-compose up`