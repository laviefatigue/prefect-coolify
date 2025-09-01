# Prefect.io Self-Hosted Setup for Coolify

This repository contains a robust, production-ready Prefect server setup optimized for Coolify deployment.

## Components Included

- **PostgreSQL 15**: Primary database for Prefect metadata
- **Redis 7**: Message broker and caching layer
- **Prefect Server**: Main API and web UI
- **Prefect Services**: Background services for scheduling and orchestration
- **Prefect Worker**: Process worker for executing flows

## Features

- ✅ Persistent data storage with Docker volumes
- ✅ Health checks for all services
- ✅ Automatic service dependencies and startup order
- ✅ Redis-based messaging for better performance
- ✅ Process worker for immediate flow execution
- ✅ Optimized for Coolify deployment (no port conflicts)

## Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Prefect UI    │    │  Prefect API     │    │  Prefect Worker │
│   (Port 4200)   │────│   Server         │────│  (Process Pool) │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                │
                                │
                       ┌─────────────────┐    ┌─────────────────┐
                       │   PostgreSQL    │    │     Redis       │
                       │   (Database)    │    │ (Messaging)     │
                       └─────────────────┘    └─────────────────┘
```

## Post-Deployment Steps

1. Find your assigned domain in the Coolify dashboard (Applications → Your Prefect App → Domains)
2. Access the Prefect UI at the Coolify-assigned URL
3. Create your first work pool (if needed)
4. Deploy your first flow
5. Monitor execution in the dashboard

## Environment Variables

Copy `.env.example` to `.env` and configure:

- `POSTGRES_PASSWORD`: Secure password for PostgreSQL

**Note**: Coolify automatically handles domain assignment - no manual URL configuration needed!

## Resource Requirements

**Minimum:**
- 2 CPU cores
- 4GB RAM
- 10GB storage

**Recommended:**
- 4 CPU cores
- 8GB RAM
- 20GB storage

## Security Notes

- Change the default PostgreSQL password
- Consider enabling authentication in production
- Set up proper backup procedures for your data