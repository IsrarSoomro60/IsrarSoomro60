name: Generate Snake Graph

on:
  schedule: # Har din ek dafa run hoga
    - cron: "0 0 * * *"
  workflow_dispatch: # manually run karne ka option bhi milega

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Generate Snake animation
        uses: Platane/snk@master
        with:
          github_user_name: IsrarSoomro60
          outputs: dist/github-contribution-grid-snake.svg

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
