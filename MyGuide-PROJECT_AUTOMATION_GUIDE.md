# 🚀 PROJECT_AUTOMATION_GUIDE.md

## Automatizácia v tomto projekte

Tento projekt používa:
✅ Dependabot → sledovanie aktualizácií závislostí,  
✅ GitHub Actions → automatické buildy a deploy,  
✅ Releases → verzovanie výstupov (ak pridáme).

---

## 🔧 Ako fungujú GitHub Actions?

- V `.github/workflows/` máme súbor `deploy.yml`.
- Po každom pushi do `main` sa spustí:
  - build projektu (`npm install`, `hugo --minify`),
  - deploy do vetvy `gh-docsy`.

---

## 🛡️ Tokeny (PAT vs. GITHUB_TOKEN)

| Token             | Kde sa používa       | Potrebuje manuálne nastavenie? |
|-------------------|-----------------------|--------------------------------|
| `GITHUB_TOKEN`    | Vstavaný token pre Actions | Nie                           |
| `PAT (GH_PAT)`    | Personal Access Token | Áno, v Settings → Secrets      |

Ak projekt používa PAT, každý, kto si spraví kópiu (template/fork), musí si svoj PAT pridať do `Secrets`.

---

## 🤖 Dependabot + Actions: Ako spolupracujú?

1️⃣ Dependabot otvorí PR → aktualizuje napr. `hugo-extended`.  
2️⃣ GitHub Actions otestujú, či build funguje.  
3️⃣ Ty rozhodneš, či PR merge-neš.

---

## 💥 Odporúčaná stratégia

✅ Merge-uj Dependabot PRs, až keď build prejde.  
✅ Neprepadaj panike, keď niečo spadne — skontroluj logy v Actions.  
✅ Ak treba, fixni lokálne → pushni opravu → merge.

---

## 💡 Bonus (ak pridáme Releases)

Ak sa rozhodneme používať GitHub Releases:
- budeme cez `gh release` alebo Actions generovať zip/tar distribúcie,  
- budeme tagovať stable verzie (`v1.0.0`, `v1.1.0` atď.).

---

## 🌍 Prečo to celé robiť?

- **Automatizácia ťa chráni pred zabudnutím.**
- **Robí za teba nudné úlohy.**
- **Umožňuje ti sústrediť sa na obsah a kvalitu.**

