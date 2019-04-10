# Description Pyhton/Scrapy

FROM python
MAINTAINER Ilyes BEN BRIK <ilyes.brik@gmail.com>

# Update OS
    RUN apt-get update
    
# Install Scrapy
    RUN pip install Scrapy

# Create a workspace

    RUN mkdir /workspace && chmod -R 644 /workspace
    VOLUME /workspace

# Make the container running

    WORKDIR /workspace
    CMD ["/bin/bash"]
