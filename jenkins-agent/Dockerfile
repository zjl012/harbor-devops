FROM harbor.mycorp.local/ci/jenkins-inbound-agent:latest-jdk17

USER root

COPY buildctl /usr/local/bin/ 
COPY harbor-ca.crt /usr/local/share/ca-certificates/
COPY kubectl /usr/local/bin/
COPY helm /usr/bin/

RUN chmod +x /usr/local/bin/buildctl \
 && chmod +x /usr/local/bin/kubectl \
 && chmod +x /usr/bin/helm \
 && sed -i 's|deb.debian.org|mirrors.aliyun.com|g' /etc/apt/sources.list.d/* \
 && sed -i 's|security.debian.org|mirrors.aliyun.com|g' /etc/apt/sources.list.d/* \
 && apt-get update \
 && apt-get install -y ca-certificates curl \
 && rm -rf /var/lib/apt/lists/* \
 && update-ca-certificates 

USER jenkins

