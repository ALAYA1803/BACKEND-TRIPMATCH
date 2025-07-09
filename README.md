# Workstation Back-End

This project uses environment variables to configure the database connection string and JWT signing key. Sensitive values have been removed from the committed `appsettings.json` files.

## Configuration

A template configuration file is provided at `workstation-back-end/appsettings.Template.json`. Copy this file to `appsettings.json` (or `appsettings.Development.json`) and replace the placeholder values, or set the following environment variables:

- `ConnectionStrings__DefaultConnection`
- `Jwt__Key`

### Render deployment

When deploying to [Render](https://render.com), open your service, go to **Environment** and add the variables listed above. The application will read them at runtime.

