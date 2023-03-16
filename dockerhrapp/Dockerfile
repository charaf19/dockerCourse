#first stage base image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /source
#copy cs project and restore dependenies
COPY *.csproj .
RUN dotnet restore
#copy and publish the application files
COPY . .
RUN dotnet publish -c release -o /app
#final stage 
FROM mcr.microsoft.com/dotnet/aspnet:6.0 
WORKDIR /app
COPY --from=build /app/ . 
#what is the first command that the container will run when it starts 
ENTRYPOINT [ "dotnet","hrapp.dll"]


