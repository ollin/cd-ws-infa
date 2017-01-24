FROM jenkins:2.32.1
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
COPY plugins.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/install-plugins.sh ace-editor:1.1 ant:1.4 antisamy-markup-formatter:1.5 bouncycastle-api:2.16.0 branch-api:1.11.1 build-environment:1.6 build-timeout:1.18 cloudbees-folder:5.16 credentials:2.1.10 credentials-binding:1.10 display-url-api:0.5 durable-task:1.13 email-ext:2.53 external-monitor-job:1.7 git:3.0.1 git-client:2.2.1 git-server:1.7 github:1.25.1 github-api:1.84 github-branch-source:1.10.1 github-organization-folder:1.5 gradle:1.25 handlebars:1.1.1 icon-shim:2.0.3 jacoco:2.1.0 javadoc:1.4 job-dsl:1.57 jquery-detached:1.2.1 junit:1.19 ldap:1.13 mailer:1.18 mapdb-api:1.0.9.0 matrix-auth:1.4 matrix-project:1.8 momentjs:1.1.1 pam-auth:1.3 pipeline-build-step:2.4 pipeline-graph-analysis:1.3 pipeline-input-step:2.5 pipeline-milestone-step:1.3 pipeline-rest-api:2.4 pipeline-stage-step:2.2 pipeline-stage-view:2.4 plain-credentials:1.3 resource-disposer:0.6 saferestart:0.3 scm-api:1.3 script-security:1.25 ssh-credentials:1.12 ssh-slaves:1.12 structs:1.5 subversion:2.7.1 timestamper:1.8.7 token-macro:2.0 windows-slaves:1.2 workflow-aggregator:2.4 workflow-api:2.8 workflow-basic-steps:2.3 workflow-cps:2.24 workflow-cps-global-lib:2.5 workflow-durable-task-step:2.8 workflow-job:2.9 workflow-multibranch:2.9.2 workflow-remote-loader:1.3 workflow-scm-step:2.3 workflow-step-api:2.7 workflow-support:2.12 ws-cleanup:0.32
ENV JAVA_OPTS=-Djenkins.install.runSetupWizard=false
RUN curl -L https://github.com/docker/compose/releases/download/1.9.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose && \
    apt-get update && \
    apt-get install -y sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
COPY run.sh ./run.sh
RUN chmod +x ./run.sh
ENTRYPOINT ["/bin/bash","-c","./run.sh"]
