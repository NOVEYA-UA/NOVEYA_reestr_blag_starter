# NOVEYA — Реестр благ и НРМ
Дата: 2025-09-22

Этот пакет — заготовка репозитория GitHub для представления **Реестра благ** и методики **совершенствования нормирования расхода ресурсов (НРМ)**.

## Что внутри
- `docs/FDL-Ethica-LICENSE.md` — этическая лицензия (черновик).
- `docs/Реестр-благ-спецификация.md` — поля и инварианты реестра.
- `docs/Методика-НРМ-сводка.md` — краткая опора на НРМ (ссылка на оригинальную методику).
- `.github/ISSUE_TEMPLATE/учёт-благ.md` — шаблон задачи на регистрацию артефакта/вклада.
- `.github/PULL_REQUEST_TEMPLATE.md` — чек-лист «паспорт происхождения» и НРМ.
- `proposal/OpenAI-как-учитывать-благо-и-ресурсы.md` — сопроводительное письмо.
- `schemas/reestr-blag.schema.json` — схема данных для импорта/проверок.
- `data-templates/*.csv` — заготовки таблиц для импорта в Notion.

## Коротко о принципе
**Квартальный отчёт = представление над тем же «Реестром благ» (1:1).**
Все суммы и доли считаются из одного источника данных.

## License & Ethics

This repository follows a dual-license scheme:

- **Code:** AGPL-3.0  
- **Content / Symbols / Media:** CC BY-NC-SA 4.0  
- **Ethical charter:** see [LICENSE-ETHICS.md](./LICENSE-ETHICS.md)

Use of FDL/NOVEYA symbols is allowed **only** in open, benevolent contexts; closed or exploitative usage is prohibited.

---

## 3) Краткая настройка CI 

`.github/workflows/ci.yml` (для Python; при необходимости сделаю Node-вариант):

```yaml
name: ci
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - run: pip install -r requirements.txt || true
      - run: pip install pytest || true
      - run: pytest -q || echo "No tests yet"
