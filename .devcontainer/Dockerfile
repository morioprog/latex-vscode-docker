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
