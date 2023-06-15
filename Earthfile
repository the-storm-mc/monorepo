VERSION 0.7
PROJECT sjerred/monorepo

preview:
  PIPELINE
  TRIGGER pr main
  BUILD ./docs+deploy
  BUILD ./site+deploy

push:
  PIPELINE --push
  TRIGGER push main
  BUILD ./docs+deploy --prod=true
  BUILD ./site+deploy --prod=true
  WAIT
    BUILD ./server+build --stage=beta
  END
  BUILD ./server+build --stage=prod

git:
  FROM ubuntu:jammy
  COPY .git .git
  SAVE ARTIFACT .git
