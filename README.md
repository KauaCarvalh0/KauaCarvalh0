## Olá! Eu não esperva você por aqui! Seja bem vindo! 👋

Prazer meu nome é Kauã! Sou um desenvolvedor apaixonado por tecnologia e programação.

**O que eu faço ✍**

- *Desenvolvimento Web*: Estou aprendendo a trabalhar com HTML, CSS, JavaScript e diversos frameworks modernos. 💻
- *Back-end*: Tenho experiência com linguagens como Python, Java, entre outras. 🖥
- *Projetos Open Source*: Sou fã de contribuir para a comunidade de código aberto. 👨‍💻
- *Toco Violão e Guitarra 🎸*
- *Amo jogar jogos. 🎮*
- *Fãnzaço da banda Jovem Dionisio!* "Acₒᵣda Pₑdᵣᵢₙₕₒ". 🐢🪑

## Como me encontrar 🔍

- [Twitter (X)](https://x.com/KauCarv75289759?t=vO8qfqvkV7c4N25BKN9cbw&s=09): Veja minhas últimas atualizações. 🌐
- [Instagram](https://www.instagram.com/kkaua_carv?igsh=ODBqc3FnbmYybWZy): Algumas fotos! 🤳

Sinta-se à vontade para explorar meus repositórios e me seguir para acompanhar meus projetos futuros. Se quiser colaborar em um projeto ou tiver alguma dúvida, fique à vontade para entrar em contato! 

Obrigado pela visita! 🙌

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
          github_user_name: artur-debv
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
