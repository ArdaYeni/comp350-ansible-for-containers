FROM python:3.9-slim

RUN apt-get update && \
    apt-get install -y python3 python3-pip openssh-client && \
    pip3 install ansible

COPY ansible/ /etc/ansible/

COPY id_rsa /root/.ssh/id_rsa
COPY id_rsa.pub /root/.ssh/id_rsa.pub

RUN chmod 600 /root/.ssh/id_rsa && chmod 644 /root/.ssh/id_rsa.pub

WORKDIR /etc/ansible

RUN chown -R root:root /etc/ansible && chown -R root:root /root/.ssh

CMD ["/bin/bash"]
