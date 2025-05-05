# DMP Tool MUG

## Workflow Diagram

For a detailed view of our workflow process involving the collaboration between TU Graz and the Medical University of Graz, please refer to the diagram located in the `Process-flow-dmp.pdf`.

## DAMAP Services Overview

| **Service**       | **Description**                                                                 | **Port**        | **Docker Image**                             | **Connected To**                                               | **Notes**                                                                                  |
|-------------------|----------------------------------------------------------------------------------|------------------|-----------------------------------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| **Damap Frontend**| Angular UI served via Nginx                                                      | `8000`           | Custom (Nginx + Angular)                      | Backend (`8080`), FITS (`8080`), Gotenberg (`3000`)             | No HTTPS, static UI files                                                                  |
| **Damap Backend** | Quarkus-based backend logic                                                      | `8080` (default) | Custom Quarkus image                          | Frontend, PostgreSQL, Keycloak                                 | Supports env vars for config                                                               |
| **FITS Service**  | Metadata extraction via Islandora FITS                                           | `8080`           | [Islandora FITS](https://github.com/Islandora/islandora_fits) | Frontend                                                        | Third-party tool used for file metadata                                                    |
| **Gotenberg**     | Document to PDF conversion and preview                                           | `3000`           | [Gotenberg](https://gotenberg.dev/)           | Frontend                                                        | Enables document previews                                                                  |
| **Keycloak**      | Identity and access management                                                   | *env override*   | Official Keycloak image                       | Backend, Frontend                                               | Used for authentication                                                                    |
| **PostgreSQL**    | Relational database for DAMAP                                                    | *env override*   | Official PostgreSQL image                     | Backend                                                         | Stores persistent data                                                                     |

## 🐞 Debugging DAMAP Services

When encountering issues in the DAMAP application—whether UI errors in the browser or backend errors—follow this guide to identify and resolve the problem.

---

### 🔧 General Tips
- Use `docker ps` to list running containers and get their names or IDs.
- Use `docker logs -f <CONTAINER_NAME>` to stream logs from a running container.
- Reference: [Docker Logs CLI Documentation](https://docs.docker.com/reference/cli/docker/container/logs/)

---

### ⚠️ Common Debugging Scenarios

| **Scenario**                              | **Where to Check**                                                                                          | **Command / Action**                                                             |
|-------------------------------------------|--------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| `500 Internal Server Error` or backend issues | Backend container logs                                                                                        | `docker logs -f <BACKEND_CONTAINER_NAME>`                                       |
| UI issues (`404`, static file errors, port routing) | Frontend container logs                                                                                       | `docker logs -f <FRONTEND_CONTAINER_NAME>`                                      |
| No logs in backend or frontend            | Check third-party services: **FITS**, **Gotenberg**                                                           | `docker logs -f <FITS_CONTAINER_NAME>`<br>`docker logs -f <GOTENBERG_CONTAINER_NAME>` |
| Login/signup errors or permission issues  | Inspect **Keycloak** configuration and logs                                                                  | `docker logs -f <KEYCLOAK_CONTAINER_NAME>`<br>Check client roles and users in Keycloak |
| Database connection issues                | PostgreSQL logs and connection string in backend environment variables                                       | `docker logs -f <POSTGRES_CONTAINER_NAME>`                                      |

---

### ✅ Checklist

- Are all containers running? (`docker ps`)
- Are there any error logs in the relevant service?
- Are port mappings and service URLs correct?
- Is Keycloak correctly configured for authentication?
- Are the required roles and users defined in Keycloak?
- Is the database accessible from the backend?

## Run a demo instance
This demo instance is configured with a keycloak username `user` & password `user`.

```bash
# make sure you have docker & docker-compose installed
docker compose -f docker/docker-compose.demo.yml up
```

**visit** [http://localhost:8000](http://localhost:8000)   


