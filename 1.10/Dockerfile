FROM alpine:3.3

RUN apk add --no-cache curl

ENV DOCKER_BUCKET github.com/umiddelb/armhf/raw/master/bin
ENV DOCKER_VERSION 1.8.3
ENV DOCKER_SHA256 c2fe5cb1987692d98e796e06922b5e305b2435945e1c08987ea8c6c4570183a7

RUN curl -fSL "https://${DOCKER_BUCKET}/docker-$DOCKER_VERSION" -o /usr/local/bin/docker \
	&& echo "${DOCKER_SHA256}  /usr/local/bin/docker" | sha256sum -c - \
	&& chmod +x /usr/local/bin/docker

COPY docker-entrypoint.sh /usr/local/bin/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["sh"]
