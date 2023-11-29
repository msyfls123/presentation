---
theme: custom
marp: true
_class: lead
math: katex
---

# 前端十年

Kimima(马申彦)
2023.12.2

---

# 目录

- 个人介绍
- 工程师思维与学生思维
- 大厂经历为何吃香
- 后互联网时代前端的冰与火

---

# 个人经历

- 现就职于阅文，曾任职于腾讯、豆瓣等互联网大厂
- 负责开发维护腾讯文档、豆瓣阅读等国民级产品
- 在 JSConf China、QConf 等技术大会进行演讲
- 为 Webpack 等知名前端开源仓库提交代码

---

# 工程师思维与学生思维
## 一些意料之中的偏见

- 前端简单，有手就能干 ✅
- 前端天花板比较低 🚫
- 前端不需要编程知识 🚫
- 低代码将给前端带来致命打击 🚫

---

# 工程师思维与学生思维
## 前端门槛低

- “为什么我选择了前端这个职业？”
- 卡在设计和后端之间
<div class="mermaid">
%%{init: {"flowchart": {"htmlLabels": false}} }%%
flowchart LR
    design([设计])
    f2e([前端])
    be([后端])
    app([客户端])
    intuitive((直观、外在))
    implicit((隐含、内禀))
    design --> f2e
    f2e --> be
    be --> app
    intuitive --- design
    app --- implicit
</div>

---

# 工程师思维与学生思维
## 转变思维

- 避免标签式学习（Flash -> HTML/CSS/JS -> K8S/WASM -> AI）
- 前端的意义在于做好 web 的浏览器部分，而不是以这个框束缚自己
- 交流比竞争更有用

<script src="./images/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>
