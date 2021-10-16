FROM timescale/timescaledb-postgis:latest-pg13

# Install pgloader
RUN echo '@testing http://nl.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories && \
      apk add --update --no-cache bzip2 curl freetds-dev gawk git sqlite-dev libzip-dev make patch sbcl@testing unzip wget

RUN git clone https://github.com/dimitri/pgloader.git /opt/src/pgloader

RUN mkdir -p /opt/src/pgloader/build/bin \
    && cd /opt/src/pgloader \
    && make


# Set up maintenance
COPY ./maintenance /usr/local/bin/maintenance
RUN chmod +x /usr/local/bin/maintenance/*
RUN mv /usr/local/bin/maintenance/* /usr/local/bin \
    && rmdir /usr/local/bin/maintenance
