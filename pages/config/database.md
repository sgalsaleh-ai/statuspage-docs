# Database Configuration

{{ app.name }} uses PostgreSQL for persistent storage. You can use the built-in embedded database or connect to your own.

## Embedded Database (default)

The embedded PostgreSQL is deployed automatically as part of the installation. No configuration needed — a secure password is auto-generated and persists across upgrades.

## External Database (BYO)

To use your own PostgreSQL instance:

1. In the config screen, select **Database Type → External**
2. Enter your connection details:
   - **Host**: Your PostgreSQL hostname
   - **Port**: Default `5432`
   - **Database Name**: The database to use
   - **Username**: Database user
   - **Password**: Database password
   - **SSL Mode**: Use `require` for cloud databases (Neon, RDS, etc.)

### Supported Providers

- Amazon RDS
- Google Cloud SQL
- Azure Database for PostgreSQL
- Neon
- Any PostgreSQL 14+ instance

### Requirements

- PostgreSQL 14 or later
- The database must be created before installation
- The user must have full permissions on the database
