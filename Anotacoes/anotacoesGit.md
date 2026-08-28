## Explicações dos Comandos Básicos

- **`git init`**: Inicializa um novo repositório Git na pasta atual.
- **`git clone {url}`**: Baixa um repositório existente do GitHub ou de outro servidor.
- **`git status`**: Mostra o estado atual dos arquivos do repositório.
- **`git add {arquivo}`**: Adiciona um arquivo para ser incluído no próximo commit.
- **`git add .`**: Adiciona todos os arquivos modificados para o próximo commit.
- **`git commit -m "{mensagem}"`**: Salva as alterações adicionadas com uma mensagem.
- **`git log`**: Mostra o histórico de commits do projeto.
- **`git diff`**: Mostra as alterações feitas nos arquivos antes do commit.
- **`git branch`**: Mostra as branches existentes.
- **`git branch {nome}`**: Cria uma nova branch.
- **`git switch {nome}`**: Troca para outra branch.
- **`git switch -c {nome}`**: Cria uma nova branch e já muda para ela.
- **`git merge {branch}`**: Junta as alterações de uma branch com a branch atual.
- **`git branch -d {nome}`**: Exclui uma branch local.
- **`git remote -v`**: Mostra os repositórios remotos conectados.
- **`git remote add origin {url}`**: Adiciona um repositório remoto chamado `origin`.
- **`git push`**: Envia os commits locais para o repositório remoto.
- **`git push -u origin {branch}`**: Envia a branch para o repositório remoto e configura a conexão padrão.
- **`git pull`**: Baixa as alterações do repositório remoto e tenta integrá-las ao projeto local.
- **`git fetch`**: Baixa informações do repositório remoto sem alterar os arquivos atuais.
- **`git restore {arquivo}`**: Desfaz alterações locais que ainda não foram adicionadas ao commit.
- **`git rm {arquivo}`**: Remove um arquivo e registra a remoção para o próximo commit.

## Exemplos

```bash
# 1. Criando um repositório
git init

# 2. Verificando o estado
git status

# 3. Adicionando um arquivo
git add index.html

# 4. Adicionando todos os arquivos
git add .

# 5. Criando um commit
git commit -m "Adiciona página inicial"

# 6. Visualizando o histórico
git log

# 7. Conectando com um repositório do GitHub
git remote add origin https://github.com/usuario/projeto.git

# 8. Enviando o projeto para o GitHub
git push -u origin main

# 9. Baixando alterações
git pull
```

#github #markdown 