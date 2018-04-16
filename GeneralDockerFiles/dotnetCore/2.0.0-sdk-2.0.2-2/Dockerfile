FROM ubuntu:14.04

RUN apt-get update \
    && apt-get upgrade -y\
		ca-certificates \
        libcurl3 \
        libgssapi-krb5-2 \
        libicu52 \
        liblttng-ust0 \
        libssl1.0.0 \
        libunwind8 \
		apt-transport-https \
		curl \
    && rm -rf /var/lib/apt/lists/*
	
	
# Install .NET Core
ENV DOTNET_VERSION 2.0.0
ENV DOTNET_DOWNLOAD_URL https://dotnetcli.blob.core.windows.net/dotnet/Runtime/$DOTNET_VERSION/dotnet-runtime-$DOTNET_VERSION-linux-x64.tar.gz
ENV DOTNET_DOWNLOAD_SHA 2D4A3F8CB275C6F98EC7BE36BEF93A3B4E51CC85C418B9F6A5EEF7C4E0DE53B36587AF5CE23A56BC6584B1DE9265C67C0C3136430E02F47F44F9CFE194219178

RUN curl -SL $DOTNET_DOWNLOAD_URL --output dotnet.tar.gz \
    && echo "$DOTNET_DOWNLOAD_SHA dotnet.tar.gz" | sha512sum -c - \
    && mkdir -p /usr/share/dotnet \
    && tar -zxf dotnet.tar.gz -C /usr/share/dotnet \
    && rm dotnet.tar.gz \
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet
	
# set up network
ENV ASPNETCORE_URLS http://+:5000
ENV ASPNETCORE_RUNTIMESTORE_DOWNLOAD_URL https://dist.asp.net/runtimestore/2.0.0/linux-x64/aspnetcore.runtimestore.tar.gz
ENV ASPNETCORE_PKG_VERSION 2.0.0

# set up the runtime store
RUN curl -o /tmp/runtimestore.tar.gz $ASPNETCORE_RUNTIMESTORE_DOWNLOAD_URL \
    && export DOTNET_HOME=$(dirname $(readlink $(which dotnet))) \
    && tar -x -C $DOTNET_HOME -f /tmp/runtimestore.tar.gz \
    && rm /tmp/runtimestore.tar.gz