### Apaixonada pelo universo da tecnologia 🪐🖥️

<br>

[![Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](www.linkedin.com/in/milena-candida-serrano-miron-4b19401ab)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](https://mail.google.com/mail/milenaserranomiron@gmail.com)


### Linguagens que domino:

<div style="display: inline_block"></br>
 <img align="center" alt="HTML5" src = "https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
  <img align="center" alt="CSS" src = "	https://img.shields.io/badge/CSS-239120?&style=for-the-badge&logo=css3&logoColor=white">
  <img align="center" alt="PHP" src = "https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white">
  <img align="center" alt="SQL" src = "https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white">
  <img align="center" alt="JAVASCRIPT" src = "https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
</div>
<br>

### Linguagens que fizeram parte de alguns dos meus projetos, mas que eu ainda estou aprendendo:

<div style="display: inline_block"></br>
 <img align="center" alt="PYTHON" src = "https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white">
 <img align="center" alt="JAVA" src = "	https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white">
 <img align="center" alt="PHP" src = "https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white">
 <img align="center" alt="C++" src = "	https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white">
</div>




# Nome da Actions:  
name: Snake Game

# Controlador do tempo que sera feito a atualização dos arquivos.
on:
  schedule:
      # Será atualizado a cada 5 horas.
    - cron: "0 */5 * * *"

# Permite executar na na lista de Actions (utilizado para testes de build).
  workflow_dispatch:

# Regras
jobs:
  build:
    runs-on: ubuntu-latest
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Repositorio que será utilizado para gerar os arquivos.
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: milenaserrano #Seu usuario
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

      - run: git status

      # Para as atualizações.
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

