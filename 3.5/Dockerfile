FROM resin/rpi-raspbian:jessie

ENV RELEASE=3.5.2
ENV PYTHON_PIP_VERSION=9.0.1
ENV ARCH=arm

# remove resin repo
RUN rm /etc/apt/sources.list.d/resin.list && \
    apt-key del 92BF1079

# install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
	build-essential \
        libbz2-dev \
        liblzma-dev \
        libsqlite3-dev \
        libncurses5-dev \
        libgdbm-dev \
        zlib1g-dev \
        libreadline-dev \
        libssl-dev \
        tk-dev \
        wget

# download and build Python
RUN mkdir python3

RUN cd python3 && \
    wget https://www.python.org/ftp/python/$RELEASE/Python-$RELEASE.tar.xz && \
    tar xvf Python-$RELEASE.tar.xz && \
    cd Python-$RELEASE

RUN cd python3/Python-$RELEASE && \
    ./configure && \
    make && \
    make install && \
    cd / && \
    rm -rf python3

RUN pip3 install --no-cache-dir --upgrade --force-reinstall "pip==$PYTHON_PIP_VERSION"

# cleanup
RUN rm -rf ~/.cache/pip && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["python3"]
