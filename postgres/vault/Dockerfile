FROM vault:1.2.0-beta2
RUN apk add --no-cache jq \
    && wget https://releases.hashicorp.com/consul/1.5.2/consul_1.5.2_linux_amd64.zip \
    && unzip consul_1.5.2_linux_amd64.zip \
    && rm consul_1.5.2_linux_amd64.zip \
    && mv consul /usr/local/bin/