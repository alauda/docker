FROM adoptopenjdk/openjdk11:jdk-11.0.11_9-debianslim-slim

RUN echo 'deb http://ftp.debian.org/debian bullseye main' >> /etc/apt/sources.list.d/bullseye.list && \
    apt-get update -y && \
    apt-get install unzip -y && \
    apt-get install bash -y && \
    apt-get install dirmngr -y && \
    apt-get install gnupg -y && \
    apt-get install gnupg-l10n -y && \
    apt-get install gnupg-utils -y && \
    apt-get install gpg -y && \
    apt-get install gpg-agent -y && \
    apt-get install gpg-wks-client -y && \
    apt-get install gpg-wks-server -y && \
    apt-get install gpgconf -y && \
    apt-get install gpgsm -y && \
    apt-get install git -y && \
    apt-get install git-man -y && \
    apt-get install libc-bin -y && \
    apt-get install libc6 -y && \
    apt-get install libc-dev-bin -y && \
    apt-get install libc-devtools -y && \
    apt-get install libc6-dev -y && \
    apt-get install locales -y && \
    apt-get install libc-l10n -y && \
    apt-get install libidn2-0 -y && \
    apt-get install libgcc1 -y && \
    apt-get install gcc-8-base -y && \
    apt-get install gcc-9 -y && \
    apt-get install liblz4-1 -y && \
    apt-get install libpcre2-8-0 -y && \
    apt-get install libpng16-16 -y && \
    apt-get install python2.7 -y && \
    apt-get install python2.7-minimal -y && \
    apt-get install libpython2.7-minimal -y && \
    apt-get install libpython2.7-stdlib -y && \
    apt-get install python-all -y && \
    apt-get install sqlite3 -y && \
    apt-get install libsqlite3-0 -y && \
    apt-get install libssh2-1 -y && \
    apt-get install libsystemd0 -y && \
    apt-get install libudev1 -y && \
    apt-get install tar -y && \
    apt-get install libgcrypt20 -y && \
    apt-get install libnettle8 -y && \
    apt-get install nettle-bin -y && \
    apt-get install nettle-dev -y && \
    apt-get install golang-golang-x-crypto-dev -y && \
    apt-get install libcommons-beanutils-java -y && \
    apt-get install libcommons-beanutils-java-doc -y && \
    apt-get install ant -y && \
    apt-get install jetty9 -y && \
    apt-get install libspring-aop-java -y && \
    apt-get install libspring-beans-java -y && \
    apt-get install libspring-context-java -y && \
    apt-get install libspring-context-support-java -y && \
    apt-get install libspring-core-java -y && \
    apt-get install libspring-expression-java -y && \
    apt-get install libspring-instrument-java -y && \
    apt-get install libspring-jdbc-java -y && \
    apt-get install libspring-jms-java -y && \
    apt-get install libspring-messaging-java -y && \
    apt-get install libspring-orm-java -y && \
    apt-get install libspring-oxm-java -y && \
    apt-get install libspring-test-java -y && \
    apt-get install libspring-transaction-java -y && \
    apt-get install libspring-web-java -y && \
    apt-get install libspring-web-portlet-java -y && \
    apt-get install libspring-web-servlet-java -y && \
    apt-get install curl -y && \
    apt-get install libgnutls30/testing -y && \
    apt-get install libseccomp2 -y && \
    apt-get install lz4 -y && \
    apt-get install binutils -y && apt-get install binutils-common -y && apt-get install binutils-x86-64-linux-gnu -y && apt-get install libbinutils -y && apt-get install libctf-nobfd0 -y && \
    apt-get install libctf0 -y && \
    apt-get install libdom4j-java -y && \
    apt-get install libgd3 -y && \
    apt-get install libgif7 -y && \
    apt-get install libglib2.0-0 -y && \
    apt-get install libglib2.0-data -y && \
    apt-get install libgssapi-krb5-2 -y && \
    apt-get install libicu67 -y && \
    apt-get install libjdom1-java -y && \
    apt-get install libjpeg62-turbo -y && \
    apt-get install libk5crypto3 -y && \
    apt-get install libkrb5-3 -y && \
    apt-get install libkrb5support0 -y && \
    apt-get install libnss3 -y && \
    apt-get install libxml2 -y && \
    apt-get install libxmlgraphics-commons-java -y && \
    apt-get install libxstream-java -y && \
    apt-get install libyaml-snake-java -y && \
    apt-get install linux-libc-dev -y && \
    apt-get install libc3p0-java -y && \
    apt-get install libhibernate3-java -y && \
    apt-get install libxstream-java -y && \
    apt-get install libavahi-client3 -y && apt-get install libavahi-common-data -y && apt-get install libavahi-common3 -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ARG GIT_LFS_VERSION=2.13.3

# required for multi-arch support, revert to package cloud after:
# https://github.com/git-lfs/git-lfs/issues/4546
COPY git_lfs_pub.gpg /tmp/git_lfs_pub.gpg
RUN GIT_LFS_ARCHIVE="git-lfs-linux-$(dpkg --print-architecture)-v${GIT_LFS_VERSION}.tar.gz" \
    GIT_LFS_RELEASE_URL="https://github.com/git-lfs/git-lfs/releases/download/v${GIT_LFS_VERSION}/${GIT_LFS_ARCHIVE}"\
    set -x; curl --fail --silent --location --show-error --output "/tmp/${GIT_LFS_ARCHIVE}" "${GIT_LFS_RELEASE_URL}" && \
    curl --fail --silent --location --show-error --output "/tmp/git-lfs-sha256sums.asc" https://github.com/git-lfs/git-lfs/releases/download/v${GIT_LFS_VERSION}/sha256sums.asc && \
    gpg --no-tty --import /tmp/git_lfs_pub.gpg && \
    gpg -d /tmp/git-lfs-sha256sums.asc | grep "${GIT_LFS_ARCHIVE}" | (cd /tmp; sha256sum -c ) && \
    mkdir -p /tmp/git-lfs && \
    tar xzvf "/tmp/${GIT_LFS_ARCHIVE}" -C /tmp/git-lfs && \
    bash -x /tmp/git-lfs/install.sh && \
    rm -rf /tmp/git-lfs*

ARG user=jenkins
ARG group=jenkins
ARG uid=1000
ARG gid=1000
ARG http_port=8080
ARG agent_port=50000
ARG JENKINS_HOME=/var/jenkins_home
ARG REF=/usr/share/jenkins/ref

ENV JENKINS_HOME $JENKINS_HOME
ENV JENKINS_SLAVE_AGENT_PORT ${agent_port}
ENV REF $REF

# Jenkins is run with user `jenkins`, uid = 1000
# If you bind mount a volume from the host or a data container,
# ensure you use the same uid
RUN mkdir -p $JENKINS_HOME \
  && chown ${uid}:${gid} $JENKINS_HOME \
  && groupadd -g ${gid} ${group} \
  && useradd -d "$JENKINS_HOME" -u ${uid} -g ${gid} -m -s /bin/bash ${user}

# Jenkins home directory is a volume, so configuration and build history
# can be persisted and survive image upgrades
VOLUME $JENKINS_HOME

# $REF (defaults to `/usr/share/jenkins/ref/`) contains all reference configuration we want
# to set on a fresh new installation. Use it to bundle additional plugins
# or config file with your custom jenkins Docker image.
RUN mkdir -p ${REF}/init.groovy.d

# Use tini as subreaper in Docker container to adopt zombie processes
ARG TINI_VERSION=v0.16.1
COPY tini_pub.gpg ${JENKINS_HOME}/tini_pub.gpg
RUN curl -fsSL https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-static-$(dpkg --print-architecture) -o /sbin/tini \
  && curl -fsSL https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-static-$(dpkg --print-architecture).asc -o /sbin/tini.asc \
  && gpg --no-tty --import ${JENKINS_HOME}/tini_pub.gpg \
  && gpg --verify /sbin/tini.asc \
  && rm -rf /sbin/tini.asc /root/.gnupg \
  && chmod +x /sbin/tini

# jenkins version being bundled in this docker image
ARG JENKINS_VERSION
ENV JENKINS_VERSION ${JENKINS_VERSION:-2.235.4}

COPY jenkins.war /usr/share/jenkins/jenkins.war

ENV JENKINS_UC https://updates.jenkins.io
ENV JENKINS_UC_EXPERIMENTAL=https://updates.jenkins.io/experimental
ENV JENKINS_INCREMENTALS_REPO_MIRROR=https://repo.jenkins-ci.org/incrementals
RUN chown -R ${user} "$JENKINS_HOME" "$REF"

ARG PLUGIN_CLI_VERSION=2.9.3
ARG PLUGIN_CLI_URL=https://github.com/jenkinsci/plugin-installation-manager-tool/releases/download/${PLUGIN_CLI_VERSION}/jenkins-plugin-manager-${PLUGIN_CLI_VERSION}.jar
RUN curl -fsSL ${PLUGIN_CLI_URL} -o /opt/jenkins-plugin-manager.jar

# for main web interface:
EXPOSE ${http_port}

# will be used by attached agents:
EXPOSE ${agent_port}

ENV COPY_REFERENCE_FILE_LOG $JENKINS_HOME/copy_reference_file.log

USER ${user}

COPY jenkins-support /usr/local/bin/jenkins-support
COPY jenkins.sh /usr/local/bin/jenkins.sh
COPY tini-shim.sh /bin/tini
COPY jenkins-plugin-cli.sh /bin/jenkins-plugin-cli

ENTRYPOINT ["/sbin/tini", "--", "/usr/local/bin/jenkins.sh"]

# from a derived Dockerfile, can use `RUN install-plugins.sh active.txt` to setup $REF/plugins from a support bundle
COPY install-plugins.sh /usr/local/bin/install-plugins.sh

# metadata labels
LABEL \
    org.opencontainers.image.vendor="Jenkins project" \
    org.opencontainers.image.title="Official Jenkins Docker image" \
    org.opencontainers.image.description="The Jenkins Continuous Integration and Delivery server" \
    org.opencontainers.image.version="${JENKINS_VERSION}" \
    org.opencontainers.image.url="https://www.jenkins.io/" \
    org.opencontainers.image.source="https://github.com/jenkinsci/jenkins" \
    org.opencontainers.image.licenses="MIT"
