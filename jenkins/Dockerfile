FROM jenkins/jenkins:lts
USER root

RUN apt-get update && apt-get install -y python-pip

COPY .ssh/ /usr/share/jenkins/ref/.ssh
COPY entrypoint.sh /entrypoint.sh

RUN chown -R 1000:1000 /usr/share/jenkins/ref/.ssh \
    && chmod 644 /usr/share/jenkins/ref/.ssh/id_rsa

RUN chown 1000:1000 /entrypoint.sh \
    && chmod +x /entrypoint.sh

RUN pip install ansible pywinrm

USER jenkins

ENTRYPOINT ["/entrypoint.sh"]
