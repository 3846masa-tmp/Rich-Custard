# Ubuntu with sshd
# Usage: docker run -d -P -v ${HOME}/.ssh/id_rsa.pub:/root/.ssh/authorized_keys 3846masa/ubuntu-base

FROM dockerfile/ubuntu
MAINTAINER 3846masa <3846masahiro+git@gmail.com>

RUN apt update && apt install -y openssh-server supervisor

RUN mkdir -p /var/run/sshd /root/.ssh

RUN sed -i /etc/ssh/sshd_config \
        -e 's/ServerKeyBits/#ServerKeyBits/g' \
        -e 's/StrictModes yes/StrictModes no/g' \
        -e 's/#AuthorizedKeysFile/AuthorizedKeysFile/g' \
        -e 's/#PasswordAuthentication yes/PasswordAuthentication no/g' \
        -e 's/UsePam yes/UsePam no/g'

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

EXPOSE 22

CMD ["/usr/bin/supervisord"]
