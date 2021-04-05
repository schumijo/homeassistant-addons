ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

RUN apk add --no-cache py3-pip

# add source and unpack
ADD "https://github.com/Minims/SomfyProtect2MQTT/archive/refs/heads/dev.zip" /src.zip
RUN mkdir /app && unzip /src.zip -d /app

# install all (and json2yaml for cofiguration parsing)
RUN pip3 install python-json2yaml
WORKDIR /app/SomfyProtect2MQTT-dev/somfyProtect2Mqtt
RUN pip3 install -r requirements.txt

COPY run.sh /
RUN chmod a+x /run.sh
CMD [ "/run.sh" ]