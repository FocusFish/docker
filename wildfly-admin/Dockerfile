FROM focusfish/wildfly
RUN /opt/focus/wildfly/bin/add-user.sh admin admin --silent
EXPOSE 9990
CMD ["/opt/focus/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]