FROM alpine:3.3 
MAINTAINER xataz <https://github.com/xataz> 

ARG DOCKER_VER=1.10.3

RUN export BUILD_DEPS="wget \
            ca-certificates \
		    tar" \
    && apk add -U git \
                bash \
                ${BUILD_DEPS} \
    && bash -c "if [[ $DOCKER_VER != 1.11.* ]]; then \
                    wget https://get.docker.com/builds/Linux/x86_64/docker-${DOCKER_VER} -O /usr/bin/docker; \
                else \
	                wget https://get.docker.com/builds/Linux/x86_64/docker-${DOCKER_VER}.tgz -O /tmp/docker.tgz; \
                    tar xzvf /tmp/docker.tgz -C /tmp; \
                    mv /tmp/docker/* /usr/bin/; \
                fi" \
    && chmod +x /usr/bin/docker* \
    && apk del ${BUILD_DEPS} \
    && rm -rf /var/cache/apk/* /tmp/* 
   

CMD ["bash"] 