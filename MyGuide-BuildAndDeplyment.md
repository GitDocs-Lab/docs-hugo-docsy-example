# 🛠️ Guide: Ako riadiť build a deployment Docsy projektu

---

## 🟢 1️⃣ Lokálne: Hugo príkazy

**Hugo samotné:**
- `hugo` → build projektu, výsledok uloží do `public/`
- `hugo server` → spustí lokálny webserver na http://localhost:1313

👉 Minimálne vieš všetko buildovať a testovať len s Hugo, bez NPM.

Príklad:
```bash
hugo
hugo server
```

---

## 🔧 2️⃣ Lokálne: NPM skripty (package.json)

**Prečo NPM?**
- pretože Docsy používa PostCSS, autoprefixer, SCSS
- pretože v `package.json` sú predpripravené skripty na build, serve, update

Dôležité skripty:
- `npm run serve` → to isté čo `hugo server` + zapojený PostCSS
- `npm run build:production` → `hugo --minify` + CSS pipeline
- `npm run build:preview` → build s preview URL (napr. Netlify/Vercel)
- `npm run update:dep` → aktualizuje CSS tooly

👉 Ak používaš NPM, už nemusíš ručne volať Hugo.

Príklad:
```bash
npm install
npm run serve
npm run build:production
```

---

## ⚙️ 3️⃣ Automatizovane: GitHub Actions

**Čo robí GitHub Actions?**
- automatizuje build a deploy pri každom pushi
- spúšťa tie isté príkazy, ktoré robíš lokálne (napr. `npm install`, `hugo --minify`)
- deployne výsledok (napr. na `gh-docsy` branch)

Workflow:
- pushneš do `main`
- Actions:
  - checkout
  - setup Go, Node, Hugo
  - `npm install`
  - `hugo --minify`
  - deploy do GitHub Pages

👉 Už nemusíš robiť nič ručne.

Príklad súboru: `.github/workflows/deploy.yml`

---

## 🏗️ Ako to spolu zapadá?

| Scenár            | Kedy použiť                                  |
|--------------------|---------------------------------------------|
| Hugo príkazy      | Rýchly test, keď nepotrebuješ CSS pipeline  |
| NPM skripty       | Lokálne buildy s plnou CSS/JS podporou      |
| GitHub Actions    | Automatizovaný deploy na produkciu          |

---

## 💡 Odporúčanie pre teba

✅ Na lokálny vývoj:  
```bash
npm install
npm run serve
```

✅ Na manuálny build pre deploy:
```bash
npm run build:production
```

✅ Na automatizovaný deploy:
- nakonfiguruj `deploy.yml`
- pushni do `main`
- hotovo, Actions sa postarajú

---

