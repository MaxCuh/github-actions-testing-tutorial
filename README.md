# github-actions-testing-tutorial

# Automatisert testing med Python og GitHub Actions

Dette er en enkel guide for VG1 elever for å lære:
- Hva automatisert testing er
- Hvordan teste lokalt med pytest
- Hvordan bruke GitHub Actions

---

# Hva du trenger (før du starter)

Installer dette:

## 1. Python 3
Last ned: https://www.python.org

Sjekk:
python3 --version

---

## 2. VS Code (anbefalt)
https://code.visualstudio.com

---

## 3. Git
https://git-scm.com

Sjekk:
git --version

---

## 4. Terminal (Mac/Linux)
Mac: innebygd terminal eller VS Code terminal

---

## 5. (Valgfritt)
- Oh My Zsh (bare for bedre terminal)
- Ikke nødvendig

---

# DEL 1 – Testing lokalt (uten GitHub Actions)

## 1. Lag prosjekt

mkdir testing-demo cd testing-demo

---

## 2. Lag fil: calculator.py

python def add(a, b):     return a + b 

---

## 3. Lag testfil: test_calculator.py

python from calculator import add  def test_add():     assert add(1, 2) == 3 

---

## 4. Installer pytest

python3 -m pip install pytest

---

## 5. Kjør tester

python3 -m pytest

---

## Resultat:

✔️ Hvis riktig:
1 passed

❌ Hvis feil:
FAILED

---

## Test dette:

Endre koden:

python return a - b 

Kjør igjen → testen feiler

---

# Hva lærte du?

- Tester sjekker koden automatisk
- Du slipper å teste manuelt

---

# 🚀DEL 2 – GitHub Actions (automatisk testing)

## 1. Lag repo på GitHub

Gå til:
https://github.com → New repository

---

## 2. Koble prosjektet

git init git add . git commit -m "første versjon" git branch -M main git remote add origin DIN_URL git push -u origin main

---

## 3. Lag workflow

Lag fil:

.github/workflows/python-tests.yml

---

## 4. Lim inn:

yaml name: Python Tests  on:   push:  jobs:   test:     runs-on: ubuntu-latest      steps:       - uses: actions/checkout@v4        - uses: actions/setup-python@v5         with:           python-version: "3.11"        - run: pip install pytest        - run: pytest 

---

## 5. Push kode

git add . git commit -m "la til workflow" git push

---

# Hva skjer nå?

GitHub:
1. Starter server
2. Installerer Python
3. Kjører tester

---

# Resultat

🟢 Grønn = OK  
🔴 Rød = Feil  

---

# Demo (anbefalt)

1. Gjør feil i kode  
2. Push  
3. Se GitHub feile inn på Actions 
4. Fiks → push → grønn  

---

# Oppsummering

- Automatisert testing sparer tid
- Finner feil tidlig
- Brukes i ekte utvikling

---

# Ekstra

Dette er en del av:
CI/CD (Continuous Integration)

---

# Tips

- Hold koden enkel
- Test små funksjoner
- Push ofte

---

# Ferdig!

Du har nå laget:
✔️ Tester  
✔️ Automatisering  
✔️ GitHub workflo
