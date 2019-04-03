# Description:    ALPINE/Oracle JDK 1.8

FROM alpine
MAINTAINER Ilyes BEN BRIK <ilyes.brik@gmail.com>

#I_ Make the OS preparations
  #1_ Install Curl

      RUN apk update  && apk add curl && apk add --no-cache --virtual=build-dependencies && apk add wget

  #2_ Install GLIBC

      RUN cd /tmp \
          && wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
          && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk \
          && apk add --no-cache glibc-2.28-r0.apk

  #3_ Activate Bash
    #a) Install bash
         RUN apk add bash
         RUN apk add bash-completion

    #b) Add bash to root user
         RUN sed -i 's/ash/bash/' /etc/passwd

#II_ Install Oracle JDK 1.8
  #1_ Download Oracle JDK 1.8

      RUN cd /tmp && \
          # curl -L -O -H "Cookie: oraclelicense=accept-securebackup-cookie" -k "https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.tar.gz"
          wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3a%2F%2Fwww.oracle.com%2Ftechnetwork%2Fjava%2Fjavase%2Fdownloads%2Fjdk8-downloads-2133151.html; oraclelicense=accept-securebackup-cookie;" "https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.tar.gz"
  #2_ Extract Oracle JDK 1.8 to its destination

      RUN cd /tmp && \
          mkdir  /usr/share/java && \
          tar xf jdk-8u201-linux-x64.tar.gz -C /usr/share/java && \
          rm -f jdk-8u201-linux-x64.tar.gz

  #2_ Organize the root folder of JAVA

      RUN ln -s /usr/share/java/jdk1.8.0_201 /usr/share/java/jdk
      RUN ln -s /usr/share/java/jdk /usr/share/java/jvm
      RUN chown -R root:root /usr/share/java

  #3_ Define JAVA_HOME variable and th PATH variable

      ENV JAVA_HOME=/usr/share/java/jdk
      ENV PATH=${PATH}:${JAVA_HOME}/bin

#III_ CLEAR Installation
  #1_ Uninstall unneeded packages

      RUN apk del build-dependencies && \
          rm -r "/tmp/"*
