# Docker Compose Examples

A full docker-compose file with mock services can be found at the [core package](https://github.com/tuwien-csd/damap-backend/blob/next/docker/docker-compose.yaml).

[`application.yaml`](https://github.com/sharedRDM/damap-backend/blob/main/src/main/resources/application.yaml) contains variables which can also be set via environment variables (i.e. `DAMAP_ORIGINS=https://dmp.medunigraz.at/`).
Most of the variables under the `DAMAP` section at the beginning have to be adapted at the deployment (e.g. database connection, keycloak connection).

## Docker Compose Minimal

The `docker-compose.mug.yml` file depicts an example of the services needed for deployment at MUG. It consists of:

- DAMAP back end
- DAMAP front end
- FITS service

### DAMAP back end

Service running the DAMAP back end adapted for MUG.

Environment Variables:

- DAMAP_BE_VERSION: Specify the version to be used for deployment

### DAMAP front end

Service running the DAMAP front end adapted for MUG.

Environment Variables:

- DAMAP_FE_VERSION: Specify the version to be used for deployment

### FITS instance

Service running a [FITS](https://projects.iq.harvard.edu/fits/home)
