FROM debian:buster-slim

# Install git
RUN set -x \
  && apt-get update \
  && apt-get install --yes --no-install-recommends \
    git \
  && apt-get autoremove --purge \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Get autotag binary from image
COPY --from=quay.io/pantheon-public/autotag:latest /autotag /usr/bin/autotag

# Create mapping user
RUN set -x && \
  groupadd -g 1000 taglamenace && \
  useradd taglamenace --uid 1000 --gid 1000 --create-home --shell /bin/bash

USER taglamenace

WORKDIR /repository
VOLUME ["/repository"]

ENTRYPOINT ["/usr/bin/autotag"]
