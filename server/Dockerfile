# go continuous delivery server
#
# VERSION: see `TAG`
FROM joaodubas/gocd-base:latest
MAINTAINER Joao Paulo Dubas "joao.dubas@gmail.com"

# download server
ENV GOVERSION 14.2.0
ENV GOMINOR ${GOVERSION}-377
ENV GOFILE go-server-${GOMINOR}.zip
ENV GOURL http://download.go.cd/gocd
RUN mkdir -p /opt/src \
    && cd /opt/src \
    && wget ${GOURL}/${GOFILE}

# install server
RUN cd /opt/src \
    && unzip ${GOFILE} \
    && ln -s /opt/src/go-server-${GOVERSION} /opt/src/go-server \
    && chmod 754 /opt/src/go-server/server.sh

# remove unused files
RUN rm -rf /opt/src/${GOFILE}

# command
EXPOSE 8153
CMD ["/opt/src/go-server/server.sh"]
