ARG BUILD_FROM
FROM $BUILD_FROM
ENV LANG C.UTF-8

# EnedisGateway2MQTT version
ARG VERSION=0.3.0

# Install required packages
RUN apk add --no-cache py3-pip
RUN pip3 install python-json2yaml

# Download source and untar
WORKDIR /usr/src
ADD "https://github.com/m4dm4rtig4n/enedisgateway2mqtt/archive/refs/tags/${VERSION}.tar.gz" src.tar.gz
RUN tar -xvf src.tar.gz
RUN mv /usr/src/EnedisGateway2MQTT-${VERSION} /usr/src/EnedisGateway2MQTT

# Install python requirements
WORKDIR /usr/src/EnedisGateway2MQTT/EnedisGateway2MQTT
RUN pip3 install -r requirements.txt

# Run script
COPY run.sh /
RUN chmod a+x /run.sh
CMD [ "/run.sh" ]
