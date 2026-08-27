# Anotações

## Explicações

- `CREATE DATABASE if NOT EXIST {nome_banco}` Cria um bando de dados se ele não existir.
- `USE {nome_banco}` Obrigatorio ultilizar pois é ele qem gera acessoa ao Banco de Dados Escolhido.
- `CREATE TABLE {nome_tabela}` Cria um tabela onde pode ser insrido os valores como "id, nome, classe e etc".
- `DESC {nome_tabela}` Abre a janela no HeidiSQL para facilitar a visualização.
- `ALTER TABLE {nome_tabela} CHANGE COLUMNS {coluna_tabela}` Altera a coluna selecionada
- `ADD COLUMN {coluna_tabela} {valor} after {coluna_tabela}` Adiciona uma coluna apos o valor selecionado  
- `ALTER TABLE heroi ADD CONSTRAINT {fk_coluna_heroi}` 
- `FOREIGN KEY(fk_coluna_tabela) REFERENCES {nome_tabela}(fk_coluna_tabela)` Adiciona uma **Chave Estrangeira** com o nome selecionado em primeiro.
- `ON DELETE SET NULL` Ao deletar seta a coluna como nula.
- `ON UPDATE CASCADE` Ao atualiza seta como cascata. 

## Exemplos

```sql
CREATE DATABASE if NOT EXISTS reino;
USE reino;

CREATE TABLE heroi(
    id_heroi INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50),
    classe VARCHAR(50),
    nivel INT(9)
);
DESC heroi;

ALTER TABLE heroi 
    MODIFY COLUMN nome_heroi VARCHAR(100) NOT NULL,
    MODIFY COLUMN classe_heroi VARCHAR(100) NOT NUll;
DESC heroi;

ADD COLUMN id_guilda INT AFTER id_heroi;
```

## Atalhos

_Ctrl + F9_: Executa a linha seleciona no terminal do HeidiSQL
