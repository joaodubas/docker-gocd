# go continuous delivery agent
#
# VERSION: see `TAG`
FROM joaodubas/gocd-base:latest
MAINTAINER Joao Paulo Dubas "joao.dubas@gmail.com"

# download agent
ENV GOVERSION 14.2.0
ENV GOMINOR ${GOVERSION}-377
ENV GOFILE go-agent-${GOMINOR}.zip
ENV GOURL http://download.go.cd/gocd
RUN mkdir -p /opt/src \
    && cd /opt/src \
    && wget ${GOURL}/${GOFILE}

# install server
RUN cd /opt/src \
    && unzip ${GOFILE} \
    && ln -s /opt/src/go-agent-${GOVERSION} /opt/src/go-agent \
    && chmod 754 /opt/src/go-agent/agent.sh

# remove unused files
RUN rm -rf /opt/src/${GOFILE}

# command
CMD ["/opt/src/go-agent/agent.sh"]
