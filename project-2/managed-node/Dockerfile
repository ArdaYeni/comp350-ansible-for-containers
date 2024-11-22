FROM python:3.9-slim

RUN apt-get update && \
    apt-get install -y python3 openssh-server && \
    mkdir -p /var/run/sshd

RUN mkdir -p /root/.ssh && mkdir -p /var/run/sshd

COPY id_rsa.pub /root/.ssh/authorized_keys

RUN chmod 600 /root/.ssh/authorized_keys

EXPOSE 22 80

CMD ["/usr/sbin/sshd", "-D"]