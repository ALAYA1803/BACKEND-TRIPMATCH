## Database Migrations

This project uses Entity Framework Core migrations. To add or update the
database schema locally run:

```bash
dotnet ef migrations add <MigrationName> -o Migrations
dotnet ef database update
```

The application automatically applies pending migrations at startup via
`Database.Migrate()`.
