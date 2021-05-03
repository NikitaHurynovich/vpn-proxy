Connection configuration
Build container using build.bat or command "docker build -t vpn ."
Configure .env file with your user id.

Run the connection using command, change path to env file to your location:
docker run -it --rm --privileged --env-file=.env -p 8888:8888 -p 8889:8889 vpn grep -qxF 'nameserver 127.0.0.11' /etc/resolv.conf || echo 'nameserver 127.0.0.11' >> /etc/resolv.conf \
    && apk del .build-deps wget \
    && rm -rf /var/cache/* \
    && rm -rf /root/.cache/*
