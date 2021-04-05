ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

RUN apk add --no-cache py3-pip

WORKDIR /usr/src/SomfyProtect2MQTT
ARG SOMFY_PROTECT_2_MQTT_VERSION

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        python3 \
        python3-pip \
        git \
        python-json2yaml \
    \
    && git clone --depth 1 -b ${SOMFY_PROTECT_2_MQTT_VERSION} \
        "https://github.com/Minims/SomfyProtect2MQTT" . \
    && rm -rf .git \
    && pip3 install --no-cache-dir -r somfyProtect2Mqtt/requirements.txt \
    \
    && apt-get purge -y --auto-remove \
        git \
        python-json2yaml \
    && rm -rf /var/lib/apt/lists/*


COPY run.sh /
RUN chmod a+x /run.sh
CMD [ "/run.sh" ]
