
# Get Docker CLI from the official Docker image
FROM docker:cli AS dockercli

# Start with Jenkins
FROM jenkins/jenkins:lts

USER root

# Copy Docker CLI into Jenkins
COPY --from=dockercli /usr/local/bin/docker /usr/local/bin/docker

USER jenkins
