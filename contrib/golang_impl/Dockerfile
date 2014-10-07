FROM scratch
MAINTAINER Michal Fojtik <mfojtik@redhat.com>

# This is an ugly hack to create directories without 'mkdir' command.
#
ADD ./tmp/.gitignore /var/run/.gitignore
ADD ./tmp/.gitignore /data/docker_index/.gitignore

# Add statically compiled docker-registry
#
ADD ./bin/docker-registry /bin/docker-registry

# You can have external mounted volume for the docker images
#
VOLUME ["/data/docker_index"]

EXPOSE 5000

# TODO: Remove the -D=true (debug)
#
CMD ["/bin/docker-registry", "-l", "0.0.0.0:5000", "-D", "true"]
