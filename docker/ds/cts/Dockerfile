FROM 673492047887.dkr.ecr.us-east-1.amazonaws.com/bwolfefrcdk/ds-base:7.2.0

USER root

COPY debian-buster-sources.list /etc/apt/sources.list

RUN chown -R forgerock:root /opt/opendj
USER forgerock
COPY --chown=forgerock:root common  /opt/opendj/
COPY --chown=forgerock:root cts     /opt/opendj/
COPY --chown=forgerock:root scripts /opt/opendj/scripts
ARG profile_version
RUN bin/setup.sh && \
    bin/relax-security-settings.sh  && \
    rm bin/setup.sh bin/relax-security-settings.sh
