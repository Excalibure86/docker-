# Description OracleJDK/RobotFramework

FROM excalibure/oracle-jdk
MAINTAINER Ilyes BEN BRIK <ilyes.brik@gmail.com>

# Update system
    RUN apk update

# Install python 3
    RUN apk add --no-cache python3 && \
        python3 -m ensurepip && \
        rm -r /usr/lib/python*/ensurepip && \
        pip3 install --upgrade pip setuptools && \
        if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
        if [[ ! -e /usr/bin/python ]]; then ln -sf /usr/bin/python3 /usr/bin/python; fi && \
        rm -r /root/.cache

# Install RobotFramework
    RUN pip3 install robotframework

# Create a workspace

    RUN mkdir /workspace && chmod -R 644 /workspace
    VOLUME /workspace

# Make the container running

    WORKDIR /root
    CMD ["/bin/bash"]
