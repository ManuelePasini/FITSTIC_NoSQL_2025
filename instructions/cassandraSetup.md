# Guide to Cassandra Setup

***With Docker Desktop running***

### Deploy Cassandra

- Open {FITSTIC_FOLDER}/code/docker-compose.yml  through some IDE (e.g., Visual Studio Code, Visual Studio) and comment each service except Cassandra (by selecting and then commenting the whole block via CTRL + ù )
```yaml
  # neo4j:
  #   image: neo4j:5.2
  #   hostname: neo4j
  #   container_name: neo4j
  #   volumes:
  #     - ./neo4j/data:/datasets
  #   expose:
  #     - 7687
  #     - 7474
  #   ports:
  #     - "7687:7687"
  #     - "7474:7474"
  #   networks:
  #     - default
  #   environment:
  #     - NEO4J_AUTH=neo4j/fitstic
  #     - NEO4J_ACCEPT_LICENSE_AGREEMENT=yes

  cassandra:
    image: cassandra:4.1.4
    container_name: cassandra
    expose:
      - 9042
    ports:
      - "9042:9042"
    environment:
      - "MAX_HEAP_SIZE=256M"
      - "HEAP_NEWSIZE=128M"
    volumes:
      - ./cassandra/data:/root/labwork/
    restart: always
    healthcheck:
      test: [ "CMD", "cqlsh", "-u cassandra", "-p cassandra" , "-e describe keyspaces" ]
      interval: 15s
      timeout: 10s
      retries: 10
```

- Open a bash terminal by typing <b>cmd</b> in your OS search bar.
- Navigate into docker-compose.yml folder

```bash
cd {FITSTIC_FOLDER}/code
```

- Run Apache Cassandra container
```bash
docker compose up
```

### Connect to Cassandra DBMS

- Open a second bash terminal

- Connect to Cassandra container
```bash
docker exec -it cassandra bash
```

- Open Cassandra query language interface

```bash
cqlsh
```
- Now you can work with your data, e.g.

```bash
CREATE KEYSPACE killrvideo WITH REPLICATION = {'class': 'SimpleStrategy', 'replication_factor' : 1 };

USE killrvideo;
```