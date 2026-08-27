# Anotações de Banco de Dados (SQL & HeidiSQL)

## Explicações dos Comandos DDL

- **`CREATE DATABASE IF NOT EXISTS {nome_banco}`**: Cria um banco de dados apenas se ele ainda não existir.
- **`USE {nome_banco}`**: Seleciona o banco de dados que receberá os próximos comandos.
- **`CREATE TABLE {nome_tabela}`**: Cria uma nova tabela onde serão inseridos e estruturados os dados.
- **`DESC {nome_tabela}`**: Exibe a estrutura da tabela, mostrando colunas, tipos de dados e chaves.
- **`ALTER TABLE {nome_tabela}`**: Permite alterar uma tabela que já existe.
- **`MODIFY COLUMN {coluna}`**: Altera o tipo ou as regras de uma coluna existente.
- **`ADD COLUMN {coluna} {tipo}`**: Adiciona uma nova coluna na tabela.
- **`AFTER {coluna}`**: Define que a nova coluna será adicionada depois de uma coluna específica.
- **`PRIMARY KEY`**: Define a chave primária que identifica cada registro de forma única.
- **`AUTO_INCREMENT`**: Faz o banco gerar automaticamente o próximo número para a chave primária.
- **`NOT NULL`**: Impede que uma coluna fique sem valor.
- **`DEFAULT`**: Define um valor padrão para uma coluna.
- **`FOREIGN KEY ({coluna})`**: Define uma chave estrangeira para criar um relacionamento entre tabelas.
- **`REFERENCES {tabela}({coluna})`**: Indica a tabela e a coluna que serão relacionadas.
- **`ON DELETE SET NULL`**: Ao excluir o registro relacionado, coloca `NULL` na chave estrangeira.
- **`ON DELETE CASCADE`**: Ao excluir o registro principal, exclui também os registros relacionados.
- **`ON UPDATE CASCADE`**: Ao alterar a chave do registro principal, atualiza automaticamente a chave estrangeira.
- **`CONSTRAINT`**: Define uma regra ou restrição e permite dar um nome para ela.

## Exemplos

    CREATE DATABASE IF NOT EXISTS reino;
    USE reino;

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

    ALTER TABLE guilda
        MODIFY COLUMN batismo VARCHAR(50) NOT NULL,
        MODIFY COLUMN especialidade VARCHAR(50) NOT NULL;

    ALTER TABLE heroi
        ADD COLUMN id_guilda INT AFTER id_heroi;

    ALTER TABLE heroi
        ADD CONSTRAINT fk_heroi_guilda
        FOREIGN KEY (id_guilda)
        REFERENCES guilda(id_guilda)
        ON DELETE SET NULL
        ON UPDATE CASCADE;

    CREATE TABLE completa (
        id_heroi INT,
        id_missao INT,
        data_conclusao DATE DEFAULT (CURRENT_DATE),

        CONSTRAINT pk_completar_heroi
            PRIMARY KEY (id_heroi, id_missao),

        CONSTRAINT fk_completar_heroi
            FOREIGN KEY (id_heroi)
            REFERENCES heroi(id_heroi)
            ON DELETE CASCADE
            ON UPDATE CASCADE,

        CONSTRAINT fk_completar_missao
            FOREIGN KEY (id_missao)
            REFERENCES missao(id_missao)
            ON DELETE CASCADE
            ON UPDATE CASCADE
    );

## Comandos DML

- **`INSERT INTO {tabela}`**: Insere novos registros em uma tabela.
- **`VALUES`**: Define os valores que serão inseridos.
- **`SELECT`**: Consulta dados de uma ou mais tabelas.
- **`UPDATE`**: Altera dados que já existem.
- **`DELETE`**: Exclui registros de uma tabela.
- **`WHERE`**: Define uma condição para filtrar, alterar ou excluir registros.
- **`ORDER BY`**: Organiza os resultados de uma consulta.
- **`ASC`**: Ordena de forma crescente.
- **`DESC`**: Ordena de forma decrescente.

## Exemplos de DML

    INSERT INTO heroi (nome, classe, nivel)
    VALUES ('Aragorn', 'Guerreiro', 10);

    SELECT *
    FROM heroi;

    SELECT nome, classe
    FROM heroi;

    SELECT *
    FROM heroi
    WHERE nivel >= 10;

    SELECT *
    FROM heroi
    ORDER BY nivel DESC;

    UPDATE heroi
    SET nivel = 15
    WHERE id_heroi = 1;

    DELETE FROM heroi
    WHERE id_heroi = 1;

## Operadores

- **`=`**: Igual a.
- **`!=`**: Diferente de.
- **`<>`**: Também significa diferente de.
- **`>`**: Maior que.
- **`<`**: Menor que.
- **`>=`**: Maior ou igual.
- **`<=`**: Menor ou igual.
- **`AND`**: Todas as condições precisam ser verdadeiras.
- **`OR`**: Pelo menos uma condição precisa ser verdadeira.
- **`LIKE`**: Procura um determinado padrão em um texto.
- **`IN`**: Verifica se um valor está dentro de uma lista.
- **`BETWEEN`**: Procura valores dentro de um intervalo.
- **`IS NULL`**: Verifica se um valor é nulo.

## Exemplos

    SELECT *
    FROM heroi
    WHERE nivel > 10;

    SELECT *
    FROM heroi
    WHERE classe = 'Mago' AND nivel >= 10;

    SELECT *
    FROM heroi
    WHERE classe = 'Mago' OR classe = 'Guerreiro';

    SELECT *
    FROM heroi
    WHERE nome LIKE 'A%';

    SELECT *
    FROM heroi
    WHERE nivel BETWEEN 10 AND 20;

    SELECT *
    FROM heroi
    WHERE classe IN ('Mago', 'Guerreiro');

## Funções de Agregação

- **`COUNT()`**: Conta a quantidade de registros.
- **`SUM()`**: Soma os valores de uma coluna.
- **`AVG()`**: Calcula a média dos valores.
- **`MAX()`**: Retorna o maior valor.
- **`MIN()`**: Retorna o menor valor.

## Exemplos

    SELECT COUNT(*) AS total_herois
    FROM heroi;

    SELECT AVG(nivel) AS nivel_medio
    FROM heroi;

    SELECT MAX(nivel) AS maior_nivel
    FROM heroi;

    SELECT MIN(nivel) AS menor_nivel
    FROM heroi;

    SELECT SUM(nivel) AS soma_niveis
    FROM heroi;

## Relacionamentos

- **`1:1`**: Um registro de uma tabela está relacionado a apenas um registro de outra tabela.
- **`1:N`**: Um registro pode estar relacionado a vários registros de outra tabela.
- **`N:N`**: Vários registros podem estar relacionados a vários registros de outra tabela.
- **`PRIMARY KEY`**: Identifica de forma única cada registro.
- **`FOREIGN KEY`**: Liga uma tabela a outra.
- **Tabela intermediária**: Normalmente utilizada para criar relacionamentos `N:N`.

## Exemplo de Relacionamento

    Guilda 1 ─────── N Herói

    Herói N ─────── N Missão
           \        /
            Completa

Uma guilda pode possuir vários heróis, mas cada herói pode pertencer a uma guilda.

Um herói pode completar várias missões e uma missão pode ser completada por vários heróis. Por isso, utilizamos a tabela intermediária `completa`.

## Atalhos

_Ctrl + F9_: Executa a linha selecionada no terminal do HeidiSQL.
