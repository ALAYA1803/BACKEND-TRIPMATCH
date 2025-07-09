# TripMatch Backend

This repository contains the ASP.NET Core API for the TripMatch platform. The API exposes endpoints for handling travel experiences, bookings, users and other domain entities. It is structured as a single project located in `workstation-back-end` and targets **.NET 9**.

## Prerequisites

- [.NET SDK 9](https://dotnet.microsoft.com/en-us/download/dotnet/9.0)
- MySQL or compatible database server
- Entity Framework Core tools (`dotnet tool install --global dotnet-ef`)

## Environment variables

The application reads its configuration from `appsettings.json` but can also use environment variables (use double underscores `__` to represent colons in the variable name):

| Variable | Description |
| -------- | ----------- |
| `ConnectionStrings__DefaultConnection` | MySQL connection string. |
| `Jwt__Key` | Secret key for signing JWTs. |
| `Jwt__Issuer` | Token issuer identifier. |
| `Jwt__Audience` | Token audience identifier. |

These variables are required when deploying to a cloud provider like **Render**.

## Deployment guide

1. **Clone the repository**

   ```bash
   git clone <repo-url>
   cd BACKEND-TRIPMATCH
   ```

2. **Set up the database**

   Create a MySQL database and note the connection details. Update the `ConnectionStrings__DefaultConnection` environment variable with your database connection string. This is necessary both locally and on Render.

3. **Apply migrations**

   If you add or modify entity classes, create a migration and apply it:

   ```bash
   dotnet ef migrations add InitialCreate --project workstation-back-end
   dotnet ef database update --project workstation-back-end
   ```

   On Render, these commands can be executed in a [build command](https://render.com/docs/build-commands) so that migrations run automatically on each deploy.

4. **Configure JWT secrets on Render**

   In your Render service settings, add the following environment variables:

   - `Jwt__Key` – a strong secret used to sign tokens
   - `Jwt__Issuer` – e.g. `workstation_back_end`
   - `Jwt__Audience` – e.g. `workstation_back_end_users`
   - `ConnectionStrings__DefaultConnection` – your MySQL connection string

5. **Build and run**

   Locally, run the API with:

   ```bash
   dotnet run --project workstation-back-end
   ```

   When deployed on Render, the platform will build the project using the .NET SDK and start the application automatically.

The API serves Swagger documentation at `/swagger` which can be used to explore the available endpoints.
