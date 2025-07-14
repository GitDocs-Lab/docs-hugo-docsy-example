# 📦 Docsy + Hugo projekt: Štartovacia príručka

## 1️⃣ Po inštalácii Docsy: Ako overiť, že funguje

1. Skontroluj Go a Node.js:
   ```bash
   go version
   node -v
   npm -v
   ```

   Ak nie sú, nainštaluj:
   - Go → https://go.dev/dl/ alebo `brew install go`
   - Node.js → https://nodejs.org/ alebo `brew install node`

2. Nainštaluj Node závislosti (ak máš `package.json`):
   ```bash
   npm install
   ```

3. Stiahni Hugo moduly:
   ```bash
   hugo mod get
   hugo mod tidy
   ```

4. Spusti lokálny server:
   ```bash
   hugo server
   ```
   ➡ Otvor prehliadač: [http://localhost:1313](http://localhost:1313)

5. Ak máš PostCSS chyby (pri buildovaní CSS), doinštaluj:
   ```bash
   npm install -D postcss postcss-cli autoprefixer
   ```

---

## 2️⃣ Deploy na GitHub Pages (vetva `gh-docsy`)

1. Priprav build do priečinka `public/`:
   ```bash
   hugo --minify
   ```

2. Commitni obsah `public/` do vetvy `gh-docsy`:
   ```bash
   git checkout --orphan gh-docsy
   git --work-tree=public add --all
   git --work-tree=public commit -m "Deploy Docsy site"
   git push origin gh-docsy --force
   git checkout main
   ```

3. V GitHub repozitári nastav:
   - Settings → Pages → Branch: `gh-docsy` → `/ (root)`

4. Hotovo! Web beží na:
   ```
   https://<tvoje-username>.github.io/<repo-name>/
   ```

---

## 3️⃣ Ako upravovať layout, menu, obsah

Pre pokročilé úpravy odporúčam:

- Layouty (šablóny): https://www.docsy.dev/docs/adding-content/layouts/
- Menu a navigácia: https://www.docsy.dev/docs/adding-content/navigation/
- Vlastný obsah, shortcode-y, obrázky: https://www.docsy.dev/docs/adding-content/
- Styling (SCSS, JS): https://www.docsy.dev/docs/adding-content/lookandfeel/

---

### 💡 Odporúčanie pre začiatok

- Upraviť `config.yaml` (názov webu, jazyk, logo)
- Pridať vlastné stránky do `content/`
- Nastaviť jednoduché menu cez `menus.main` v configu

---

### 📦 Poznámka k vetvám

Ak používaš viac dokumentačných systémov (napr. MkDocs, Hugo, Docusaurus), odporúčame pre každý samostatnú deploy vetvu:

- `gh-docsy` → pre Docsy
- `gh-mkdocs` → pre MkDocs
- `gh-hugo` → pre čistý Hugo
- `gh-docusaurus` → pre Docusaurus

---

