# Description OracleJDK/RobotFramework

FROM python
MAINTAINER Ilyes BEN BRIK <ilyes.brik@gmail.com>

# Update system
    RUN apt-get update

# Install RobotFramework
    RUN pip3 install robotframework

# Create a workspace

    RUN mkdir /workspace && chmod -R 644 /workspace
    VOLUME /workspace

# Make the container running

    WORKDIR /root
    CMD ["/bin/bash"]
