FROM centos:7

# Install packages necessary to run EAP
RUN yum update -y && yum -y install xmlstarlet saxon augeas bsdtar unzip && yum clean all

# Create a user and group used to launch processes
# The user ID 1000 is the default for the first "regular" user on Fedora/RHEL,
# so there is a high chance that this ID will be equal to the current user
# making it easier to use volumes (no permission issues)
RUN groupadd -r focus -g 1000 && useradd -u 1000 -r -g focus -m -d /opt/focus -s /sbin/nologin -c "Focus user" focus && \
    chmod 755 /opt/focus

# Set the working directory to focus' user home directory
WORKDIR /opt/focus

# Specify the user which should be used to execute all commands below
USER focus
