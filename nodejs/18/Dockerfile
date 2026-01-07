FROM        node:18-bookworm-slim

RUN		    apt-get update && apt-get install -y --no-install-recommends \
	        build-essential \
	        ca-certificates \
	        curl \
	        dnsutils \
	        ffmpeg \
	        git \
	        iproute2 \
	        iputils-ping \
	        libnss3 \
	        libsqlite3-dev \
	        libtool \
	        python3 \
	        python3-dev \
	        sqlite3 \
	        tar \
	        tini \
	        tzdata \
	        zip \
	        && rm -rf /var/lib/apt/lists/*

RUN       	npm install --global npm@9.8.1 typescript ts-node @types/node

ENV         USER=container
ENV			HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL	SIGINT

COPY        --chown=root:root --chmod=755 ./../entrypoint.sh /entrypoint.sh
ENTRYPOINT	["/usr/bin/tini", "-g", "--"]
CMD			["/entrypoint.sh"]
