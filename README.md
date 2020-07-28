# maven-runner

## Description

Simple plugin to run `mvn` command in git project dir.

## How to use it

```yml
#  Example that togeher with git clone, maven-runner plugin

envs:
  FLOWCI_GIT_URL: "https://github.com/FlowCI/spring-petclinic-sample.git"
  FLOWCI_GIT_BRANCH: "master"
  FLOWCI_GIT_REPO: "spring-petclinic"

docker:
  image: "maven:3.6-jdk-8"

steps:
  - name: clone
    plugin: 'gitclone'
    allow_failure: false

  - name: run unit test
    envs:
      MVN_CMD: "mvn clean test"
    plugin: 'maven-runner'
```

> For `mvnw`, you should change image to `openjdk` that without maven, or unset `MAVEN_CONFIG`.