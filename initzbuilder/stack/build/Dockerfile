# Define the base image
FROM initializbuildpacks/go-securepack-base:latest
 
# Switch to the root user to install packages
USER root
 
# Update package database and install dependencies
RUN apk update && \
    apk del libcrypt1  && \
    apk add \
         ca-certificates-bundle \
         wolfi-base \
         libexpat1 \
         libssl3 \
         yaml \
         openssl \
         tzdata \
         zlib \
         libstdc++ \
         fontconfig
        
# Create symbolic link for libpcre
RUN ln -s /usr/lib/libpcre.so.1 /usr/lib/libpcre.so.3
 
# Switch back to the non-root user
USER cnb
 
# Set required CNB target information
LABEL io.buildpacks.base.distro.name="wolfi"
LABEL io.buildpacks.base.distro.version="20230201"
 
LABEL io.buildpacks.stack.id="Initializ Distroless Stack"
 
ENV CNB_STACK_ID="Initializ Distroless Stack"