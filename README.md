# Nucleus Deployment

Runs the entire nucleus stack (frontend, backend as well as database) in a Docker environment

## How to run

## Prerequisites
You need to have [Docker](https://docs.docker.com/get-started/get-docker/) installed.

### Persistent volume
There should already be a directory `.mongo-local-data` that serves as the database persistency, if not then create it.
If you start freshly, make sure the directory is empty.

### Frontend & Backend directories
The frontend project as well as the backend project directories need to be at the same level as
the deployment directory:
```
nucleus/
├─ nucleus-frontend/
├─ nucleus-backend/
├─ nucleus-deployment/
```

### Data directory
There must be a directory containing all the simulation data you want to store in the database.
This folder MUST be referenced in the compose file under:

```yaml
services:
  ...
  init-db:
    ...
    volumes:
      - /PATH/TO/THE/CALCULATION/DIRECTORY:/app/calculation # Replace everything before ':/app/calculation'
```

### Execute
Now simply run:

`$ docker compose up -d`

And navigate to http://localhost:3000/dashboard to see the application.
