FROM dockerfile/java:oracle-java8

MAINTAINER tsukaby

RUN apt-get update

# Copy application
RUN mkdir /usr/local/anime-lineup
ENV APP_SHA1 5f6c18c14ffff2fa5bb73489b87887fb9dee2b72
RUN wget https://s3-ap-northeast-1.amazonaws.com/anime-lineup/binary/anime-lineup-${APP_SHA1}.jar -O /usr/local/anime-lineup/anime-lineup.jar

WORKDIR /usr/local/anime-lineup

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "-Dskinny.port=8080", "-Dskinny.env=production", "anime-lineup.jar"]
