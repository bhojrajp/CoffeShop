FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 8080

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["CoffeWeb.csproj", "./"]
RUN dotnet restore "CoffeWeb.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "CoffeWeb.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "CoffeWeb.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "CoffeWeb.dll"]
