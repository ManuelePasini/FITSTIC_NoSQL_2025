# Guide to Cassandra Setup

***With Docker Desktop running***

### Deploy Cassandra

- Open {FITSTIC_FOLDER}/code/docker-compose.yml and comment each service except Cassandra
- Open a bash terminal

```bash
// Navigate into docker-compose.yml folder
cd {FITSTIC_FOLDER}/code

// Run cassandra container
docker compose up
```

### Connect to Cassandra DBMS

- Open a second bash terminal

```bash
docker ps

// Now copy {CONTAINER_ID} from the output of the above cmd

// Connect to Cassandra container
docker exec -it {CONTAINER_ID} bash

// Open Cassandra bash
cqlsh
```