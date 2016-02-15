FROM alpine:3.3

RUN apk add --no-cache curl

ENV DOCKER_BUCKET github.com/armhf-docker-library/docker-build/releases/download/1.10.1
ENV DOCKER_VERSION 1.10.1
ENV DOCKER_SHA256 71f0d0dcda7de6605d5dadcb72541109b3bbdff120ef20db74a6fc20cb96553b

RUN curl -fSL "https://${DOCKER_BUCKET}/docker-$DOCKER_VERSION" -o /usr/local/bin/docker \
	&& echo "${DOCKER_SHA256}  /usr/local/bin/docker" | sha256sum -c - \
	&& chmod +x /usr/local/bin/docker

COPY docker-entrypoint.sh /usr/local/bin/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["sh"]
