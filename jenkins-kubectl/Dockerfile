FROM ubuntu:14.04

RUN apt-get update && apt-get install -y wget git curl && apt-get install -y software-properties-common
#openjdk-8-jdk install
RUN add-apt-repository  ppa:openjdk-r/ppa && apt-get update && apt-get install -y --no-install-recommends openjdk-8-jdk

RUN apt-get update && apt-get install -y maven ant ruby rbenv make
RUN echo "2.164.3" > .lts-version-number
RUN wget -q -O - http://pkg.jenkins-ci.org/debian-stable/jenkins-ci.org.key | sudo apt-key add -
RUN echo deb http://pkg.jenkins-ci.org/debian-stable binary/ >> /etc/apt/sources.list
RUN apt-get update && apt-get install -y jenkins
RUN mkdir -p /var/jenkins_home && chown -R jenkins /var/jenkins_home
ADD init.groovy /tmp/WEB-INF/init.groovy
RUN apt-get install -y zip && cd /tmp && zip -g /usr/share/jenkins/jenkins.war WEB-INF/init.groovy

#kubectl install
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && chmod +x ./kubectl && mv kubectl /usr/bin/ && kubectl
USER jenkins

ENV JENKINS_HOME /var/jenkins_home

# for main web interface:
EXPOSE 8080

# will be used by attached slave agents:
EXPOSE 50000
CMD ["/usr/bin/java",  "-jar",  "/usr/share/jenkins/jenkins.war"]
