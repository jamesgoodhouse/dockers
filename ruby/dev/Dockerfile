FROM jamgood96/ruby:2.1.7-alpine3.4

RUN BUILD_PACKAGES="build-base curl-dev freetds-dev gdbm-dev libgcrypt-dev \
                    libffi-dev libxml2-dev libxslt-dev linux-headers \
                    ncurses-dev nodejs openssl-dev postgresql-dev python \
                    readline-dev yaml-dev zlib-dev" && \
    MISC_PACKAGES="git openssh postgresql-client" && \
    apk --update --upgrade --no-cache add ${BUILD_PACKAGES} ${MISC_PACKAGES}

ENV NOKOGIRI_USE_SYSTEM_LIBRARIES="1"
