FROM debian:stretch
LABEL maintainers="Markus Langer <langer.markus@gmail.com>"
LABEL description="csi-s3 slim image"

# s3fs and some other dependencies
RUN apt-get update && \
  apt-get install -y \
  s3fs curl unzip && \
  rm -rf /var/lib/apt/lists/*

# install rclone
ARG RCLONE_VERSION=v1.47.0
RUN cd /tmp \
  && curl -O https://downloads.rclone.org/${RCLONE_VERSION}/rclone-${RCLONE_VERSION}-linux-arm64.zip \
  && unzip /tmp/rclone-${RCLONE_VERSION}-linux-arm64.zip \
  && mv /tmp/rclone-*-linux-arm64/rclone /usr/bin \
  && rm -r /tmp/rclone*

COPY ./_output/s3driver /s3driver
ENTRYPOINT ["/s3driver"]
