# NAME:     jiaji/homeland
FROM homeland/base:0.2.3
MAINTAINER Jiaji Yin "https://github.com/Fykec"

ENV RAILS_ENV 'production'
RUN curl https://get.acme.sh | sh

ENV HOMELAND_VERSION '158e53d07287bab0bd0d263b34eefa1806f5613f'

RUN useradd ruby -s /bin/bash -m -U &&\
    mkdir -p /var/www &&\
    cd /var/www &&\
    git clone https://github.com/maoyouhui/homeland.git
RUN cd /var/www/homeland &&\
    git pull && git checkout ${HOMELAND_VERSION} &&\
    bundle install --deployment &&\
    find /var/www/homeland/vendor/bundle -name tmp -type d -exec rm -rf {} + &&\
    chown -R ruby:ruby /var/www

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

WORKDIR /var/www/homeland
