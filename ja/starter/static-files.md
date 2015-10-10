---
layout: page
title: Expressで静的ファイルを提供する
menu: starter
lang: ja
---

# Expressで静的ファイルを提供する

画像やCSS、JavaScriptといった静的ファイルを提供するには、Expressのビルトインミドルウェア`express.static`を用います。

静的アセットのディレクトリパスを`express.static`ミドルウェアに渡すと、ファイル提供を直接するようになります。
たとえば、あなたの画像やCSS、JavaScriptのファイルが`public`という名前のディレクトリに入っているなら、以下のように記述します。

~~~js
app.use(express.static('public'));
~~~

そうすると、`public`ディレクトリ以下のファイルをロードできるようになります。

~~~js
http://localhost:3000/images/kitten.jpg
http://localhost:3000/css/style.css
http://localhost:3000/js/app.js
http://localhost:3000/images/bg.png
http://localhost:3000/hello.html
~~~

<div class="doc-box doc-info">
ファイルは、静的ディレクトリから相対的に検索されます。そのため、ディレクトリの名前はURLの一部には含まれません。
</div>

もし、複数のディレクトリを静的アセットとして使いたいなら、`express.static`ミドルウェアを複数回呼ぶことができます。

~~~js
app.use(express.static('public'));
app.use(express.static('files'));
~~~

ファイルは`express.static`ミドルウェアにセットされた順序で静的ディレクトリから検索されます。

もし、`express.static`を使って仮想的なパスを作りたいなら、以下のように静的ディレクトリの[マウントパスを指定](/{{ page.lang }}/4x/api.html#app.use)することができます。

~~~js
app.use('/static', express.static('public'));
~~~

そうすると、"/static"パスから`public`ディレクトリ以下のファイルをロードできるようになります。

~~~js
http://localhost:3000/static/images/kitten.jpg
http://localhost:3000/static/css/style.css
http://localhost:3000/static/js/app.js
http://localhost:3000/static/images/bg.png
http://localhost:3000/static/hello.html
~~~
