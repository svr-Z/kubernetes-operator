FROM debian:bookworm-slim

LABEL maintainer="Jenkins Kubernetes Operator Community" \
      org.opencontainers.image.authors="Jenkins Kubernetes Operator Community" \
      org.opencontainers.image.title="backup-pvc" \
      org.opencontainers.image.description="Jenkins Operator Backup img via pvc volume" \
      org.opencontainers.image.url="quay.io/jenkins-kubernetes-operator/backup-pvc" \
      org.opencontainers.image.source="https://github.com/jenkinsci/kubernetes-operator/tree/master/backup/pvc" \
      org.opencontainers.image.base.name="debian:bookworm-slim"

ARG UID
ARG GID

ENV USER=user

RUN apt update \
   && apt install -y procps zstd \
   && rm -rf /var/lib/apt/lists/* \
   && addgroup --gid "$GID" "$USER" && \
    adduser \
    --disabled-password \
    --gecos "" \
    --ingroup "$USER" \
    --uid "$UID" \
    "$USER"

COPY bin/*.sh /home/user/bin/
RUN chmod -R a+rx /home/user
WORKDIR /home/user/bin
USER user

CMD ./run.sh
