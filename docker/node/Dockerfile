FROM node:6-alpine

RUN export LC_ALL=C.UTF-8

RUN echo @edge http://nl.alpinelinux.org/alpine/edge/main >> /etc/apk/repositories && \
    echo /etc/apk/respositories && \
    apk update

RUN apk add --no-cache \
    openssh \
    git \
    nano \
    curl \
    bash \
    wget \
    openssl \
    libressl@edge \
    ca-certificates

RUN git config --global user.email "nikolas.serko@gmail.com" \
    && git config --global user.name "Nikolas Serko" \
    && git config --global push.default current

RUN mkdir -p /code && \
    chmod 775 /code && \
    rm -rf /var/cache/apk/* /tmp/* /usr/share/man

RUN npm install -g bower webpack yar

WORKDIR /code

RUN adduser -s /bin/bash -D -h /home/serko -u 1111 serko

EXPOSE 8888

#ENTRYPOINT ["/bin/sh"]
#CMD ["/usr/local/bin/node"]