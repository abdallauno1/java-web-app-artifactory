# java-web-app-artifactory

# Sample repository

* https://github.com/abdallauno1/java-web-app-artifactory
* be sure to use the `main` branch

# JFrog CLI documentation

* https://jfrog.com/getcli/
* https://www.jfrog.com/confluence/display/CLI/JFrog+CLI
* https://www.jfrog.com/confluence/display/CLI/CLI+for+JFrog+Artifactory#CLIforJFrogArtifactory-UploadingFiles

# Run Artifactory with Docker Compose

```
version: '2'
services:
  artifactory:
    image: docker.bintray.io/jfrog/artifactory-oss:latest
    container_name: artifactory
    ports:
      - "8081:8081"
      - "8082:8082"
```