<h2 align="center">Hola👋! Me llamo Patricio Casanova</h2>

###

<h4 align="center">Soy un estudiante de Analista de Sistemas Con muchas ganas de adquirir experiencia laboral para crecer como profesional!</h4>

###

<h2 align="center">🛠  Herramientas:</h2>

###

<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="58" alt="javascript logo"  />
  <img width="39" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="58" alt="html5 logo"  />
  <img width="39" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="58" alt="css3 logo"  />
  <img width="39" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" height="58" alt="php logo"  />
  <img width="39" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" height="58" alt="mysql logo"  />
</div>

###

<br clear="both">

<div align="center">
  <img height="220" src="https://img.freepik.com/vector-premium/ordenador-portatil-grafico-azul-pc-futurista-aislado-sobre-fondo-negro_541075-1283.jpg"  />
</div>

###

<h4 align="center">Pueden comunicarse  en..  👇</h4>

###

<div align="center">
  <a href="www.linkedin.com/in/patricio-casanova-479037245" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="linkedin logo"  />
  </a>
  <a href="patriciocasanova@outlook.com.ar" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Outlook&logo=microsoft-outlook&label=&color=0078D4&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="microsoft-outlook logo"  />
  </a>
</div>

###

<br clear="both">

<img src="https://raw.githubusercontent.com/PatricioCasanova23/PatricioCasanova23/output/snake.svg" alt="Snake animation" />

###
name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
