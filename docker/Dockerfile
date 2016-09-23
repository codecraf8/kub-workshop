############################################################
# Dockerfile to run a Django-based web application
# Based on an Ubuntu Image
############################################################

# Set the base image to use to Ubuntu
FROM ubuntu:14.04

# Set env variables used in this Dockerfile (add a unique prefix, such as DOCKYARD)
# Local directory with project source
ENV DEMO_SRC=hello_django
# Directory in container for all project files
ENV DEMO_HOME=/app
# Directory in container for project source files
ENV DEMO_SRVPROJ=/app/hello_django

# Update the default application repository sources list
RUN apt-get update && apt-get -y upgrade
RUN apt-get install -y python python-pip

# Create application subdirectories
WORKDIR $DEMO_HOME
RUN mkdir media static logs
VOLUME ["$DEMO_HOME/media/", "$DEMO_HOME/logs/"]

# Copy application source code to SRCDIR
COPY $DEMO_SRC $DEMO_PROJ

# Install Python dependencies
RUN pip install -r $DEMOD_PROJ/requirements.txt

# Port to expose
EXPOSE 8000

# Copy entrypoint script into the image
WORKDIR $DEMO_PROJ
COPY ./docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
