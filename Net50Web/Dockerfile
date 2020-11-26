FROM mcr.microsoft.com/dotnet/sdk AS build
WORKDIR /app
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish Net50Web.csproj -c Release -o out

FROM mcr.microsoft.com/dotnet/runtime AS base
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS="http://*:1923" 
ENTRYPOINT ["dotnet", "Net50Web.dll"]
