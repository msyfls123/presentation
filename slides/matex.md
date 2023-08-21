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
# [MaTeX](https://msyfls123.github.io/MaTeX/)

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

## Why not Word?

<div class="column-2">

&nbsp;
![width:550px](images/latex-word-markdown.png)

&nbsp;
- No installation
- Easy to use
- Open for extension

_Outdated Tech Makes Workers Feel Less Productive, More Likely To Quit_
</div>


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

## Visual Editor

![bg right contain](images/simplemde-editor.jpg)

- WYSIWG
- **Pure Text Output**
- Toolbar
- Syntax Guide

---

## Tokenize

![bg right 100% contain](images/tokens.jpg)


- Nested Structure
- Tags VS **Entity**
- Pagination
  - soft break
  - paragraph

---

## Image?

![bg right vertical](images/image.png)
![bg](images/upload-image.gif)

* Editor **NOT** support image upload. [#202](https://github.com/RIP21/react-simplemde-editor/issues/202)
* Trade-off: external image uploading
* Problem: Where to upload?

---

## Storage in JavaScript

|Category|Items|Visibility|Query|
|---|:--:|---|---|
|Pure File|![width:100px](images/folder.png)|⭐⭐⭐|⭐|
|Browser|![width:200px](images/indexeddb.png)|⭐⭐|⭐⭐⭐|
|Server|![width:160px](images/sqlite.png) ![width:200px](images/leveldb.png)|⭐|⭐⭐⭐|

</div>

---

## Render Mode

<div class="column-2">
Client/Sever Mode
<div class="mermaid">
sequenceDiagram;
    client->>server: Text Data
    rect rgba(200, 150, 255, .3)
    client->>server: Image(latency, authentication)
    server-->server: Store Image
    end
    server->>client: PDF(latency)
</div>

Single Mode ✅
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

## Pagination

![bg right cover](images/pagination.jpg)

* Precipitation（沉淀）
* **Pagebreak among paragraphs** destroied my pagination algorithm
* Two repositories, one dream.
* PDFMake is also PDFKit
* I'll always miss the time in struggling with pagination.

---

## Features

<div class="column-2">

![width:500px](images/nest-list.jpg)
Nested List

&nbsp;
![width:500px](images/preview-scroll-sync.gif)
Preview Scroll Sync 🚫
Fallback: `#page=xxx` anchor

</div>

---

## Last Critical Problem

<div class="column-2">

![width:550px](images/chinese-fonts.jpg)

&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![width:450px](images/simpsons-bugs.gif)
</div>


---

## <ruby>> 27MB!<rt>Chinese fonts</rp></ruby>

<div class="column-2">
<div class="mermaid">
sequenceDiagram;
    autonumber
    client->>server: Text Data
    client->>server: Image
    loop generatePDF
        client->>server: Text Data
        server->>client: PDF(expensive)
    end
</div>
Client/Sever Mode

<div class="mermaid center">
flowchart TD;
    fonts["load fonts(expensive, once)"]-->editor(Editor)
    editor-->text
    editor-->image(Image)
    text-->content(Content)
    image-->content
    fonts-->content
    content-->PDF
    PDF-->editor
</div>
Single Mode ✅
</div>


---

## Futhermore

### User Feedback
- Support import/export raw data(markdown text)
- Pause/Resume PDF generation periodically
- Deploying web application
  Only domain bill, cloud object storage and CDN is **FREE**

### Vision

- Import & Export both text and images(zip format)

---

# Thanks 

![bg right 55%](images/invisible_formatting.png)

_To avoid errors like this, we render all text and pipe it through OCR before processing, fixing a handful of irregular bugs by burying them beneath a smooth, uniform layer of bugs._

<script src="./images/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>
