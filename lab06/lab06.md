## Exercício 1

Faça a projeção em relação a Patologia, ou seja, conecte patologias que são tratadas pela mesma droga.

### Resolução

```cypher
MATCH (p1:Pathology)<-[a]-(d:Drug)-[b]->(p2:Pathology)
WHERE a.weight > 20 AND b.weight > 20
MERGE (p1)<-[s:Semelhante]->(p2)
ON CREATE SET s.weight=1
ON MATCH SET s.weight=s.weight+1


MATCH (p1:Pathology)<-[:Semelhante]->(p2:Pathology)
RETURN p1, p2
LIMIT 20
```

## Exercício 2

Construa um grafo ligando os medicamentos aos efeitos colaterais (com pesos associados) a partir dos registros das pessoas, ou seja, se uma pessoa usa um medicamento e ela teve um efeito colateral, o medicamento deve ser ligado ao efeito colateral.

### Resolução

```cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/santanche/lab2learn/master/data/faers-2017/sideeffect.csv' AS line
CREATE(:Efeito {code: line.codePathology, person: line.idPerson})

CREATE INDEX FOR (n:Efeito) ON (n.code)

LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/santanche/lab2learn/master/data/faers-2017/drug-use.csv' AS line
MATCH (d:Drug {code: line.codedrug})
MATCH (p:Pathology {code: line.codepathology})
CREATE (d)-[:Cura {person: line.idperson}]->(p)

MATCH (d:Drug)-[c:Cura]->(p:Pathology)
MATCH (e:Efeito)
WHERE (e.person) = c.person
MERGE (d)-[g:Gerou]->(e)
ON CREATE
    SET g.weight = 1
ON MATCH
    SET g.weight = g.weight + 1
```

## Exercício

Que tipo de análise interessante pode ser feita com esse grafo?

Proponha um tipo de análise e escreva uma sentença em Cypher que realize a análise.

### Resolução

```cypher
Podemos realizar uma projeção que conecta medicamentos que geraram o mesmo efeito colateral. Assim, podemos facilmente visualizar relações e associar princípios ativos semelhantes à certos efeitos colaterais.
A query que nos possibilita tal relação é a seguinte:
MATCH (d1:Drug)-[x]->(e:Efeito)<-[y]-(d2:Drug)
WHERE x.weight > 3 AND y.weight > 3
MERGE (d1)<-[a:Analogo]->(d2)
ON CREATE
    SET a.weight=1
ON MATCH
    SET a.weight=a.weight+1
```
