FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["app/Azure_Exam3.Server/Azure_Exam3.Server.csproj", "Azure_Exam3.Server/"]
RUN dotnet restore "Azure_Exam3.Server/Azure_Exam3.Server.csproj"
COPY . .
WORKDIR "/src/app/Azure_Exam3.Server"
RUN dotnet build "Azure_Exam3.Server.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Azure_Exam3.Server.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Azure_Exam3.Server.dll"]