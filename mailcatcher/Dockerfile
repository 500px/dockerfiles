FROM alpine:latest

# Add mailcatcher user and group
RUN addgroup -S mailcatcher && \
    adduser -S -H -D mailcatcher -G mailcatcher -g "mailcatcher user"

# Envs
ENV MAILCATCHER_VERSION 0.6.4

# Install ruby, tools and mailcatcher
RUN apk update && apk upgrade && \
    apk add build-base su-exec curl sqlite-dev ruby ruby-dev && \
    gem install --no-ri --no-rdoc bigdecimal && \
    gem install --no-ri --no-rdoc mailcatcher --version $MAILCATCHER_VERSION && \
    rm -rf /var/cache/apk/*

# Entrypoint
EXPOSE 1080 1025
ENTRYPOINT ["su-exec", "mailcatcher:mailcatcher", "/usr/bin/mailcatcher"]
CMD ["--smtp-ip=0.0.0.0", "--http-ip=0.0.0.0", "--http-port=1080", "--smtp-port=1025", "--foreground"]
