FROM microsoft/aspnetcore:2.0
ARG source
WORKDIR /indexer
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", "Indexer.dll"]