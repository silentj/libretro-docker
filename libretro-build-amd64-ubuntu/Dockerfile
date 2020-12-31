FROM ubuntu:bionic

ARG uid
ARG branch=master
ENV branch=$branch

RUN apt-get update && \
    apt-get install -y unzip && \
    useradd -d /developer -m developer && \
    chown -R developer:developer /developer

RUN apt-get upgrade -y \
	&& apt-get install -y \
		build-essential \
		bash \
		bc \
		bzip2 \
		diffutils \
		g++ \
		gawk \
		gcc \
		git-core \
		gperf \
		gzip \
		libjson-perl \
		libncurses5-dev \
		lzop \
		make \
		patch \
		patchutils \
		perl \
		sed \
		tar \
		texinfo \
		unzip \
		wget \
		xfonts-utils \
		xsltproc \
		xz-utils \
		zip \
		libssl-dev \
		u-boot-tools \
		sudo \
		libglib2.0-dev \
		doxygen \
		bsdmainutils \
		swig \
		curl \
		libx11-dev \
		mesa-common-dev \
		libglu1-mesa-dev \
		libasound2 \
		xxd \
		meson \
		ninja-build \
		nasm \
		python2.7 \
		python-pip \
		python3 \
		python3-pip \
		p7zip-full \
		g++-mingw-w64 \
		gcc-mingw-w64 \
		libz-mingw-w64 \
		mingw-w64-tools \
		cmake \
		libass-dev \
		libpcap-dev \
		imagemagick \
		optipng \
		rsync \
	&& rm -rf /var/lib/apt/lists/*

RUN echo "###### Ubuntu Main Repos" > /etc/apt/sources.list && \
	echo "deb http://de.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb-src http://de.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo  >> /etc/apt/sources.list && \
	echo "###### Ubuntu Update Repos" >> /etc/apt/sources.list && \
	echo "deb http://de.archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb http://de.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb http://de.archive.ubuntu.com/ubuntu/ bionic-proposed main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb http://de.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-proposed main restricted universe multiverse " >> /etc/apt/sources.list && \
	echo "deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse " >> /etc/apt/sources.list

RUN apt-get update && apt-get build-dep -y retroarch && rm -rf /var/lib/apt/lists/*

RUN echo "1"| sudo update-alternatives --config x86_64-w64-mingw32-gcc
RUN echo "1"| sudo update-alternatives --config x86_64-w64-mingw32-g++

RUN echo "developer:developer" | chpasswd && adduser developer sudo

ENV HOME=/developer

USER root
WORKDIR /developer
VOLUME /developer

CMD /bin/bash
