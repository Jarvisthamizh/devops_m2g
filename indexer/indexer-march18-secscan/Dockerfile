FROM tlv-docker.us.int.genesyslab.com:5000/microsoft/dotnet:2.0.0-sdk-2.0.2

ARG source
WORKDIR /indexer
COPY ${source:-/bin/release/PublishOutput} .
ENTRYPOINT ["dotnet", "Indexer.dll"]