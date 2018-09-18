# Description:    ALPINE/Oracle JDK 1.8

FROM alpine
MAINTAINER Ilyes BEN BRIK <ilyes.brik@gmail.com>

#I_ Make the OS preparations
  #1_ Install Curl

      RUN apk update  && apk add curl && apk add --no-cache --virtual=build-dependencies 

      RUN cd /tmp \
          && wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
          && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk \
          && apk add --no-cache glibc-2.28-r0.apk

  #2_ Activate Bash
    #a) Install bash
         RUN apk add bash
         RUN apk add bash-completion

    #b) Add bash to root user
         RUN set -i 's/bin/ash/bin/bash' /etc/passwd

#II_ Install Oracle JDK 1.8
  #1_ Download Oracle JDK 1.8

      RUN cd /tmp && \
          curl -L -O -H "Cookie: oraclelicense=accept-securebackup-cookie" -k "http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/jdk-8u181-linux-x64.tar.gz" && \
          mkdir  /usr/share/java && \
          tar xf jdk-8u181-linux-x64.tar.gz -C /usr/share/java && \
          rm -f jdk-8u181-linux-x64.tar.gz 

  #2_ Organize the root folder of JAVA
 
      RUN ln -s /usr/share/java/jdk1.8.0_181 /usr/share/java/jdk
      RUN ln -s /usr/share/java/jdk /usr/share/java/jvm
      RUN chown -R root:root /usr/share/java

  #3_ Define JAVA_HOME variable and th PATH variable

      ENV JAVA_HOME=/usr/share/java/jdk 
      ENV PATH=${PATH}:${JAVA_HOME}/bin

#III_ CLEAR Installation
  #1_ Uninstall unneeded packages
      
      RUN apk del build-dependencies && \
          rm -r "/tmp/"*
