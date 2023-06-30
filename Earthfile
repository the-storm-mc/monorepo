VERSION 0.7
PROJECT sjerred/monorepo

pipeline.push:
  PIPELINE --push
  TRIGGER push main
  BUILD +deploy.web
  BUILD +deploy.servers
  BUILD +devcontainer

deploy.web:
  BUILD ./docs+deploy --prod=true
  BUILD ./site+deploy --prod=true

deploy.servers:
  BUILD ./server+deploy --stage=infra
  WAIT
    BUILD ./server+deploy --stage=beta
  END
  WAIT
    BUILD ./server+deploy --stage=prod
  END

git:
  FROM ubuntu:jammy
  COPY .git .git
  SAVE ARTIFACT .git

devcontainer:
  FROM earthly/dind:ubuntu
  WORKDIR /workspace
  ARG TARGETARCH
  ARG version=0.1.11-beta.0
  RUN curl --location --fail --silent --show-error -o /usr/local/bin/devpod https://github.com/loft-sh/devpod/releases/download/v$version/devpod-linux-$TARGETARCH
  RUN chmod +x /usr/local/bin/devpod
  COPY .devcontainer/devcontainer.json .
  RUN --push --secret GITHUB_TOKEN=github_token echo $GITHUB_TOKEN | docker login ghcr.io -u shepherdjerred --password-stdin
  WITH DOCKER
    RUN devpod provider add docker && \
      devpod build github.com/the-storm-mc/monorepo --repository ghcr.io/the-storm-mc/monorepo
  END
