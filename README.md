# TripMatch Backend

This repository contains the ASP.NET Core backend for TripMatch.

## Deploying to Render

1. Sign in to [Render](https://render.com/) and create a **new Web Service**.
2. Connect your GitHub repository and select this project.
3. Choose **Docker** as the environment.
4. Leave the build command empty (Render will build using the `Dockerfile`).
5. The service will start automatically using the command specified in the `Dockerfile`.
6. Expose port **8080** and click **Create Web Service**.

Once deployment completes, your API will be available at the Render-provided URL.

## Local development

You can run the project locally using the .NET SDK:

```bash
# Restore dependencies
 dotnet restore workstation-back-end/workstation-back-end.csproj
# Run the app
 dotnet run --project workstation-back-end/workstation-back-end.csproj
```

## Directory structure

- `workstation-back-end/` – ASP.NET Core source code
- `Dockerfile` – build and runtime instructions for Render
