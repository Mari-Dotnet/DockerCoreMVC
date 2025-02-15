FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app
COPY *.sln .
COPY Testcoremvc/Testcoremvc.csproj ./Testcoremvc/
RUN dotnet restore

COPY Testcoremvc/. ./Testcoremvc/
RUN dotnet publish -c Release -o out

RUN ls -lR /app

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app/Testcoremvc
COPY --from=build app/out ./  
ENTRYPOINT ["dotnet", "Testcoremvc.dll"]

# Docker command
#docker build -t testcoremvc .
#docker run -d -p 8080:8080 --name testcoremvcinstance testcoremvc