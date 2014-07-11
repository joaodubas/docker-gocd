# go continuous delivery agent
#
# VERSION: see `TAG`
FROM joaodubas/gocd-base:latest
MAINTAINER Joao Paulo Dubas "joao.dubas@gmail.com"

# download server
ENV GOVERSION 14.1.0
ENV GOMINOR ${GOVERSION}-18882
ENV GOFILE go-agent-${GOMINOR}.zip
ENV GOURL http://download01.thoughtworks.com/go
RUN mkdir -p /opt/src \
    && cd /opt/src \
    && wget ${GOURL}/${GOVERSION}/ga/${GOFILE}

# install server
RUN cd /opt/src \
    && unzip ${GOFILE} \
    && ln -s /opt/src/go-agent-${GOVERSION} /opt/src/go-agent \
    && chmod 754 /opt/src/go-agent/agent.sh

# remove unused files
RUN rm -rf /opt/src/${GOFILE}

# command
CMD ["/opt/src/go-agent/agent.sh"]
