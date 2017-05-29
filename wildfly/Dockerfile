# Use latest focus/jdk:7 image as the base
FROM focus/jdk:7

# Set the WILDFLY_VERSION env variable
ENV WILDFLY_VERSION 8.2.0.Final
ENV WILDFLY_SHA1 d78a864386a9bc08812eed9781722e45812a7826
ENV WILDFLY_HOME /opt/focus/wildfly
ENV DEPLOYMENT_DIR ${WILDFLY_HOME}/standalone/deployments/

USER root

# Add the WildFly distribution to /opt, and make wildfly the owner of the extracted tar content
# Make sure the distribution is available from a well-known place
RUN cd $HOME \
    && curl -O https://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz \
    && sha1sum wildfly-$WILDFLY_VERSION.tar.gz | grep $WILDFLY_SHA1 \
    && tar xf wildfly-$WILDFLY_VERSION.tar.gz \
    && mv $HOME/wildfly-$WILDFLY_VERSION $WILDFLY_HOME \
    && rm wildfly-$WILDFLY_VERSION.tar.gz \
		&& mkdir -p /app/logs ${WILDFLY_HOME}/standalone/log \
		&& chown -R focus:focus /app/logs \
    && chown -R focus:focus ${WILDFLY_HOME} \
    && chmod -R g+rw ${WILDFLY_HOME}

USER focus		
# Ensure signals are forwarded to the JVM process correctly for graceful shutdown
ENV LAUNCH_WILDFLY_IN_BACKGROUND true



# Expose stuff to outside world
EXPOSE 8080

VOLUME ["/app/logs", "${WILDFLY_HOME}/standalone/log"]

# Set the default command to run on boot
# This will boot WildFly in the standalone mode and bind to all interface
CMD ["${WILDFLY_HOME}/bin/standalone.sh", "-b", "0.0.0.0"]



