FROM ubuntu:18.04

ARG DOTNET_CORE_VERSION=3.1
ENV DOTNET_CORE_VERSION=$DOTNET_CORE_VERSION
ENV DOTNET_CLI_TELEMETRY_OPTOUT=1
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
    && apt-get install -y dialog apt-utils wget ca-certificates openjdk-8-jdk bash software-properties-common supervisor unzip socat net-tools vim \
    && wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb \
    && add-apt-repository universe \
    && apt-get install -y apt-transport-https \
    && apt-get update \
    && apt-get install -y dotnet-sdk-$DOTNET_CORE_VERSION \
    && apt-get autoremove -y --purge \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf packages-microsoft-prod.deb
