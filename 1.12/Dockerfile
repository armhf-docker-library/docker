FROM alpine:3.4

RUN apk add --no-cache \
		ca-certificates \
		curl \
		openssl

ENV DOCKER_BUCKET github.com/armhf-docker-library/docker-build/releases/download/1.12.1
ENV DOCKER_VERSION 1.12.1
ENV DOCKER_SHA256 ca7ce875110ae78d1665fc06d863c794c9e5a140f8c534f4342b0ecf1266d325

RUN set -x \
	&& curl -fSL "https://${DOCKER_BUCKET}/docker-$DOCKER_VERSION.tgz" -o docker.tgz \
	&& echo "${DOCKER_SHA256} *docker.tgz" | sha256sum -c - \
	&& tar -xzvf docker.tgz \
	&& mv docker/* /usr/local/bin/ \
	&& rmdir docker \
	&& rm docker.tgz \
	&& docker -v

COPY docker-entrypoint.sh /usr/local/bin/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["sh"]
