FROM        node:24-trixie-slim

RUN		    apt-get update && apt-get install -y --no-install-recommends \
            apt-utils \
            build-essential \
            bash \
            ca-certificates \
            curl \
            dnsutils \
            ffmpeg \
            git \
            gnupg2 \
            iproute2 \
            iputils-ping \
            libnss3 \
            libsqlite3-dev \
            libtool \
            net-tools \
            python3 \
            python3-dev \
            apt-transport-https \
            sqlite3 \
            tar \
            tini \
	        tzdata \
            wget \
            xz-utils \
            zip \

RUN		    wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | gpg --dearmor -o /usr/share/keyrings/google-chrome-keyring.gpg \
            && echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/google-chrome-keyring.gpg] http://dl.google.com/linux/chrome/deb/ stable main' \
                > /etc/apt/sources.list.d/google-chrome.list \
            && apt-get update \
            && apt-get install -y --no-install-recommends \
                libasound2 \
                libatk-bridge2.0-0 \
                libatk1.0-0 \
                libatspi2.0-0 \
                libcairo2 \
                libcups2 \
                libdbus-1-3 \
                libdrm2 \
                libgbm1 \
                libglib2.0-0 \
                libgtk-3-0 \
                libnspr4 \
                libpango-1.0-0 \
                libx11-6 \
                libxcb1 \
                libxcomposite1 \
                libxdamage1 \
                libxext6 \
                libxfixes3 \
                libxkbcommon0 \
                libxrandr2 \
                google-chrome-stable \
            && rm -rf /var/lib/apt/lists/*

RUN       	npm install --global npm@latest typescript ts-node @types/node

ENV         USER=container
ENV			HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL	SIGINT

COPY        --chown=root:root --chmod=755 ./../entrypoint.sh /entrypoint.sh
ENTRYPOINT	["/usr/bin/tini", "-g", "--"]
CMD			["/entrypoint.sh"]
