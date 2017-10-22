FROM jenkins/jenkins:lts
# if we want to install via apt
USER root

RUN apt-get update \
        && apt-get install -y curl ca-certificates \
        && curl -s https://get.docker.com/ | sed 's/docker-engine/docker-engine=%%DOCKER_VERSION%%*/' | sh \
        && echo 'DOCKER_OPTS="-H :2375 -H unix:///var/run/docker.sock"' >> /etc/default/docker \
        && chown jenkins:jenkins /var/run/docker.sock \
        && usermod -aG docker jenkins

# drop back to the regular jenkins user - good practice
USER jenkins