## 💻 Atividade 1 - Projeto Integrador Transdisciplinar em Ciência de Dados

### Este arquivo tem o objetivo de demonstrar os scripts e constraints necessários para realizar a atividade da UNIDADE I do Projeto Integrador Transdisciplinar em Ciência de Dados

Demonstrações a seguir nos scripts:

- Criação da tabela TB_PAIS
- Criação da tabela TB_CIRCUITO
- Criação da tabela TB_PROVA
- Criação da tabela TB_EQUIPE
- Criação da tabela TB_PILOTO
- Criação da tabela TB_RESULTADO
- Criação da tabela TB_PAIS

<br/>

### Tabela TB_PAIS

```sh
CREATE TABLE TB_PAIS (
   ID_PAIS INT PRIMARY KEY,
   NM_PAIS VARCHAR(100) NOT NULL,
   NR_POPULACAO BIGINT
);
```

### Tabela TB_CIRCUITO

<br/>

```sh
CREATE TABLE TB_CIRCUITO (
    ID_CIRCUITO INT PRIMARY KEY,
    NM_CIRCUITO VARCHAR(100) NOT NULL,
    NR_EXTENSAO DECIMAL(10, 2),
    ID_PAIS INT,
    FOREIGN KEY (ID_PAIS) REFERENCES TB_PAIS(ID_PAIS)
);
```

### Tabela TB_PROVA

<br/>

```sh
CREATE TABLE TB_PROVA (
    ID_PROVA INT PRIMARY KEY,
    DT_PROVA DATE NOT NULL,
    NM_SITUACAO VARCHAR(50),
    ID_CIRCUITO INT,
    FOREIGN KEY (ID_CIRCUITO) REFERENCES TB_CIRCUITO(ID_CIRCUITO)
);
```

### Tabela TB_EQUIPE

<br/>

```sh
CREATE TABLE TB_EQUIPE (
    ID_EQUIPE INT PRIMARY KEY,
    NM_EQUIPE VARCHAR(100) NOT NULL,
    ID_PAIS INT,
    FOREIGN KEY (ID_PAIS) REFERENCES TB_PAIS(ID_PAIS)
);
```

### Tabela TB_PILOTO

<br/>

```sh
CREATE TABLE TB_PILOTO (
    ID_PILOTO INT PRIMARY KEY,
    NM_PILOTO VARCHAR(100) NOT NULL,
    DT_NASCIMENTO DATE,
    ID_PAIS INT,
    ID_EQUIPE INT,
    FOREIGN KEY (ID_PAIS) REFERENCES TB_PAIS(ID_PAIS),
    FOREIGN KEY (ID_EQUIPE) REFERENCES TB_EQUIPE(ID_EQUIPE)
);
```

### Tabela TB_RESULTADO

<br/>

```sh
CREATE TABLE TB_RESULTADO (
    ID_PROVA INT,
    ID_PILOTO INT,
    NR_TEMPO_PROVA DECIMAL(10, 2),
    NR_COLOC_FINAL INT,
    NR_POSICAO_GRID INT,
    NR_MELHOR_VOLTA DECIMAL(10, 2),
    PRIMARY KEY (ID_PROVA, ID_PILOTO),
    FOREIGN KEY (ID_PROVA) REFERENCES TB_PROVA(ID_PROVA),
    FOREIGN KEY (ID_PILOTO) REFERENCES TB_PILOTO(ID_PILOTO)
);
```
