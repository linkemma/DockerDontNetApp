FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR webapp

EXPOSE 80
EXPOSE 5024

#Copio los archivos de proyecto
COPY ./*.csproj ./
RUN dotnet restore

#Copia El restante
COPY . .
RUN dotnet publish -c Release -o out

#Build:Contruir la imagen
FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /webapp
COPY --from=build /webapp/out .
ENTRYPOINT ["dotnet","DockerDotNetApp.dll"]