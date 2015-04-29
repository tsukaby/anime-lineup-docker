FROM centos

MAINTAINER tsukaby

# Install common tools
RUN yum install -y git curl; yum upgrade -y; yum update -y

# Install java
ENV JDK_VERSION 8u40
ENV JDK_BUILD_VERSION b26
RUN curl -LO "http://download.oracle.com/otn-pub/java/jdk/$JDK_VERSION-$JDK_BUILD_VERSION/jdk-$JDK_VERSION-linux-x64.rpm" -H 'Cookie: oraclelicense=accept-securebackup-cookie' && rpm -i jdk-$JDK_VERSION-linux-x64.rpm; rm -f jdk-$JDK_VERSION-linux-x64.rpm; yum clean all
RUN yum clean all
ENV JAVA_HOME /usr/java/default

# Copy application
RUN mkdir /usr/local/anime-lineup
RUN wget https://s3-ap-northeast-1.amazonaws.com/anime-lineup/binary/anime-lineup-5f6c18c14ffff2fa5bb73489b87887fb9dee2b72.jar -O /usr/local/anime-lineup/anime-lineup.jar

WORKDIR /usr/local/anime-lineup

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "-Dskinny.port=8080", "-Dskinny.env=production", "anime-lineup.jar"]
