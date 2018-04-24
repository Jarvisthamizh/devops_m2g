FROM tlv-docker.us.int.genesyslab.com:5000/microsoft/dotnet:2.0.0-sdk-2.0.2
ARG W:\Aviv Kabesa\Indexer\
WORKDIR /indexer
COPY ${W:\Aviv Kabesa\Indexer\:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", "Indexer.dll"]