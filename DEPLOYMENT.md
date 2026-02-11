# 🚢 Deploying Asamblor Command Center (Twenty CRM)

This repository contains the forked and branded version of Twenty CRM, now known as the **Asamblor Command Center**. Follow these steps to self-host it on your server.

## 📋 Prerequisites

- **Docker** and **Docker Compose** installed on your server.
- A domain name (e.g., `crm.asamblor.com`) pointing to your server's IP.
- At least 4GB of RAM recommended for a smooth experience.

## 🚀 Quick Start (Production)

1. **Clone your fork on your server**:
   ```bash
   git clone https://github.com/bodiseey/twenty.git
   cd twenty/deploy
   ```

2. **Configure Environment Variables**:
   Copy the example environment file and edit it:
   ```bash
   cp .env.example .env
   nano .env
   ```
   - Update `SERVER_URL` to your production domain.
   - Generate a strong `APP_SECRET` (e.g., `openssl rand -base64 32`).
   - Set strong passwords for `PG_DATABASE_PASSWORD`.

3. **Build and Launch**:
   Run the following command to build the branded images from source and start the containers:
   ```bash
   docker compose up -d --build
   ```

4. **Verify**:
   Wait a few minutes for migrations to run. You can check logs with:
   ```bash
   docker compose logs -f server
   ```
   Access your CRM at your `SERVER_URL`.

## 🎨 Branding Customizations

This fork has already been customized with:
- **Asamblor Emerald Theme**: Accent colors changed across the app.
- **Logos**: Asamblor logo injected into auth and sidebar views.
- **Terminology**: White-labeled to "Asamblor Command Center".

## 🛠️ Maintenance

- **Update Code**: `git pull origin main` followed by `docker compose up -d --build`.
- **Backup Database**: Use `docker exec` to run `pg_dump` on the `db` container.
