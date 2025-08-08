# Nucleus Deployment
Runs the entire nucleus stack (frontend, backend as well as database) in a Docker environment

## Installation
1. Clone the repository:
   ```bash
   git clone https://gitlab.fhnw.ch/iit-projektschiene/fs25/25fs_iit44-interface-and-data-management-of-accidents-in-npp-simulations/nucleus-deployment.git
   ```
2. Navigate to the project directory:
   ```bash
   cd nucleus-deployment
   ```

## How to run

## Prerequisites
You need to have [Docker](https://docs.docker.com/get-started/get-docker/) installed.

### Persistent volume
There should already be a directory `.mongo-local-data` that serves as the database persistency, if not then create it in the root of the project directory.

### Data directory
There must be a directory containing all the simulation data you want to store in the database.
This folder MUST be referenced in the compose file under:

```yaml
services:
  ...
  backend:
    ...
    volumes:
      - /PATH/TO/THE/CALCULATION/DIRECTORY:/app/calculation # Replace everything before ':/app/calculation'
```

### Execute
Now simply run:

`$ docker compose up -d`

And navigate to http://localhost:3000 to see the application.
