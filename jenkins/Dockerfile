FROM jenkins:2.46.3
MAINTAINER Oliver Nautsch
USER root
RUN apt-get update && \
    apt-get install -y apt-transport-https ca-certificates && \
    apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D && \
    echo "deb https://apt.dockerproject.org/repo debian-jessie main" >> /etc/apt/sources.list.d/docker.list && \
    apt-get update && \
    apt-get install -y docker-engine && \
    gpasswd -a jenkins docker && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN /usr/local/bin/install-plugins.sh ace-editor:1.1 ant:1.5 antisamy-markup-formatter:1.5 authentication-tokens:1.3 blueocean:1.0.1 blueocean-autofavorite:0.7 blueocean-commons:1.0.1 blueocean-config:1.0.1 blueocean-dashboard:1.0.1 blueocean-display-url:2.0 blueocean-events:1.0.1 blueocean-git-pipeline:1.0.1 blueocean-github-pipeline:1.0.1 blueocean-i18n:1.0.1 blueocean-jwt:1.0.1 blueocean-personalization:1.0.1 blueocean-pipeline-api-impl:1.0.1 blueocean-pipeline-editor:0.2.0 blueocean-rest:1.0.1 blueocean-rest-impl:1.0.1 blueocean-web:1.0.1 bouncycastle-api:2.16.1 branch-api:2.0.9 build-environment:1.6 build-timeout:1.18 cloudbees-folder:6.0.4 credentials:2.1.13 credentials-binding:1.11 display-url-api:2.0 docker-commons:1.6 docker-workflow:1.11 durable-task:1.13 email-ext:2.57.2 external-monitor-job:1.7 favorite:2.0.4 git:3.3.0 git-client:2.4.6 git-server:1.7 github:1.27.0 github-api:1.85 github-branch-source:2.0.5 github-organization-folder:1.6 gradle:1.26 handlebars:1.1.1 icon-shim:2.0.3 jackson2-api:2.7.3 jacoco:2.2.1 job-dsl:1.63 jquery-detached:1.2.1 junit:1.20 ldap:1.15 mailer:1.20 mapdb-api:1.0.9.0 matrix-auth:1.6 matrix-project:1.11 metrics:3.1.2.9 momentjs:1.1.1 pam-auth:1.3 pipeline-build-step:2.5 pipeline-github-lib:1.0 pipeline-graph-analysis:1.3 pipeline-input-step:2.7 pipeline-milestone-step:1.3.1 pipeline-model-api:1.1.4 pipeline-model-declarative-agent:1.1.1 pipeline-model-definition:1.1.4 pipeline-model-extensions:1.1.4 pipeline-rest-api:2.8 pipeline-stage-step:2.2 pipeline-stage-tags-metadata:1.1.4 pipeline-stage-view:2.8 plain-credentials:1.4 pubsub-light:1.8 resource-disposer:0.6 saferestart:0.3 scm-api:2.1.1 script-security:1.27 sse-gateway:1.15 ssh-credentials:1.13 ssh-slaves:1.17 structs:1.7 subversion:2.7.2 timestamper:1.8.8 token-macro:2.1 variant:1.1 windows-slaves:1.3.1 workflow-aggregator:2.5 workflow-api:2.15 workflow-basic-steps:2.4 workflow-cps:2.32 workflow-cps-global-lib:2.8 workflow-durable-task-step:2.11 workflow-job:2.11 workflow-multibranch:2.14 workflow-scm-step:2.4 workflow-step-api:2.10 workflow-support:2.14 ws-cleanup:0.33
ENV JAVA_OPTS=-Djenkins.install.runSetupWizard=false
RUN curl -L https://github.com/docker/compose/releases/download/1.13.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose && \
    apt-get update && \
    apt-get install -y sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
COPY run.sh ./run.sh
RUN chmod +x ./run.sh
ENTRYPOINT ["/bin/bash","-c","./run.sh"]
