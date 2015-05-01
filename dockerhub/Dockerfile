FROM dockerfile/java:oracle-java8

MAINTAINER tsukaby

RUN apt-get update

# Copy application
RUN mkdir /usr/local/anime-lineup
ENV APP_SHA1 dafa30dfd12cd97935cf2c2280050a45a906ee02
RUN wget https://s3-ap-northeast-1.amazonaws.com/anime-lineup/binary/anime-lineup-${APP_SHA1}.jar -O /usr/local/anime-lineup/anime-lineup.jar

WORKDIR /usr/local/anime-lineup

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "-Dskinny.port=8080", "-Dskinny.env=production", "anime-lineup.jar"]