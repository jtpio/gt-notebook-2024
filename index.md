---
marp: true
theme: default
paginate: true
footer: ![height:20px](img/twitter.svg) ![height:20px](img/github.svg) @jtpio @QuantStack
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }
---

<style>
section::after {
  content: attr(data-marpit-pagination) '/' attr(data-marpit-pagination-total);
}
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
</style>

![bg fit right:30%](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg)

# Interactive computing in the browser with Jupyterlite

## Journées du GT notebook 2024

- Jérémy Tuloup
- Pierre Poulain

https://jtpio.github.io/gt-notebook-2024

---

<div class="columns">
<div>

# Jérémy Tuloup

- Technical Director à QuantStack
- Jupyter Distinguished Contributor
- Jupyter Frontends SSC (Steering Software Council) representative
- Contributor and maintainer of many Jupyter projects
- JupyterLite creator

</div>
<div>

# Pierre Poulain

- TODO

</div>
</div>

---

# The Jupyter ecosystem

- Navigating the Jupyter Landscape
  - JupyterCon 2023 (Paris)
  - Jeremy Tuloup, Johan Mabille
  - https://www.youtube.com/watch?v=uWJ0-OPKTxI

---

![bg fit 60%](img/repos_map.svg)

---

![bg fit](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg)

---

# JupyterLite

- Everything runs in the browser via WebAssembly
- Based on the Jupyter stack:
  - Pyodide and Xeus kernels run code in the browser
  - JupyterLab and Jupyter Notebook interfaces

---

# Jupyter

![center](https://user-images.githubusercontent.com/591645/228267004-e4e2e54f-1d5f-45b7-bacb-6c3a1844c479.png)

---

# JupyterLite

![center](https://user-images.githubusercontent.com/591645/237059523-d29b94e6-7287-4608-b617-b0fe2a74877a.png)

---


![bg fit 60%](./img/jupyterlite.png)

---

# Wasm powered Jupyter running in the browser

- https://developer.mozilla.org/en-US/docs/WebAssembly

![center h:400px](https://user-images.githubusercontent.com/591645/162831191-16956085-783a-435e-b810-0d25da1379b3.png)

---

# Python in the browser

![center h:200px](https://github.com/jtpio/jobim-2024/assets/591645/771dc6ca-8ae3-418a-8368-f036df0ffbd6)

- Pyodide
- CPython compiled to WebAssembly
- Xeus Python + Emscripten Forge

---

![bg fit 75%](./img/jupyterlite.svg)

---

# Jupyter and Python in the browser

![center w:512](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/badge-launch.svg)

- ✅ no Python server
- ✅ no command line for users
- ✅ no need to install Python and other packages locally
- ✅ can be hosted as a static site

---

# JupyterLite: quick history

- Started in 2021 as the p5 notebook, a minimal notebook UI based on JupyterLab components
- May 2021: integration with Pyodide
- Developed by JupyterLab contributors (QuantStack, Nicholas Bollweg)
- Partially funded (thanks Bloomberg)
- Progressive integration in JupyterLab?

---

# A Jupyter web site available in a few seconds

![center h:600px](https://user-images.githubusercontent.com/591645/120649478-18258400-c47d-11eb-80e5-185e52ff2702.gif)

---

# `jupyterlite-core`: a static site generator

```shell
pip install jupyterlite-core

jupyter lite build
```

---

# HTML, CSS, JavaScript, Wasm files

<div class="columns">
<div>


```
├── api
│   └── translations
│       ├── all.json
│       └── en.json
├── bootstrap.js
├── build
│   ├── 9507.1e6cc5d.js
│   ├── 9602.62bf0f1.js
│   ├── 9621.e2e8b5d.js
│   ├── ...
│   ├── repl
│   │   ├── bundle.js
│   ├── retro
│   │   ├── bundle.js
│   ├── schemas
│   │   ├── all.json
│   │   ├── @jupyterlab
│   │   │   ├── application-extension
│   │   │   │   ├── commands.json
│   │   │   │   ├── context-menu.json
│   │   │   │   ├── shell.json
│   │   │   │   └── sidebar.json
│   ├── themes
│   │   └── @jupyterlab
│   │       ├── theme-dark-extension
│   │       │   ├── index.css
│   │       │   └── index.js
...
```
</div>
<div>

```
...
│   │       └── theme-light-extension
│   │           ├── index.css
│   │           └── index.js
├── config-utils.js
├── extensions
│       └── xeus-python-kernel
│           └── static
│               ├── numpy-1.24.2-py310h6d2fff6_0.0.data
│               ├── numpy-1.24.2-py310h6d2fff6_0.0.js
│               ├── python-3.10.2-h_hash_26_cpython.0.data
│               ├── python-3.10.2-h_hash_26_cpython.0.js
│               ├── python_data.js
│               ├── remoteEntry.35b4eac217ec6bf078a4.js
├── lab
│   ├── favicon.ico
│   ├── index.html
│   ├── jupyter-lite.ipynb
│   ├── jupyter-lite.json
│   ├── package.json
│   ├── tree
│   │   └── index.html
│   └── workspaces
│       └── index.html
...
```

</div>
</div>


---

# Easy to deploy

Served via well-cacheable, static HTTP(S) on most static web hosts

<div class="columns">
<div>

![center width:256](https://user-images.githubusercontent.com/591645/120675034-00f29080-c495-11eb-928c-26bb94e8eb68.png)
![center width:256](https://user-images.githubusercontent.com/591645/120676545-6dba5a80-c496-11eb-9b2b-604e92c3429b.png)
![center width:256](https://user-images.githubusercontent.com/591645/120675516-6f375300-c495-11eb-819c-d6f1fb3cb0f1.png)

</div>
<div>

![center width:256](https://user-images.githubusercontent.com/591645/120676313-2df37300-c496-11eb-8639-25e2fc606850.png)
![center width:256](https://user-images.githubusercontent.com/591645/236239105-d00f05df-ee79-4062-a0a8-f0f0118bbe1d.png)
![center h:128](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Amazon-S3-Logo.svg/428px-Amazon-S3-Logo.svg.png)

</div>
</div>

---

# Use cases

---

![center h:300px](https://user-images.githubusercontent.com/591645/162619390-ecab994a-3f39-4e26-af78-ca2569aee9b2.png)

```html
<iframe
  src="https://jupyterlite.github.io/demo/repl/index.html?kernel=python&toolbar=1"
  width="100%"
  height="500px"
>
</iframe>
```

---

<iframe
  src="https://jtp.io/gt-notebook-2024/lite/repl/index.html?kernel=python&toolbar=1"
  width="100%"
  height="500px"
>
</iframe>

---

![bg fit](https://github.com/jtpio/alposs-2024/assets/591645/c0fe58fa-c2d8-4777-a996-9a8cd8f641f7)

---

<video
  controls
  width="100%"
  height="600px"
  src="https://github.com/jtpio/alposs-2024/assets/591645/9b5e247d-cb89-4b15-aba3-97e5ab381bb5">
</video>

---

https://github.com/rowanc1/myst-lite

<video
  controls
  width="100%"
  height="600px"
  src="https://github.com/rowanc1/myst-lite/assets/913249/c62478d3-fc90-4350-8006-9a65846a2f26">

</video>

---

# 🎓 Education

- Capytale: https://capytale.fr
- Paris Saclay: https://jupyter.gitlab.dsi.universite-paris-saclay.fr/tutoriel-jupyter/utiliser.html
- UC Berkeley
- LabNBook (Université Grenoble Alpes): https://labnbook.fr/les-labdocs-code-sont-disponibles-dans-labnbook-integration-de-jupyterlite/
- Grenoble INP UGA Phelma: https://phelma-sicom.gricad-pages.univ-grenoble-alpes.fr/1a/3pmpols6-cours/TD_1.html

---

# :test_tube: Current developments

- In-browser terminal (Ian Thomas)
- AI code completions and chat (Nicolas Brichet)
- Real Time Collaboration via WebRTC (David Brochart)
- Emscripten Forge and Conda Forge (Thorsten Beier, Isabel Paredes, Anutosh Bhat)
- Xeus-R (Isabel Paredes, Anutosh Bhat)

---

# :sparkles: Demo :sparkles:

- Terminal: https://jupyterlite-terminal.vercel.app/
- RTC (other WebRTC): https://davidbrochart.github.io/jupyter-shared-drive
- AI code completions and chat: https://jupyterlite.github.io/jupyterlab-codestral/

---

# :sparkles: AI code completions and chat

<video
  controls
  width="100%"
  height="600px"
  src="https://github.com/jupyterlite/jupyterlab-codestral/assets/591645/855c4e3e-3a63-4868-8052-5c9909922c21">

</video>

---

# :desktop_computer: Terminal

<video
  controls
  width="100%"
  height="600px"
  src="https://raw.githubusercontent.com/jtpio/pydata-paris-2024-jupyterlite-xeus/main/img/terminal.m4v">
</video>

---

# :busts_in_silhouette: Real Time Collaboration


<video
  controls
  width="100%"
  height="600px"
  src="https://github.com/user-attachments/assets/ab03433c-2ac2-4856-8e83-b5cc17ed3f6f">

</video>

---

# :rocket: Deploy to GitHub Pages

- https://github.com/jupyterlite/demo

![center height:400px](https://raw.githubusercontent.com/jupyterlite/xeus-python-demo/main/deploy.gif)


---

https://jupyterlite.github.io/demo/


![](https://github.com/jtpio/alposs-2024/assets/591645/9e19fcea-4f17-4bd4-a83a-9eb548bd9968)

---

# 🎓 Feedback on the use in education

Pierre Poulain, Université Paris Cité

## Context

Introductory Bioinformatics course:

- 40-45 first-year students (biology/chemistry)
- Introduction to Python programming (2 x 2-hour practical sessions)

Choice of Jupyter notebooks for interactivity and literate programming

Challenges in software installation in computer labs

---

## 💻 IT Solutions

Historically: MyBinder

- Quite slow: takes several minutes to rebuild a (Docker) image (upon each commit)
- Free computing resources, not always available

Since 2023: JupyterLite

- Easy to deploy (GitHub → GitHub Pages)
- No installation required for students
- Works everywhere (university, library, home)
- Interactive quizzes since 2024 (https://github.com/jmshea/jupyterquiz)

---

## Demo 🚀

Source code : https://github.com/pierrepo/intro-bioinfo-python-2024

Website (GitHub pages) : https://pierrepo.github.io/intro-bioinfo-python-2024/lab/index.html

---

## Student feedback 1/3

![center](img/student_feedback_1.png)

---

## Student feedback 2/3

![center](img/student_feedback_2.png)

---

## Student feedback 3/3

![center](img/student_feedback_3.png)

---

## Next steps

Septembre 2025, new course of simulation in biology (Python):

- 250 second-year students
- 150 third-year students

---

# ⌛ Reproducibility time capsule

- WebAssembly is a web standard
- Runnable for much longer than native binary packages

![center h:300](https://github.com/jtpio/jobim-2024/assets/591645/4686d0f6-8c4a-4195-8420-74a71ff0b510)

---

# 🔍 References

- Jupyter documentation: https://docs.jupyter.org
- This presentation:
  - Repo: https://github.com/jtpio/gt-notebook-2024
  - Slides: https://jtp.io/gt-notebook-2024

---

# Thanks !
