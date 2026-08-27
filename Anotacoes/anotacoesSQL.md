# Anotações de Banco de Dados (SQL & HeidiSQL)

## Explicações dos Comandos DDL

- **`CREATE DATABASE IF NOT EXISTS {nome_banco}`**: Cria um banco de dados apenas se ele ainda não existir.
- **`USE {nome_banco}`**: Seleciona o banco de dados que receberá os próximos comandos de consulta ou alteração.
- **`CREATE TABLE {nome_tabela}`**: Cria uma nova tabela onde serão inseridos e estruturados os dados (ex: id, nome, classe).
- **`DESC {nome_tabela}`**: Exibe a estrutura técnica da tabela (colunas, tipos de dados, chaves) para facilitar a visualização no HeidiSQL.
- **`ALTER TABLE {nome_tabela} MODIFY COLUMN {coluna_tabela}`**: Altera o tipo ou restrição de uma coluna existente.
- **`ADD COLUMN {coluna_tabela} {tipo} AFTER {coluna_existente}`**: Adiciona uma nova coluna logo após uma coluna específica.
- **`ALTER TABLE {tabela} ADD CONSTRAINT {nome_fk}`**: Cria uma regra para obrigar a inserção de dados válidos através de uma Chave Estrangeira.
- **`FOREIGN KEY ({coluna}) REFERENCES {tabela_pai}({coluna_pai})`**: Vincula uma coluna local à chave primária de outra tabela.
- **`ON DELETE SET NULL`**: Ao excluir o registro pai, o valor da chave estrangeira na tabela filha é definido como nulo.
- **`ON DELETE CASCADE`**: Ao excluir o registro pai, todos os registros filhos associados também são excluídos automaticamente.
- **`ON UPDATE CASCADE`**: Ao atualizar o identificador no registro pai, atualiza automaticamente a chave estrangeira na tabela filha.

## Exemplos

```sql
-- 1. Criação e seleção do Banco de Dados
CREATE DATABASE IF NOT EXISTS reino;
USE reino;

-- 2. Criação das tabelas principais
CREATE TABLE heroi (
    id_heroi INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50),
    classe VARCHAR(50),
    nivel INT
);

CREATE TABLE guilda (
    id_guilda INT PRIMARY KEY AUTO_INCREMENT,
    batismo VARCHAR(50),
    especialidade VARCHAR(50)
);

CREATE TABLE missao (
    id_missao INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(100),
    nivel INT,
    recompensa DECIMAL(7, 2)
);

-- 3. Alteração de tabelas (Adicionando NOT NULL e colunas)
ALTER TABLE guilda
    MODIFY COLUMN batismo VARCHAR(50) NOT NULL,
    MODIFY COLUMN especialidade VARCHAR(50) NOT NULL;

ALTER TABLE heroi
    MODIFY COLUMN nome VARCHAR(50) NOT NULL,
    MODIFY COLUMN classe VARCHAR(50) NOT NULL,
    MODIFY COLUMN nivel INT NOT NULL,
    ADD COLUMN id_guilda INT AFTER id_heroi;

-- 4. Adição da Relacionamento 1:N (Heroi -> Guilda)
ALTER TABLE heroi
    ADD CONSTRAINT fk_heroi_guilda
    FOREIGN KEY (id_guilda) REFERENCES guilda(id_guilda)
    ON DELETE SET NULL
    ON UPDATE CASCADE;

-- 5. Tabela Intermediária N:N (Heroi <-> Missao)
CREATE TABLE completa (
    id_heroi INT,
    id_missao INT,
    data_conclusao DATE DEFAULT (CURRENT_DATE),

    CONSTRAINT pk_completar_heroi PRIMARY KEY (id_heroi, id_missao),
    CONSTRAINT fk_completar_heroi FOREIGN KEY (id_heroi) REFERENCES heroi(id_heroi)
        ON DELETE CASCADE
        ON UPDATE CASCADE,
    CONSTRAINT fk_completar_missao FOREIGN KEY (id_missao) REFERENCES missao(id_missao)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);

-- Conferir estruturas
DESC heroi;
DESC guilda;
DESC missao;
DESC completa;

```

## Atalhos

_Ctrl + F9_: Executa a linha seleciona no terminal do HeidiSQL
