# Neo4j - Soluzioni

Manuale Cypher https://neo4j.com/docs/cypher-manual/current/ 

## Movie graph

### Pattern semplici

1. Restituire tutti i nodi e le relazioni nel database

    ```
    MATCH (n) RETURN n
    ```

2. Contare i nodi e gli archi presenti

    ```
    MATCH (n) WITH COUNT(n) AS numVertices
    MATCH (a)-[e]->(b)
    RETURN numVertices, COUNT(e) AS numEdges
    ```

3. Dato il film The Departed (https://www.imdb.com/title/tt0407887/?ref_=fn_al_tt_1) inserire i seguenti nodi ed i seguenti archi (ATTENZIONE: eseguire il codice in un unico blocco! Altrimenti, le istruzioni per creare gli archi devono essere precedute da un MATCH per recuperare i rispettivi nodi coinvolti). Cosa fa il seguente codice?

    ```
    CREATE (departed:Movie {title:'The Departed', released:2006, tagline:'Il bene e il male'})
    CREATE (leo:Person {name:'Leonardo Di Caprio', born: 1974})
    CREATE (matt:Person {name:'Matt Damon', born: 1970})
    CREATE (leo)-[:ACTED_IN {roles: ['Billy']}]->(departed)
    CREATE (matt)-[:ACTED_IN {roles: ['Colin Sullivan']}]->(departed);

    MATCH (jack:Person {name: 'Jack Nicholson'})
    MATCH (departed:Movie {title:'The Departed'})
    CREATE (jack)-[:ACTED_IN {roles: ['Frank Costello']}]->(departed)
    ```

Il codice crea:
- L'istanza del film (proprietà: title, released)
- 3 attori principali (proprietà: name, born) 
- Le rispettive relazioni ACTED_IN (proprietà: role)

4. Restituire il film The Departed e tutti i nodi ad esso collegati

    ```
    MATCH (n:Movie {title:'The Departed'})<--(m) RETURN n, m
    ```

5. Restituire tutte le 134 persone collegate ad un film

    ```
    MATCH (n:Person)-->(:Movie) RETURN n
    ```

6. Restituire i 104 attori, ossia persone che hanno recitato (ACTED_IN) in un film

    ```
    MATCH (n:Person)-[:ACTED_IN]->(:Movie) RETURN n
    ```

7. Restituire i 5 attori che sono anche direttori, ossia hanno diretto (DIRECTED) un film (:Movie)

    ```
    MATCH (n:Person)-[:ACTED_IN]->(:Movie),(n:Person)-[:DIRECTED]->(:Movie) RETURN n


    MATCH (n:Person)-[:ACTED_IN]->(:Movie)
    MATCH (n:Person)-[:DIRECTED]->(:Movie)
    RETURN n
    ```

8. Restituire i 3 attori che hanno anche diretto un film in cui hanno recitato (ACTED_IN); restituire anche il relativo film

    ```
    MATCH (n:Person)-[:ACTED_IN]->(m:Movie),(n:Person)-[:DIRECTED]->(m:Movie) RETURN n, m
    ```