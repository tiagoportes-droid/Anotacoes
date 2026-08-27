## 🧱 Estrutura Básica

- `<!DOCTYPE html>` → Informa que o documento usa HTML5.
- `<html>` → Elemento principal da página.
- `<head>` → Contém informações da página que não aparecem diretamente.
- `<body>` → Contém o conteúdo que aparece na página.
- `<title>` → Define o título da aba do navegador.
- `<meta>` → Define informações sobre a página, como codificação e responsividade.

### Exemplo

~~~html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Página</title>
</head>
<body>

    <h1>Olá, mundo!</h1>

</body>
</html>
~~~

---

## 📝 Textos e Títulos

- `<h1>` → Título principal.
- `<h2>` até `<h6>` → Subtítulos.
- `<p>` → Parágrafo.
- `<strong>` → Dá importância ao texto, normalmente deixando em negrito.
- `<em>` → Dá ênfase ao texto, normalmente deixando em itálico.
- `<br>` → Quebra uma linha.
- `<hr>` → Cria uma linha horizontal.

### Exemplo

~~~html
<h1>Título Principal</h1>
<h2>Subtítulo</h2>

<p>Esse é um parágrafo.</p>

<p>
    Texto em <strong>negrito</strong>
    e texto em <em>itálico</em>.
</p>
~~~

---

## 🔗 Links

A tag `<a>` é usada para criar links.

- `href` → Define para onde o link vai.
- `target="_blank"` → Abre o link em uma nova aba.

~~~html
<a href="https://google.com">
    Google
</a>

<a href="https://github.com" target="_blank">
    GitHub
</a>
~~~

---

## 🖼️ Imagens

A tag `<img>` adiciona imagens na página.

- `src` → Caminho ou endereço da imagem.
- `alt` → Texto alternativo da imagem

#frontEnd #banco #estudos 