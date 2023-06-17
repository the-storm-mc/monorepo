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
  BUILD +deploy.web
  BUILD +deploy.servers

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
