FROM xataz/alpine:3.4
MAINTAINER xataz <https://github.com/xataz>

ARG DOCKER_VER=1.12.1

LABEL description="docker client for drone.io based on alpine" \
      tags="1.12.1 1.12 latest" \
      build_ver="2016110701"

RUN export BUILD_DEPS="wget \
            ca-certificates \
		    tar" \
    && apk add -U git \
                bash \
                ${BUILD_DEPS} \
    && bash -c "if [[ $DOCKER_VER != 1.11.* ]] && [[ $DOCKER_VER != 1.12.* ]]; then \
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
