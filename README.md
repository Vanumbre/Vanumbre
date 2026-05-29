
const fs = require("fs");

const cols = 20;
const rows = 7;

let grid = "";

for (let y = 0; y < rows; y++) {
  for (let x = 0; x < cols; x++) {
    grid += `<rect x="${x * 14}" y="${y * 14}" width="10" height="10" rx="2" fill="#1f2937"/>`;
  }
}

const pacman = `
<circle r="6" fill="yellow">
  <animateMotion dur="6s" repeatCount="indefinite"
    path="M0,0 H280"/>
</circle>
`;

const ghosts = `
<circle cx="80" cy="30" r="5" fill="red"/>
<circle cx="120" cy="50" r="5" fill="pink"/>
<circle cx="160" cy="20" r="5" fill="cyan"/>
`;

const svg = `
<svg width="300" height="120" xmlns="http://www.w3.org/2000/svg">

${grid}
${ghosts}
${pacman}

</svg>
`;

fs.writeFileSync("pacman.svg", svg);

console.log("Pacman generated!");





name: Generate Pacman SVG

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Generate SVG
        run: node generate.js

      - name: Commit
        run: |
          git config --global user.name "github-actions"
          git config --global user.email "github-actions@github.com"
          git add pacman.svg
          git commit -m "update pacman" || echo "no changes"
          git push



<!-- BANNER -->
<p align="center">
  <img src="./assets/banner.png" />
</p>

# VANUMBRE 🚀

> Code. Create. Dominate.

---

## 👨‍💻 ABOUT ME

- Developer
- Cybersecurity Enthusiast
- Open Source Lover
- Always Learning

---

## ⚡ TECH STACK

- Python 🐍
- JavaScript ⚡
- C 💻
- HTML5 🌐
- CSS3 🎨

---

## 🧠 OPERATING SYSTEMS

- Linux 🐧
- Ubuntu
- Windows

---

## 📊 GITHUB STATS

![stats](https://github-readme-stats.vercel.app/api?username=vanumbre&show_icons=true&theme=tokyonight)

---

## 🔥 CONTRIBUTION GRAPH

![graph](https://github-readme-activity-graph.vercel.app/graph?username=vanumbre&theme=react-dark)

---

## 👾 CONTRIBUTION PAC-MAN

![pacman](./pacman.svg)

---

## 🔗 CONNECT

- Instagram
- LinkedIn
- GitHub

---

> Code. Create. Dominate.
