# Etapa 1: build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copiamos archivos de proyecto y restauramos dependencias
COPY *.sln .
COPY PortalProveedores.API/*.csproj PortalProveedores.API/
RUN dotnet restore

# Copiamos todo el código y construimos
COPY . .
WORKDIR /src/PortalProveedores.API
RUN dotnet build -c Release -o /app/build
RUN dotnet publish -c Release -o /app/publish

# Etapa 2: runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 5000
ENTRYPOINT ["dotnet", "PortalProveedores.API.dll"]
