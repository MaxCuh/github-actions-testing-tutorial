# github-actions-testing-tutorial

# Automatisert testing med Python og GitHub Actions

Denne guiden viser:
- Hvordan teste kode lokalt med pytest
- Hvordan automatisere testing med GitHub Actions

---

# Hva trenger du?

## 1. Python 3
https://www.python.org/downloads/

Sjekk:
```bash
python3 --version
```
Bruk gjerne "3.11"

---

## 2. VS Code (anbefalt)
https://code.visualstudio.com/

---

## 3. GitHub konto
https://github.com/

---

## DEL 1 – Testing lokalt

## 1. Lag prosjekt

```bash
mkdir testing-demo
cd testing-demo
```

---

## 2. Lag fil: `calculator.py`

```python
def add(a, b):
    return a + b
```

---

## 3. Lag testfil: `test_calculator.py`

```python
from calculator import add

def test_add():
    assert add(1, 2) == 3
```

---

## 4. Installer pytest

```bash
python3 -m pip install pytest
```

---

## 5. Kjør tester

```bash
python3 -m pytest
```

---

## Resultat

Hvis riktig:

```bash
1 passed
```

Hvis feil:

```bash
FAILED
```

---

## Test selv

Endre i `calculator.py`:

```python
return a - b
```

Kjør tester igjen → FAIL

---

# DEL 2 – GitHub Actions

## 1. Lag repository på GitHub

Gå til:
https://github.com → New repository

---

## 2. Last opp filer

Du kan:
- Dra filene inn på GitHub  
ELLER  
- Bruke GitHub Desktop  

---

## 3. Lag workflow-fil

Lag fil:

```bash
.github/workflows/python-tests.yml
```

---

## 4. Lim inn dette:

```yaml
name: Python Tests

on:
  push:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-python@v5
        with:
          python-version: "3.11"

      - run: pip install pytest

      - run: pytest
```

---

## 5. Push / last opp

Nå trenger du ikke å skrive "pytest" i terminalen.
Push kode til Github med "git push" -
Gå til repository/actions, der ser du testen

GitHub kjører testene automatisk

---

# Hva skjer?

GitHub:
1. Starter en server
2. Installerer Python
3. Installerer pytest
4. Kjører testene

---

# Resultat

- 🟢 Grønn = alt fungerer
- 🔴 Rød = feil i koden

---

# Demo

1. Gjør en feil i koden
2. Last opp / push
3. Gå til "Actions"
4. Se testen feile
5. Fiks → last opp → grønn

---

# Oppsummering

- Tester kjører automatisk
- Finner feil tidlig
- Brukes i ekte utvikling

---

# !!

Dette er en del av:

CI/CD (Continuous Integration)
