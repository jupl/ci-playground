FROM jenkins/jenkins:2.89.4-alpine

USER root

# Install Docker CLI
RUN apk update && apk add docker sudo
RUN echo 'jenkins ALL=NOPASSWD: /usr/bin/docker' >> /etc/sudoers
ADD docker /usr/local/bin/docker

USER jenkins

# Install plugins
ADD plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
