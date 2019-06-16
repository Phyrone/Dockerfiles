FROM ubuntu
MAINTAINER Phyrone<phyrone@phyrone.de>
ENV DEBIAN_FRONTEND=noninteractive 
ENV MONO_VERSION 5.20.1.19
RUN mkdir /build/
RUN apt-get update
# Install Ffmpeg youtube-dl etc.
RUN apt install curl unzip gnupg ca-certificates libopus-dev ffmpeg -y
RUN curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl && chmod a+rx /usr/local/bin/youtube-dl
# Install MONO
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
RUN echo "deb https://download.mono-project.com/repo/ubuntu stable-bionic main" | tee /etc/apt/sources.list.d/mono-official-stable.list
RUN apt-get update
RUN apt-get install ca-certificates-mono mono-devel mono-complete -y
# Download Bot
RUN curl -L https://github.com/Splamy/TS3AudioBot/releases/download/0.9.0/TS3AudioBot.zip -o /build/bot.zip
RUN mkdir /opt/bot/
RUN unzip /build/bot.zip -d /opt/bot/
RUN rm -r /build/
RUN mono --version
WORKDIR /app/
VOLUME /app/
CMD ["mono","/opt/bot/TS3AudioBot.exe"]
