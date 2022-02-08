FROM paperist/alpine-texlive-ja:latest

RUN apk update && \
    apk upgrade && \
    apk add --no-cache \
    git \
    openssh \
    make \
    perl-log-log4perl \
    perl-log-dispatch \
    perl-yaml-tiny \
    perl-unicode-linebreak && \
    apk add --no-cache \
    -X http://dl-cdn.alpinelinux.org/alpine/edge/testing \
    perl-file-homedir

RUN tlmgr option repository ctan && \
    tlmgr update --self && \
    tlmgr install latexindent

ARG USER_NAME
ARG USER_ID
ARG GROUP_ID

RUN addgroup -g $GROUP_ID $USER_NAME
RUN adduser --disabled-password -h /home/$USER_NAME -s /bin/bash -u $USER_ID -G $USER_NAME $USER_NAME

RUN echo "Defaults visiblepw"                  >> /etc/sudoers
RUN echo "${USER_NAME} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER ${USER_ID}:${GROUP_ID}
