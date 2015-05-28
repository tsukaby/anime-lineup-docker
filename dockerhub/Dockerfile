FROM java:8

MAINTAINER tsukaby

RUN apt-get update

RUN apt-get -y install bzip2

# PhantomJS
RUN apt-get -y install libfontconfig
ENV PHANTOM_VERSION 1.9.8
WORKDIR /tmp
RUN wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOM_VERSION-linux-x86_64.tar.bz2
RUN bzip2 -dc phantomjs-$PHANTOM_VERSION-linux-x86_64.tar.bz2 | tar xvf -
RUN mv phantomjs-$PHANTOM_VERSION-linux-x86_64/bin/phantomjs /usr/local/bin/

# Reconfig
## Locale
RUN apt-get -y install locales
RUN sed -i -e "s/# ja_JP.UTF-8 UTF-8/ja_JP.UTF-8 UTF-8/g" /etc/locale.gen
RUN locale-gen
RUN update-locale LANG=ja_JP.UTF-8

## TimeZone
RUN echo "Asia/Tokyo" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata

# Copy application
RUN mkdir /usr/local/anime-lineup
ENV APP_SHA1 027f2eebf4741bb67755b7f5c95980541191721e
RUN wget https://s3-ap-northeast-1.amazonaws.com/anime-lineup/binary/anime-lineup-${APP_SHA1}.jar -O /usr/local/anime-lineup/anime-lineup.jar

WORKDIR /usr/local/anime-lineup

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "-Dskinny.port=8080", "-Dskinny.env=production", "anime-lineup.jar"]
