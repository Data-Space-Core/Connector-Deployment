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
This setup includes the following services defined in the `docker compose.yml` file:

### 1. PostgreSQL Database
A PostgreSQL container is used to store connector-related data.

**Service Name:** `postgres`

### 2. DSIL Connector
The DSIL Connector is deployed as a container and connects to the PostgreSQL database.

**Service Name:** `connector`

## Running the DSIL Connector
Follow these steps to start the services using Docker Compose:

1. **Clone the repository**
   ```
   git clone https://github.com/Data-Space-Core/Connector-Deployment.git
   ```
   
2. **Navigate to the project directory**
   ```
   cd Connector-Deployment
   ```
3. **Start the containers**
   ```
   docker compose up --build -d
   ```
4. **Verify that "connector" and "postgres" containers are running**
   ```
   docker ps
   ```
5. **Check logs if needed**
   ```
   docker compose logs -f connector
   ```
6. **Verify DSIL Connector is running**
   ```
   opening this URL https://localhost:8081/ in Chrome will render the following
   {
  "@context": {
    "ids": "https://w3id.org/idsa/core/",
    "idsc": "https://w3id.org/idsa/code/"
  },
  "@type": "ids:BaseConnector",
  "@id": "https://connector",
  "ids:version": "8.0.2",
  "ids:description": [
    {
      "@value": "DSIL Connector built by VTT",
      "@type": "http://www.w3.org/2001/XMLSchema#string"
    }
  ],
  "ids:publicKey": {
    "@type": "ids:PublicKey",
    "@id": "https://w3id.org/idsa/autogen/publicKey/78eb73a3-3a2a-4626-a0ff-631ab50a00f9",
    "ids:keyType": {
      "@id": "https://w3id.org/idsa/code/RSA"
    },
    "ids:keyValue": "TUlJQklqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FROEFNSUlCQ2dLQ0FRRUF1dzZtRnJkZmxYWlRKZ0ZPQTVzbURYQzA5U21wSldvR3B5RVJaTkV5MzFwS2RzUkdoVGlwUjI3ajlpcm1tcWlodjdnSWd6Q254NmtJUk5HSTJ1MG9GUTVGZ3ZPMXh4Z3pjaWhkcEYwQ2hlT2Y5SU5naXNQa3E1aGo4QWUvRFlYa3ZqaFE2YzZhay9aWWZqME5wcXlFUGNKNU1MUm1ZR2V4TWFNWm1UYnFESnZKbDVKRzMrYkUzWWEyMWhUWllPeGlTaWNwZkZnSjMwa241YVVJQXRkMDVJWnk3ejFzRGlWTHRUWGxMZmUvWlFDNHBuakZ0cyt0YzEyc1g5aWhJbW5Da2QwV3Z6M0NUWm95QlNzYzFUZEJrYjltMEM1dHZnMGZRUDRRZ0YvekgyUW9abm5ySTUydUFaOE1vbVd0WTJsdDNEMGtrcFI2OXBmVkRKN3kzdk4vZXdJREFRQUI="
  },
  "ids:title": [
    {
      "@value": "DSIL Connector",
      "@type": "http://www.w3.org/2001/XMLSchema#string"
    }
  ],
  "ids:hasDefaultEndpoint": {
    "@type": "ids:ConnectorEndpoint",
    "@id": "https://w3id.org/idsa/autogen/connectorEndpoint/e5e2ab04-633a-44b9-87d9-a097ae6da3cf",
    "ids:accessURL": {
      "@id": "https://connectorb:8081/api/ids/data"
    }
  },
  "ids:securityProfile": {
    "@id": "https://w3id.org/idsa/code/BASE_SECURITY_PROFILE"
  },
  "ids:maintainer": {
    "@id": "https://VTT.fi/"
  },
  "ids:curator": {
    "@id": "https://VTT.fi/"
  },
  "ids:inboundModelVersion": [
    "4.2.6",
    "4.2.7",
    "4.2.0",
    "4.1.2",
    "4.2.1",
    "4.0.0",
    "4.1.0",
    "4.2.4",
    "4.2.5",
    "4.2.2",
    "4.2.3"
  ],
  "ids:outboundModelVersion": "4.2.7"
}
   ```

Accessing this 
## Stopping the Services
To stop and remove the running containers, run:
```sh
docker compose down -v
```

## Additional Notes
- Ensure the configuration file (`config.json`) is correctly mapped to the container.

