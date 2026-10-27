# Biks&Baks ApS – et komplet datasæt fra en dansk underleverandør

Biks&Baks ApS er en (fiktiv) metalvirksomhed i Ikast med ca. 80 ansatte. Vi laserskærer, bukker, svejser,
CNC-bearbejder og pulverlakerer emner til industrikunder i landbrugsmaskiner, vind, fødevareudstyr, byggeri og
transportbånd – i Danmark, Sverige og Tyskland.

Her er virksomhedens data for **2021–2025**: regnskab, salg, produktion, kvalitet, løn, mails og Trello – som
de ville se ud, hvis du fik adgang til systemerne i en rigtig virksomhed.

> Alt er opdigtet: virksomheden, personerne, kunderne, leverandørerne, CVR-numrene og adresserne.
> Ligheder med virkelige personer eller virksomheder er tilfældige. Markedsudviklingen (stålpriser,
> energikrise, renter) følger dog den virkelige udvikling.

## Kom i gang

Lav dit eget projekt, og hent data ned i en `src/`-mappe i det:

```
mkdir mit-projekt
cd mit-projekt
git clone https://github.com/Asillatem/Biks-og-Baks src
```

Din egen kode og dine notebooks ligger så ved siden af `src/`, fx `pd.read_csv("src/03_salg/clean/kunder.csv")`.

Start med [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md) – den beskriver alle filer og kolonner.
[`RELATIONER.md`](RELATIONER.md) viser, hvordan tabellerne hænger sammen (nøgler og joins), og samler de
faldgruber, der er værd at kende, før du regner. Bruger du en AI-assistent, læser den [`AGENTS.md`](AGENTS.md).

## Mapper

| Mappe | Indhold |
|---|---|
| `01_virksomhed/` | Stamdata, ejere, ledelse, kalender, årsrapporter og nøgletal |
| `02_okonomi/` | Kontoplan, alle posteringer, bank, debitorer/kreditorer, købsfakturaer, anlæg |
| `03_salg/` | Kunder, varer, tilbud, ordrer, leverancer, fakturaer |
| `04_produktion/` | Maskiner, ruter, produktionsordrer, timeregistrering, maskinstop, OEE |
| `05_kvalitet_kundeservice/` | Reklamationer (NCR) og kundehenvendelser |
| `06_hr/` | Medarbejdere, stillinger, lønsedler, fravær |
| `07_trello/` | Trello-boards (JSON-eksport) + flade tabeller |
| `08_mail/` | Mails som .eml-filer + indeks |
| `09_kpi/` | Månedligt KPI-board |
| `excel/` | De samme tabeller som Excel-projektmapper (én pr. område; de største tabeller kun som CSV) |

Hver datamappe har to versioner:

- **`clean/`** – klar til analyse: UTF-8, komma-separeret, datoer som `2024-03-01`, decimalpunktum,
  ens kolonnenavne gennem hele perioden.
- **`raw/`** – sådan som systemerne eksporterer: semikolon, decimalkomma, datoer som `01-03-2024`, danske
  kolonneoverskrifter. Virksomheden skiftede økonomisystem fra **e-conomic til Navi ERP den 1. marts 2024**, så
  ERP-tabellerne findes i to filer med hvert systems kolonnenavne og nummerformater. Raw-filerne indeholder også
  de fejl, man finder i virkelige data.

## Indlæs data

```python
import pandas as pd

# clean
fakturaer = pd.read_csv("03_salg/clean/fakturaer.csv", parse_dates=["fakturadato", "forfaldsdato"])

# raw – e-conomic eksporterer Windows-1252, Navi ERP UTF-8 med BOM
gl = pd.read_csv("03_salg/raw/fakturaer_e-conomic_2021-2024.csv", sep=";", decimal=",", encoding="cp1252")
ny = pd.read_csv("03_salg/raw/fakturaer_navi_2024-2025.csv", sep=";", decimal=",", encoding="utf-8-sig")
```

Mails:

```python
from email import policy
from email.parser import BytesParser

with open("08_mail/eml/2023/...eml", "rb") as f:
    mail = BytesParser(policy=policy.default).parse(f)
print(mail["From"], mail["Subject"])
print(mail.get_content())
```

Excel: alle CSV-filer kan åbnes direkte i Excel. Brug *Data → Fra tekst/CSV* til `raw/`-filerne og vælg
semikolon og den rigtige tegnkodning.

## Om virksomheden

- **1989** – smedene Kurt "Biks" Bisgaard og Poul "Baks" Baksgaard starter i en lejet hal i Ikast.
- **1998** – omdannet til ApS og flytter til Smedevænget 14.
- **2006** – første laserskærer; fra reparationssmedje til underleverandør.
- **2012** – eget pulverlakeringsanlæg.
- **2016** – Kurt sælger sin andel; Poul og en ekstern investor ejer virksomheden.
- **2021–2025** – stålpriser, energikrise, nye kunder og kunder der forsvinder, et nyt ERP-system og et
  generationsskifte i ledelsen. Resten må du finde i data.

| | |
|---|---|
| CVR | 57422580 (fiktivt) |
| Branche | 25.62.00 Maskinforarbejdning |
| Regnskabsår | Kalenderår, regnskabsklasse C |
| Overenskomst | Industriens Overenskomst |
