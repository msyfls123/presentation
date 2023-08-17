---
theme: custom
marp: true
_class: lead
math: katex
---

# Introduction
Speaker: **Shenyan Ma** (aka **Kimi**)

Aug. 2023

---
# Career


- Worked as front end engineer on Tencent, Douban Read, Snail Games(internship).
- Master of Design, learn about product design, UX design and ergonomics.
- Speeches at JSConf China, QConf in Tencent.
- Contributions to open sources like Playwright, Webpack etc.

---

# Knowledge

- Front End: React / RxJS / Lodash / Cycle.js
- Language: TypeScript / Rust / Python / C++ / $\LaTeX{}$
- Build Tools: Rollup / Gulp / Webpack

---

# Project

![bg right](./images/bg-pattern-head-eff397.png)

### TencentDocs Desktop

Electron Application
* Local edit for Office document
* C++ Addons
* Monitor & Report
* CI/CD pipeline

---

# Project

### Douban Read

* TypeScript refactoring
* GraphQL API
* Mobile App rich text editor
* Book search engine

![bg right 70%](./images/v2-254fb13c31a4c50521260397fb1631ac_ipico.jpg)

---

<!--
_class: lead
-->
# MaTeX

Markdown-to-PDF editor

---
<style scoped>
p {
  display: flex;
  justify-content: center;
}

</style>

## Motivation

![](images/gandalf.jpeg)

Bro, I need your help!

---


![bg 50%](images/markdown.png)
![bg 50%](images/right-arrow.png)
![bg 50% contain](images/unnamed.png)

## Motivation


---

## Basic Steps

<div class="mermaid center">
sequenceDiagram;
    participant editor as react-simplemde-editor
    participant tokenizer as markdown-it
    editor->>tokenizer: raw text
    participant parser
    tokenizer->>parser: tokens
    participant pdfmake as pdfmake
    parser->>pdfmake: contents
    pdfmake->>editor: PDF document
</div>


---

## Render Mode

<div class="column-2">
Client/Sever Mode
<div class="mermaid">
sequenceDiagram;
    client->>server: Text Data
    rect rgba(200, 150, 255, .3)
    client->>server: Image?
    server-->server: Store Image
    end
    server->>client: PDF
</div>

Single Mode
<div class="mermaid center">
flowchart TD;
    editor(Editor)-->text(Text Data)
    editor-->image(Image)
    text-->token(Token)
    token-->content(Content)
    image-->content
    content-->PDF
</div>
</div>


---

## Features

- Image Layout
- Import/Export Document
- Nested List
- Pagination
- PDF Anchor
- Chinese Fonts

---

## Known issues

- Not support images between paragraphs.

<script src="https://unpkg.com/mermaid@10.3.1/dist/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>
