FROM jamgood96/ruby:2.3.1

RUN BUILD_PACKAGES="build-base curl-dev gdbm-dev libffi-dev libxml2-dev \
                    libxslt-dev linux-headers ncurses-dev openssl-dev \
                    postgresql-dev readline-dev yaml-dev zlib-dev" && \
    apk --update --upgrade --no-cache add ${BUILD_PACKAGES}
