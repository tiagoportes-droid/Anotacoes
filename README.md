# Anotações 

- `CREATE DATABASE if NOT EXIST {nome_banco}` Cria um bando de dados se ele não existir.
- `USE {nome_banco}` Obrigatorio ultilizar pois é ele qem gera acessoa ao Banco de Dados Escolhido.
- `CREATE TABLE {nome_tabela}` Cria um tabela onde pode ser insrido os valores como "id, nome, classe e etc".
- `DESC {nome_tabela}` Abre a janela no Heidi para facilitar a visualização.

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
DESC heroi
```

## Atalhos 

*Ctrl + F9*: Executa a linha seleciona no terminal do heidi