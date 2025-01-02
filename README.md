<!-- SUBTITLE: The funkiest site on the Internet! -->

# Index file

This is **[BlaB! Pages](https://justblab.com/blab-pages)** and what you see is the default *content* file: [`blab-pages-content/index.md`](blab-pages-content/index.md) (*CTRL+U to view-source*). BlaB! Pages uses [Parsedown](https://parsedown.org/) to display markdown formatted content. Drop a bunch of **markdown** documents in `blab-pages-content`, set up a menu in [`blab-pages-content/menu.json`](./blab-pages-content/menu.json) and your website is ready to go! 

<!-- you can use HTML in case markdown is not enough -->
<p style="text-align:right"><a href="?markdown">What is markdown?</a></p>

---

## How to install

* [Download BlaB! Pages](https://justblab.com/blab-pages).
* Unzip and upload to your hosting space.

---

File/directory structure with the bare minimum of files for a working installation:


```

  📁 public_html ← (your website root directory)
  ├── 📁 blab-pages-content
  │   ├── 📄 index.md
  │   ├── 📄 404.md
  │   └── 📄 menu.json
  ├── 📁 blab-pages-parsedown
  │   └── 📄 parsedown.php
  ├── 📁 blab-pages-themes
  │   └── 📁 [THEME]
  │       └── 📄 template.html
  └── 📄 index.php


```

---

Dead simple JSON menu: [`blab-pages-content/menu.json`](./blab-pages-content/menu.json)

```

{
"?index"     : "BlaB! Pages",
"?markdown"  : "Markdown"
}


```

---

Any **`.md`** file from `blab-pages-content` can be displayed as a web page and you can link to it in the other markdown documents: `[text](?name-of-the-markdown-file-without-md-extension)`. 

A GET request `?page=name-of-the-md-file` returns the content of the .md file as HTML (*without template*).

* [`blab-pages-content/index.md`](blab-pages-content/index.md) is the default index page.
* [`blab-pages-content/404.md`](blab-pages-content/404.md) is a custom *error-404-file-not-found* page. 

The names of the .md files can only contain digits, dashes & letters including UTF-8 letters.

---

Optional `blab-pages-config.php` (*or change the config array in `index.php`  directly*)

```

<?php

$config=array();

$config['theme'] = '01-default'; // theme directory within /blab-pages-themes
$config['title'] = 'funky website'; // global title
$config['subti'] = 'The funkiest site on the internet!'; // fallback subtitle
$config['metad'] = 'Website dedicated to music!'; // META description
$config['metak'] = 'funk, jazz, samba'; // META keywords
$config['i6391'] = 'en'; // 2-letter language code
$config['b_url'] = 'chat/index.php'; // URL or relative path to BlabChat/index.php

?>


```

---

Optional subtitle can be set in the markdown document as an HTML comment: 

<pre><code>
&lt;!-- SUBTITLE: This is the funkiest site on the Internet!  --&gt;

</code></pre>

---

A theme only requires a `template.html` file in `blab-pages-themes/[THEME]/` and here is the default template file: [`blab-pages-themes/01-default/template.html`](blab-pages-themes/01-default/template.html) (*CTRL+U to view-source*). How to load located in the [THEME] folder images, CSS & JavaScript in `template.html`? No problem at all:


<pre><code>&lt;img src="blab-pages-themes/&#123;{THEME}}/image.jpg" /&gt;</code></pre>


---

The following variables are dynamically replaced in `template.html` when loading the page:

| Syntax               | Description                                      |
| -------------------: | :----------------------------------------------- |
| &#123;{`CONTENT`}}   | the content of the .md file converted to HTML    |
| &#123;{`SUBTITLE`}}  | subtitle from  the .md file (or fallback from config)  |
| &#123;{`MENU_JSON`}} | `blab-pages-content/menu.json` untouhed                |
| &#123;{`MENU_HTML`}} | `blab-pages-content/menu.json` converted to HTML links |
| &#123;{`EDITED`}}    | .md file last edited: *2020-04-20*               |
| &#123;{`FSTGET`}}    | GET request name (md file)                       |
| &#123;{`THEME`}}     | `config array`: theme folder                     |
| &#123;{`TITLE`}}     | `config array`: global title                     |
| &#123;{`METAD`}}     | `config array`: META description                 |
| &#123;{`METAK`}}     | `config array`: META keywords                    |
| &#123;{`I6391`}}     | `config array`: language code                    |
| &#123;{`B_URL`}}     | `config array`: URL/relative path to `BlabChat/index.php`  |

---

## That's all!
