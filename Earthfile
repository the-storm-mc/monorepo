VERSION 0.7
PROJECT sjerred/monorepo

pipeline.pr:
  PIPELINE
  TRIGGER pr main
  BUILD ./docs+deploy
  BUILD ./site+deploy

pipeline.push:
  PIPELINE --push
  TRIGGER push main
  BUILD +web
  # BUILD +servers

web:
  BUILD ./docs+deploy --prod=true
  BUILD ./site+deploy --prod=true

server.update:
  ARG --required stage
  WAIT
    BUILD ./server+down --stage=$stage
  END
  WAIT
    BUILD ./server+sync --stage=$stage
  END
  WAIT
    BUILD ./server+pull --stage=$stage
  END
  WAIT
    BUILD ./server+up --stage=$stage
  END

servers:
  BUILD +server.update --stage=infra
  WAIT
    BUILD +server.update --stage=beta
  END
  WAIT
    BUILD +server.update --stage=prod
  END

git:
  FROM ubuntu:jammy
  COPY .git .git
  SAVE ARTIFACT .git
