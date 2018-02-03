FROM ubuntu:14.04

RUN apt-get update && apt-get install -y curl sudo gendarme apt-transport-https

RUN curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg && \
    mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg && \
    sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF && \
    echo "deb http://download.mono-project.com/repo/ubuntu trusty main" | sudo tee /etc/apt/sources.list.d/mono-official.list && \
    apt-get update && \
    apt-get install -y mono-devel ca-certificates-mono nunit-console

#RUN mkdir /opt/nuget && \
#    curl https://dist.nuget.org/win-x86-commandline/v4.4.1/nuget.exe -o /opt/nuget/nuget.exe && \
#    NUGET_SCRIPT='#!/bin/sh\nmono /opt/nuget/nuget.exe "$@"' && \
#    echo $NUGET_SCRIPT > /usr/bin/nuget && \
#    chmod +x /usr/bin/nuget

RUN mkdir -p /opt/paket && cd /opt/paket && \
    curl -L https://github.com/fsprojects/Paket/releases/download/5.133.0/paket.exe -o "paket.exe"
    PAKET_SCRIPT='#!/bin/sh\nmono /opt/paket/paket.exe "$@"' && \
    echo $PAKET_SCRIPT > /usr/bin/paket && \
    chmod +x /usr/bin/paket
