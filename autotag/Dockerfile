FROM alpine:latest

# Install git
RUN apk add --no-cache git

# Get autotag binary from image
COPY --from=quay.io/pantheon-public/autotag:latest /autotag /usr/bin/autotag

# Create mapping user
RUN set -x && \
  addgroup -g 1000 taglamenace && \
  adduser taglamenace -S -u 1000 -G taglamenace -H

USER taglamenace

WORKDIR /repository
VOLUME ["/repository"]

ENTRYPOINT ["/usr/bin/autotag"]
