FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS builder
WORKDIR /src

COPY *.sln ./
COPY Portfolio.Api/Portfolio.Api.csproj Portfolio.Api/
COPY Portfolio.CrossCutting.Exceptions/Portfolio.CrossCutting.Exceptions.csproj Portfolio.CrossCutting.Exceptions/
COPY Portfolio.Domain/Portfolio.Domain.csproj Portfolio.Domain/
COPY Portfolio.Infrastructure.Data.Query/Portfolio.Infrastructure.Data.Query.csproj Portfolio.Infrastructure.Data.Query/
COPY Portfolio.Infrastructure.Data.Service/Portfolio.Infrastructure.Data.Service.csproj Portfolio.Infrastructure.Data.Service/
RUN dotnet restore

COPY . .
RUN dotnet publish --output /app/ --configuration Release

FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
WORKDIR /app
COPY --from=builder /app .
CMD ["dotnet", "Portfolio.Api.dll"]
