# for local platform
FROM --platform=$BUILDPLATFORM mcr.microsoft.com/dotnet/sdk:7.0 AS build
ARG TARGETARCH

WORKDIR /source
COPY *.csproj .
RUN dotnet restore -a $TARGETARCH

COPY . .
RUN dotnet publish -c Release -a $TARGETARCH --self-contained false --no-restore -o /app

# for app image
FROM mcr.microsoft.com/dotnet/runtime:7.0-alpine
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Worker.dll"]