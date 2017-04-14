FROM jamgood96/base:alpine3.4

RUN PACKAGES="curl freetds gdbm libffi libpq libstdc++ libxml2 libxslt \
              ncurses nodejs openssl readline tzdata yaml zlib" && \
    apk --update --upgrade --no-cache add ${PACKAGES}

# RUBY ------------------------------------------------------------------------
ENV RUBY_MAJOR_VERSION="2.1" \
    RUBY_VERSION="2.1.7" \
    BUNDLE_SILENCE_ROOT_WARNING="1"

RUN BUILD_PACKAGES="build-base gdbm-dev libffi-dev linux-headers ncurses-dev \
                    openssl-dev readline-dev yaml-dev zlib-dev" && \
    apk --update --upgrade --no-cache add ${BUILD_PACKAGES} && \

    curl -sSL "http://cache.ruby-lang.org/pub/ruby/${RUBY_MAJOR}/ruby-${RUBY_VERSION}.tar.bz2" | \
      tar -xj && \
    cd /ruby-${RUBY_VERSION} && \
    ./configure --disable-install-doc && \
    make && \
    make install && \
    gem update --system --no-document && \

    # all about the gems, baby
    gem install --no-document bundler && \
    echo 'gem: --no-document' >> ~/.gemrc && \
    cp ~/.gemrc /etc/gemrc && \
    chmod uog+r /etc/gemrc && \

    # cleanup
    apk del ${BUILD_PACKAGES} && \
    cd / && \
    rm -rf /ruby-${RUBY_VERSION} \
           /usr/local/lib/ruby/gems/*/cache/* \
           ~/.gem \
           /tmp/*
