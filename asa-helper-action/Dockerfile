# Use the official Microsoft .NET 8 SDK image as the build environment
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /app

# Copy everything and build the application
COPY . ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

# Use the official Microsoft .NET 8 runtime image for the final image
FROM mcr.microsoft.com/dotnet/runtime:8.0
WORKDIR /app
COPY --from=build-env /app/out .

# Set the entry point of the container to run your application
# ENTRYPOINT ["dotnet", "YourConsoleApp.dll"]
ENTRYPOINT [ "/app/asa-helper-action" ]
