FROM arm32v7/openjdk:latest

EXPOSE 8080

RUN apt-get update; apt-get --yes install \
    apt-transport-https \
    curl \
    git \
    ca-certificates \
    gnupg-agent \
    software-properties-common && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    add-apt-repository "deb [arch=armhf] https://download.docker.com/linux/debian $(lsb_release -cs) stable" && \
    apt-get update && \
    apt-get --yes install \
    docker-ce docker-ce-cli containerd.io docker-compose && \
    apt-get clean && apt-get autoremove -q && \
    rm -rf /var/lib/apt/lists/* /usr/share/doc /usr/share/man /tmp/*

ENV JENKINS_HOME /var/jenkins_home

RUN mkdir -p /var/jenkins_home
RUN useradd --no-create-home --shell /bin/sh jenkins
RUN chown -R jenkins:jenkins /var/jenkins_home/
ADD http://mirrors.jenkins-ci.org/war-stable/2.289.2/jenkins.war /var/jenkins_home.war
RUN chmod 644 /var/jenkins_home.war

CMD ["/usr/bin/java", "-jar", "/var/jenkins_home.war"]
