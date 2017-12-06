FROM jenkins/jenkins:lts
# see at https://hub.docker.com/r/jenkins/jenkins/
# uses debian
MAINTAINER Oliver Nautsch
USER root
RUN apt-get update && \
    apt-get install -y apt-transport-https ca-certificates curl software-properties-common && \
    apt-key adv --fetch-keys https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg && \
    apt-key fingerprint 0EBFCD88 && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") $(lsb_release -cs) stable" && \
    apt-get update && \
    apt-get install -y docker-ce && \
    gpasswd -a jenkins docker && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN /usr/local/bin/install-plugins.sh ace-editor:1.1 ant:1.7 antisamy-markup-formatter:1.5 apache-httpcomponents-client-4-api:4.5.3-2.0 authentication-tokens:1.3 blueocean:1.3.4 blueocean-autofavorite:1.2.1 blueocean-bitbucket-pipeline:1.3.4 blueocean-commons:1.3.4 blueocean-config:1.3.4 blueocean-dashboard:1.3.4 blueocean-display-url:2.2.0 blueocean-events:1.3.4 blueocean-git-pipeline:1.3.4 blueocean-github-pipeline:1.3.4 blueocean-i18n:1.3.4 blueocean-jira:1.3.4 blueocean-jwt:1.3.4 blueocean-personalization:1.3.4 blueocean-pipeline-api-impl:1.3.4 blueocean-pipeline-editor:1.3.4 blueocean-pipeline-scm-api:1.3.4 blueocean-rest:1.3.4 blueocean-rest-impl:1.3.4 blueocean-web:1.3.4 bouncycastle-api:2.16.2 branch-api:2.0.16 build-environment:1.6 build-timeout:1.19 cloudbees-bitbucket-branch-source:2.2.7 cloudbees-folder:6.2.1 credentials:2.1.16 credentials-binding:1.13 display-url-api:2.2.0 docker-commons:1.9 docker-workflow:1.14 durable-task:1.17 email-ext:2.61 external-monitor-job:1.7 favorite:2.3.1 git:3.6.4 git-client:2.6.0 git-server:1.7 github:1.28.1 github-api:1.90 github-branch-source:2.3.1 github-organization-folder:1.6 gradle:1.28 handlebars:1.1.1 htmlpublisher:1.14 icon-shim:2.0.3 jackson2-api:2.8.7.0 jacoco:2.2.1 jira:2.5 job-dsl:1.66 jquery-detached:1.2.1 jsch:0.1.54.1 junit:1.23 ldap:1.18 mailer:1.20 mapdb-api:1.0.9.0 matrix-auth:2.2 matrix-project:1.12 mercurial:2.2 metrics:3.1.2.10 momentjs:1.1.1 pam-auth:1.3 pipeline-build-step:2.5.1 pipeline-github-lib:1.0 pipeline-graph-analysis:1.5 pipeline-input-step:2.8 pipeline-milestone-step:1.3.1 pipeline-model-api:1.2.5 pipeline-model-declarative-agent:1.1.1 pipeline-model-definition:1.2.5 pipeline-model-extensions:1.2.5 pipeline-rest-api:2.9 pipeline-stage-step:2.3 pipeline-stage-tags-metadata:1.2.5 pipeline-stage-view:2.9 plain-credentials:1.4 pubsub-light:1.12 resource-disposer:0.8 saferestart:0.3 scm-api:2.2.5 script-security:1.36 sse-gateway:1.15 ssh-credentials:1.13 ssh-slaves:1.22 structs:1.10 subversion:2.9 timestamper:1.8.8 token-macro:2.3 variant:1.1 windows-slaves:1.3.1 workflow-aggregator:2.5 workflow-api:2.24 workflow-basic-steps:2.6 workflow-cps:2.42 workflow-cps-global-lib:2.9 workflow-durable-task-step:2.17 workflow-job:2.15 workflow-multibranch:2.16 workflow-scm-step:2.6 workflow-step-api:2.14 workflow-support:2.16 ws-cleanup:0.34
ENV JAVA_OPTS=-Djenkins.install.runSetupWizard=false
RUN curl -L https://github.com/docker/compose/releases/download/1.17.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose && \
    apt-get update && \
    apt-get install -y sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
COPY run.sh ./run.sh
RUN chmod +x ./run.sh
ENTRYPOINT ["/bin/bash","-c","./run.sh"]
