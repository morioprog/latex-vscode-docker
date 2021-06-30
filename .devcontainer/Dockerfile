# FROM paperist/alpine-texlive-ja:latest

# Copyright (c) 2016 Kaito Udagawa
# Copyright (c) 2016-2020 3846masa
# Released under the MIT license
# https://opensource.org/licenses/MIT

FROM frolvlad/alpine-glibc:latest

ENV PATH /usr/local/texlive/2021/bin/x86_64-linuxmusl:$PATH

RUN apk add --no-cache curl perl fontconfig-dev freetype-dev && \
    apk add --no-cache --virtual .fetch-deps xz tar wget && \
    mkdir /tmp/install-tl-unx && \
    curl -L ftp://tug.org/historic/systems/texlive/2021/install-tl-unx.tar.gz | \
    tar -xz -C /tmp/install-tl-unx --strip-components=1 && \
    printf "%s\n" \
    "selected_scheme scheme-basic" \
    "tlpdbopt_install_docfiles 0" \
    "tlpdbopt_install_srcfiles 0" \
    > /tmp/install-tl-unx/texlive.profile && \
    /tmp/install-tl-unx/install-tl \
    --profile=/tmp/install-tl-unx/texlive.profile && \
    tlmgr install \
    collection-latexextra \
    collection-fontsrecommended \
    collection-langjapanese \
    latexmk && \
    rm -fr /tmp/install-tl-unx && \
    apk del .fetch-deps

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
