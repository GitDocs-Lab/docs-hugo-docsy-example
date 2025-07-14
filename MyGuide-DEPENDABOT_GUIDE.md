# 🤖 DEPENDABOT_GUIDE.md

## Čo je Dependabot?

Dependabot je GitHub bot, ktorý:
✅ sleduje závislosti v tvojom projekte,  
✅ zisťuje, či existujú novšie alebo bezpečnejšie verzie,  
✅ automaticky otvára pull requesty (PR), ktoré navrhujú aktualizácie.

---

## Ako ho spoznáš?

- Na karte **Pull requests** uvidíš PR od autora `dependabot[bot]`.
- PR bude mať názov ako:
  ```
  Bump hugo-extended from 0.147.9 to 0.148.1
  ```

---

## Čo s tým robiť?

1️⃣ **Otvoriť PR**  
Klikni na názov a pozri si:
- čo sa mení,
- či sú tam konflikty,
- aké sú závislosti.

2️⃣ **(Voliteľne) otestovať**  
Ak chceš byť opatrný:
- checkoutni branch lokálne:
  ```bash
  git fetch origin dependabot/...
  git checkout dependabot/...
  ```
- spusti:
  ```bash
  npm install
  hugo server
  ```

3️⃣ **Merge**  
Ak je všetko v poriadku → klikni:
```
Merge pull request
```

4️⃣ **(Voliteľne) odstráň vetvu**

---

## Prečo je to dôležité?

✅ Udržuješ aktuálne závislosti.  
✅ Znižuješ riziko bezpečnostných problémov.  
✅ Máš kontrolu nad tým, čo merge-neš.

---

## Ako vypnúť Dependabot?

Ak by si ho nechcel používať, môžeš:
- upraviť alebo odstrániť `.github/dependabot.yml`,
- v GitHub Settings vypnúť Dependabot alerts alebo updates.

---

## Upozornenie

Dependabot je pomocník, nie magická guľka.  
Stále platí:
👉 **merge len to, čo rozumieš alebo vieš, že funguje.**

