---
layout: page
title: Servindo arquivos estáticos no Express
menu: starter
lang: pt-br
---

# Servindo arquivos estáticos no Express

Servir arquivos, como imagens, CSS, JavaScript e outros arquivos estáticos é realizado com a ajuda de um <i>middleware</i> embutido no Express - `express.static`.

Passe o nome do diretório, que será marcado como a localização dos arquivos estáticos, para que o <i>middleware</i> `express.static` comece a servir os arquivos diretamente. Por exemplo, se você deixa suas imagens, CSS e JavaScript em um diretório com o nome `public`, você pode fazer o seguinte:

~~~js
app.use(express.static('public'));
~~~

Agora, se você é capaz de carregar os arquivos que estão sob o diretório `public`:

~~~js
http://localhost:3000/images/kitten.jpg
http://localhost:3000/css/style.css
http://localhost:3000/js/app.js
http://localhost:3000/images/bg.png
http://localhost:3000/hello.html
~~~

<div class="doc-box doc-info">
Os arquivos são procurados em relação ao diretório estático, portanto, o nome do diretório estático não faz parte da URL.
</div>

Se você deseja múltiplos diretórios como diretórios de arquivos estáticos, você pode chamar o <i>middleware</i> `express.static` múltiplas vezes:

~~~js
app.use(express.static('public'));
app.use(express.static('files'));
~~~

Os arquivos será procurados na ordem em que os diretórios estáticos foram configurados usando o <i>middleware</i> `express.static`.

Se você deseja criar um prefixo "virtual" (desde que o caminho não exista no <i>file system</i>) de caminho para os arquivos servidos pelo `express.static`, você pode [especificar um caminho de montagem](/4x/api.html#app.use) para o diretório estático, conforme apresentado abaixo:

~~~js
app.use('/static', express.static('public'));
~~~

Agora, se você é capaz de carregar os arquivos que estão sob o diretório `public`, pelo prefixo de caminho "/static".

~~~js
http://localhost:3000/static/images/kitten.jpg
http://localhost:3000/static/css/style.css
http://localhost:3000/static/js/app.js
http://localhost:3000/static/images/bg.png
http://localhost:3000/static/hello.html
~~~
