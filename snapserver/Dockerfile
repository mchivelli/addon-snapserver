ARG BUILD_FROM
FROM $BUILD_FROM

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install necessary packages
RUN apk add --no-cache \
        pulseaudio \
        alsa-plugins-pulse \
        bash \
        librespot=0.6.0-r0 \
        snapcast-server=0.30.0-r0 \
    --repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing/ \
    --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community/

# Install Snapweb
RUN wget https://github.com/badaix/snapweb/releases/download/v0.8.0/snapweb.zip && \
    unzip -o snapweb.zip -d /usr/share/snapserver/snapweb/ && \
    rm snapweb.zip

# Copy run script
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
