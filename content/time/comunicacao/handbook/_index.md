---
title: Handbook
weight: 2
---

# Como usar este Handbook

## Lendo o Manual

Este manual é dividido nas seções Time (administrativo), Anotação e 
Modelagem. Cada seção tem suas sub-páginas com conteúdo relevante.

O manual não está completo, algumas páginas não terão conteúdo pois 
está em construção e uma parte do conteúdo está em inglês pois precisa 
de tradução e revisão.

{{< hint warning >}}
**2 Índices de Conteúdo**

* O índice geral do handbook está ao lado esquerdo.
* O índice específico de uma página estará ao lado direito quando 
necessário.

{{</ hint >}}

**Se você identificar qualquer informação incompleta, errada ou 
ultrapassada, por favor faça a edição, levará apenas um minuto.**

## Modificações de conteúdo

#### Vídeo com passo a passo básico para modificar o manual

[![video tutorial para modificacao do manual](http://img.youtube.com/vi/OGM-Zk5Ds5Y/0.jpg)](http://www.youtube.com/watch?v=OGM-Zk5Ds5Y "Handbook - Como modificar o manual")

#### Descrição e mais detalhes

Para editar uma página, clique no link `Edit in WebIDE` ao final da 
página. isto te levará diretamente ao repositório da página que você 
estava visualizando, e você poderá executar a modificação escrevendo 
com uma sintaxe chamada *Markdown*.

No canto esquerdo terá 3 icones/abas, um para edição, um para revisão 
e o último para submissão. Durante a modificação, você poderá visualizar 
a renderização clicando em `Preview Markdown` (logo acima do espaço 
onde o texto/conteúdo aparece) e após modificar, você poderá visualizar 
as diferenças da versão atual com a modificada caso queira. 
Por fim a aba de submissão permitirá finalizar o commit.

Após clicar em `Commit...`, adicione uma mensagem sobre sua 
modificação, que deve ser concisa sobre o que está sendo modificado, 
como por exemplo "Melhora definição do que são modelos de extração 
de informação na seção de Modelagem". Opte por criar uma nova branch, 
com um nome informativo como "\<usuario\>-nova-definicao-modelos-extracao" 
(onde \<usuario\> é o nome do seu usuário no sistema). E por fim 
deixe marcado a opção de iniciar um novo Merge Request.

Na tela seguinte adicione um titulo e uma descrição para o MR 
(para pequenas modificações, o titulo pode ser como o nome da 
branch criada, e a descrição pode ser a mensagem do commit). Deixe 
marcada a opção para deletar a branch após o MR ser executado. Por 
fim, clique em `Submit merge request`.

Você pode verificar se a sua modificação não quebrou o site acessando 
a [aba de CI/CD](https://gitlab.com/Semantix/aijus/data-science/handbook/-/pipelines) 
do repositório. Você também pode acompanhar o status do Merge Request 
na [aba de Merge Requests](https://gitlab.com/Semantix/aijus/data-science/handbook/-/merge_requests) 
do repositório do handbook.

A `Web IDE` permite explorar outros arquivos do projeto, utilizando 
o explorador de arquivos na aba de edição, para casos em que deseja-se 
modificar mais de um arquivo.

## Structure or Theme Change

For a change to the whole site, it is recommended to perform the updates locally using a regular git workflow. The readme file in this repo talks about how to run hugo locally. The Merge Request for these changes will include a link to the local environment to review changes. It will only work for the developer or anyone who checks out the branch and runs Hugo locally.

Be sure to update docs about how to use the handbook for any changes that impact the user worlflow.

###  Menu and Navigation

There are 2 approaches to managing the left-side navigation. One is to use the front matter for each page in the site and let it compile the menu at build-time. The alternative is to go into the `config.toml` and set `BookMenuBundle = '/menu'` (or uncomment it). Then the sample `menu/index.md` file will be used to render the left navigation.

{{< hint info >}}
**Menu Structure**

For changes to titles, order, or other menu renderings, edit the page's _front matter_ or modify the `_index.md` file in that directory.
{{</ hint >}}

The `menu/index.md` approach has a significant drawback, an additional approval will be required for any changes to the site that require updates to the navigation.

The in-page approach has the drawback that as the site grows, many pages will require the `bookHidden: true` or `bookCollapseSection: true` to be set to prevent being overwehlmed by content.

### Adding Images and Screentshots

To add an image, open the `/static/images` directory and upload your image. Create subdirectories as needed to help organize the images. 

To insert the image into a page, you can either use the `![image](/images/path.png)` approach or the [`Figures` shortcode](https://gohugo.io/content-management/shortcodes/#figure).

An `[image]` looks like this: 

![image](/images/screengrab-static-images.png)

Be sure the leave off the "static" directory since the contents are loaded directly into the root of the published content. 

A 'Figure' looks like this: 


{{< figure src="/images/screengrab-static-images.png" title="Title: Screengrab of Image Path" caption="Captions can add extra context." >}}

### Adding Simple Diagrams

Check out the [Mermaid shortcode](https://themes.gohugo.io//theme/hugo-book/docs/shortcodes/mermaid/) for creating simple diagrams. 

{{< mermaid >}}
graph LR;
  id1[Identify Change]
  id2[Commit Changes]
  id3[Merge Change]
  id1-- Open WebIDE -->id2
  id2-- Create Merge Request -->id3
{{< /mermaid >}}

## Front Matter Options

```toml
---
title: GitLab Workflow with Infrastructure as Code
weight: 11
bookHidden: true
bookCollapseSection: true
bookToc: false
bookFlatSection: true
---
```

*  `bookHidden`: if set to true, hides the page from the left navigation
*  `bookCollapseSection`: if set to true, it only shows this page in the left nav and child pages only appear when navigated to.
*  `weight`: Sets the order in the left navigation with 1 at the top and 10000 at the bottom.
*  `title`: the text that shows in the left navigation for the title
*  `bookToc`: Hides the page-specific table of content (on the right-hand side of the page)
*  `bookFlatSection`: If set to true, promotes the pages at this level to the same tier as the _index page.

## Tecnologia do Handbook

O handbook foi feito utilizando um template baseado nas seguintes tecnologias:

*  [Hugo Static Site Generator](https://gohugo.io)
    *  [Markdown](https://www.markdownguide.org/cheat-sheet/) for simple formatting (title, bold, link)
    *  [Shortcodes](https://themes.gohugo.io//theme/hugo-book/) for formatting (columns, hints, tabs, diagrams)
    *  [Docker build container](https://gitlab.com/brownfield-dev/remote/handbook/-/tree/docker) to create the HTML rendering from the markdown and images
*  [Hugo Book Theme](https://themes.gohugo.io/hugo-book/)
    *  Page layout, additional shortcodes
*  [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/)
    *  Web site hosting
*  [GitLab Flow](https://about.gitlab.com/solutions/gitlab-flow/)
    *  Handbook content change workflow
    *  Use issues to formulate ideas
    *  Use merge requests to create and update content collaboratively

All of the functionality is open source so anything can be scrutinized.

## Shortcodes

### Buttons

Buttons are styled links that can lead to local page or external link.

#### Example

```tpl
{{</* button relref="/" [class="..."] */>}}Get Home{{</* /button */>}}
{{</* button href="https://github.com/alex-shpak/hugo-book" */>}}Contribute{{</* /button */>}}
```

{{< button relref="/" >}}Get Home{{< /button >}}
{{< button href="https://github.com/alex-shpak/hugo-book" >}}Contribute{{< /button >}}

### Columns

Columns help organize shorter pieces of content horizontally for readability.


```html
{{</* columns */>}} <!-- begin columns block -->
# Left Content
Lorem markdownum insigne...

<---> <!-- magic sparator, between columns -->

# Mid Content
Lorem markdownum insigne...

<---> <!-- magic sparator, between columns -->

# Right Content
Lorem markdownum insigne...
{{</* /columns */>}}
```

#### Example

{{< columns >}}
#### Left Content
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.

<--->

#### Mid Content
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter!

<--->

#### Right Content
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /columns >}}

### Expand

Expand shortcode can help to decrease clutter on screen by hiding part of text. Expand content by clicking on it.

#### Example
##### Default

```tpl
{{</* expand */>}}
## Markdown content
Lorem markdownum insigne...
{{</* /expand */>}}
```

{{< expand >}}
#### Markdown content
Lorem markdownum insigne...
{{< /expand >}}

##### With Custom Label

```tpl
{{</* expand "Custom Label" "..." */>}}
## Markdown content
Lorem markdownum insigne...
{{</* /expand */>}}
```

{{< expand "Custom Label" "..." >}}
#### Markdown content
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /expand >}}

### Hints

Hint shortcode can be used as hint/alerts/notification block.  
There are 3 colors to choose: `info`, `warning` and `danger`.

```tpl
{{</* hint [info|warning|danger] */>}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{</* /hint */>}}
```

#### Example

{{< hint info >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

{{< hint warning >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

{{< hint danger >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

### KaTeX

KaTeX shortcode let you render math typesetting in markdown document. See [KaTeX](https://katex.org/)

#### Example
{{< columns >}}

```latex
{{</* katex [display] [class="text-center"]  */>}}
x = \begin{cases}
   a &\text{if } b \\
   c &\text{if } d
\end{cases}
{{</* /katex */>}}
```

<--->

{{< katex >}}
x = \begin{cases}
   a &\text{if } b \\
   c &\text{if } d
\end{cases}
{{< /katex >}}

{{< /columns >}}

#### Display Mode Example

Here is some inline example: {{< katex >}}\pi(x){{< /katex >}}, rendered in the same line. And below is `display` example, having `display: block`
{{< katex display >}}
x = \begin{cases}
   a &\text{if } b \\
   c &\text{if } d
\end{cases}
{{< /katex >}}
Text continues here.

### Mermaid Chart

[Mermaid](https://mermaidjs.github.io/) is library for generating svg charts and diagrams from text.

#### Example

{{< columns >}}
```tpl
{{</* mermaid */>}}
sequenceDiagram
    Alice->>Bob: Hello Bob, how are you?
    alt is sick
        Bob->>Alice: Not so good :(
    else is well
        Bob->>Alice: Feeling fresh like a daisy
    end
    opt Extra response
        Bob->>Alice: Thanks for asking
    end
{{</* /mermaid */>}}
```

<--->

{{< mermaid >}}
sequenceDiagram
    Alice->>Bob: Hello Bob, how are you?
    alt is sick
        Bob->>Alice: Not so good :(
    else is well
        Bob->>Alice: Feeling fresh like a daisy
    end
    opt Extra response
        Bob->>Alice: Thanks for asking
    end
{{< /mermaid >}}

{{< /columns >}}

### Tabs

Tabs let you organize content by context, for example installation instructions for each supported platform.

```tpl
{{</* tabs "uniqueid" */>}}
{{</* tab "MacOS" */>}} # MacOS Content {{</* /tab */>}}
{{</* tab "Linux" */>}} # Linux Content {{</* /tab */>}}
{{</* tab "Windows" */>}} # Windows Content {{</* /tab */>}}
{{</* /tabs */>}}
```

#### Example

{{< tabs "uniqueid" >}}
{{< tab "MacOS" >}}
# MacOS

This is tab **MacOS** content.

Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /tab >}}

{{< tab "Linux" >}}

# Linux

This is tab **Linux** content.

Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /tab >}}

{{< tab "Windows" >}}

# Windows

This is tab **Windows** content.

Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /tab >}}
{{< /tabs >}}
