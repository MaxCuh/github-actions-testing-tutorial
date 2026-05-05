# Automatisert testing med Python og GitHub Actions (tutorial)

Denne guiden viser:
- Hvordan teste kode lokalt med pytest
- Hvordan bruke virtual environment (venv)
- Hvordan automatisere testing med GitHub Actions

---

# Hva trenger du?

## Python 3
https://www.python.org/downloads/

Sjekk:
```bash
python3 --version
```
Hhelst bruk "3.11"

---

## Code editor -VS Code (anbefalt)
https://code.visualstudio.com/

---

## GitHub
https://github.com/

---

# DEL 1 – Lokalt (Uten Github actions)

## 1. Lag prosjekt

```bash
mkdir demo
cd demo
```

---

## 2. Lag virtual environment (VENV)

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3. Installer pytest

```bash
pip install pytest
```

---

## 4. Lag fil: `calculator.py`

```python
def add(a, b):
    return a + b
```

---

## 5. Lag testfil: `test_calculator.py`

```python
from calculator import add

def test_add():
    assert add(1, 2) == 3
```

---

## 6. Kjør tester

```bash
pytest
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

## 💡 Hva skjer?

- Vi bruker venv for å holde prosjektet isolert
- pytest tester koden automatisk

---

# Viktig: .gitignore

Lag fil:

```bash
.gitignore
```

Innhold:

```text
venv/
__pycache__/
.pytest_cache/
```

---

## requirements.txt

Lag fil:

```text
pytest
```

---

# DEL 2 – Med GitHub Actions

## 1. Lag repository på GitHub

Gå til:
https://github.com → New repository

---

## 2. Last opp prosjektet

Du kan:
- Dra filene inn på GitHub  
ELLER  
- Bruke GitHub Desktop  

---

## 3. Lag workflow-fil

Lag mappe og fil:

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

      - run: pip install -r requirements.txt

      - run: pytest
```

---

## 5. Last opp / push kode

Hver gang du pusher kode til git med "git push",
så kjører github testene automatisk.
Du kan se testen inne på repository/Actions



---

# Hva skjer?

Når du pusher:

1. GitHub starter en server  
2. Installerer Python  
3. Installerer pytest  
4. Kjører testene  

---

# Resultat

- 🟢 Grønn = alt fungerer  
- 🔴 Rød = feil i koden  

---

# Test testene

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
