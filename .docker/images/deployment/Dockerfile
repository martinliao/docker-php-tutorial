FROM busybox as prod

RUN mkdir /codebase

COPY ./.docker/ /codebase/.docker/
COPY ./.make/ /codebase/.make/
COPY ./Makefile /codebase/

# copy files to the /shared directory that should be shared with the host system
RUN echo "#!/bin/sh" > "/entrypoint.sh" && \
    echo "cp -r /codebase/.docker/ /shared/" >> "/entrypoint.sh" && \
    echo "cp -r /codebase/.make/ /shared/" >> "/entrypoint.sh" && \
    echo "cp -r /codebase/Makefile /shared/" >> "/entrypoint.sh" && \
    chmod +x "/entrypoint.sh"
 
ENTRYPOINT ["/entrypoint.sh"]
