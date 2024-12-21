FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG PROJECT
WORKDIR /src

# Copy solution and project files
COPY ["src/${PROJECT}/${PROJECT}.csproj", "src/${PROJECT}/"]
COPY ["src/BloggingPlatform.Common/BloggingPlatform.Common.csproj", "src/BloggingPlatform.Common/"]
RUN dotnet restore "src/${PROJECT}/${PROJECT}.csproj"

# Copy everything else
COPY . .
WORKDIR "/src/src/${PROJECT}"
RUN dotnet build "${PROJECT}.csproj" -c Release -o /app/build

FROM build AS publish
ARG PROJECT
RUN dotnet publish "${PROJECT}.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "BloggingPlatform.API.dll"]