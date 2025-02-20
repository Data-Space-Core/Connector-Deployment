# DSIL Connector Setup and Deployment Using Docker

## Overview
This documentation provides instructions on setting up and running a TRUST level 2 third-party certified IDSA-compliant DSILC (Data Space Innovation Lab Connector) using Docker. The setup includes a PostgreSQL database and a DSIL Connector.

## Prerequisites
Before proceeding, ensure you have the following installed on your system:

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Configuration
The DSIL Connector is configured using a JSON configuration file (`config.json`). This file defines the logging level, deployment mode, security profiles, public key, endpoints, and connector metadata. It also specifies the trust store and key store locations.

### Configuration Highlights
- **Logging Level:** Minimal Logging
- **Deployment Mode:** Test Deployment
- **Security Profile:** Base Security Profile
- **Connector Status:** Online
- **Database:** PostgreSQL 13
- **Keystore and Truststore:** Used for securing the connector

## Services
This setup includes the following services defined in the `docker-compose.yml` file:

### 1. PostgreSQL Database
A PostgreSQL container is used to store connector-related data.

**Service Name:** `postgres`

### 2. DSIL Connector
The DSIL Connector is deployed as a container and connects to the PostgreSQL database.

**Service Name:** `connector`

## Running the DSIL Connector
Follow these steps to start the services using Docker Compose:

1. **Navigate to the project directory**
   ```
   cd /path/to/project
   ```
2. **Start the containers**
   ```
   docker compose up --build -d
   ```
3. **Verify running containers**
   ```
   docker ps
   ```
4. **Check logs if needed**
   ```
   docker compose logs -f <container-id>
   ```
5. **Access DSIL Connector application**
   ```
   https://localhost:8081/
   ```

## Stopping the Services
To stop and remove the running containers, run:
```sh
docker compose down -v
```

## Additional Notes
- Ensure the configuration file (`config.json`) is correctly mapped to the container.

