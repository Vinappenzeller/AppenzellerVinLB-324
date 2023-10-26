# LB 324

## Aufgabe 2
1. `pre-commit` installieren
   ```
   pip install pre-commit
   ```
2. `pre-commit install` ausführen
   ```
   pre-commit install
   ```
3. Nun kann man im Wurzelverzeichnis des Projekts ein File erstellen `.pre-commit-config.yaml`
4. Inhalt des Files
   ```
   repos:
- repo: https://github.com/ambv/black
  rev: 23.7.0
  hooks:
    - id: black
      language_version: python3.12

- repo: https://github.com/pre-commit/pre-commit-hooks
  rev: v2.0.0
  hooks:
  - id: check-byte-order-marker
  - id: check-case-conflict
  - id: check-json
  - id: check-yaml
  - id: end-of-file-fixer
  - id: flake8
  - id: mixed-line-ending
    args:
    - --fix=lf
  - id: trailing-whitespace

- repo: local
  hooks:
  -   id: needs-hash
      name: commit message needs issues
      language: pygrep
      entry: '#\d+'
      args: [--multiline, --negate]
      stages: [commit-msg]

  -   id: pytest-check
      stages: [commit]
      types: [python]
      name: pytest-check
      entry: python -m pytest
      language: system
      pass_filenames: false
      always_run: true
```

## Aufgabe 4
Erklären Sie hier, wie Sie das Passwort aus Ihrer lokalen `.env` auf Azure übertragen.
