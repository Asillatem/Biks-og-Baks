# AGENTS.md – vejledning til AI-assistenter

Denne fil er til AI-værktøjer (Claude, Copilot, ChatGPT, Cursor …). Den forklarer, hvad data er, hvordan
mapperne er bygget op, og hvordan du finder rundt i tabellerne. Mennesker kan med fordel starte i `README.md`.

## Hvor ligger data?

Typisk har brugeren lavet sit eget projekt og hentet dette repo ned i en undermappe, oftest `src/`. Alle stier i
denne fil og i `DATA_DICTIONARY.md` og `RELATIONER.md` er relative til datamappen – i et sådant projekt er
`03_salg/clean/kunder.csv` altså `src/03_salg/clean/kunder.csv`. Find datamappen (den med `AGENTS.md`), før du
skriver stier.

## Hvad er det her?

Et komplet, opdigtet datasæt for **Biks&Baks ApS**, en dansk metalunderleverandør i Ikast (~80 ansatte),
for perioden **2021–2025**. Data ligner eksporter fra virksomhedens systemer: økonomi (e-conomic → Navi ERP),
salg, produktion, kvalitet, HR/løn, Trello og mail. Det bruges i undervisning i BI, data science og økonomi.

Alle personer, kunder, leverandører, CVR-numre og adresser er fiktive. Markedsdata (stål, energi, renter)
følger den virkelige udvikling.

## De tre dokumenter – og hvornår du bruger dem

| Dokument | Svarer på | Brug det når |
|---|---|---|
| `README.md` | Hvad er virksomheden, hvordan er mapperne bygget op, hvordan læses raw-filer | Du skal i gang eller forklare datasættet |
| `DATA_DICTIONARY.md` | Hvilke kolonner har tabellen, hvad betyder de, hvor mange rækker | Du skal vælge tabel eller kolonne – **før du skriver kode** |
| `RELATIONER.md` | Hvilken kolonne er nøglen, hvad joiner til hvad, hvor er faldgruberne | Du skal kombinere to eller flere tabeller, eller summere beløb |

Arbejdsgang: find emnet i tabellen herunder → slå tabellerne op i `DATA_DICTIONARY.md` → find join-vejen i
`RELATIONER.md` → læs faldgruberne nederst i `RELATIONER.md` → skriv koden.

## Emne → tabeller

Alle stier er `<mappe>/clean/<tabel>.csv`.

| Emne | Tabeller | Mappe |
|---|---|---|
| Stamdata, ejere, ledelse, helligdage/arbejdsdage | `stamdata`, `ejere`, `ledelse`, `arbejdskalender` | `01_virksomhed` |
| Årsregnskab og nøgletal | `resultatopgoerelse`, `balance`, `noegletal` (+ `aarsrapporter/*.md`) | `01_virksomhed` |
| Bogføring, kontoplan, bank | `posteringer`, `kontoplan`, `bankkontoudtog` | `02_okonomi` |
| Kunders betalinger, debitorer | `indbetalinger`, `debitorer_primo` | `02_okonomi` |
| Indkøb, leverandører, betalinger | `kreditorer`, `kreditorfakturaer`, `udbetalinger`, `kreditorer_primo` | `02_okonomi` |
| Anlæg og afskrivninger | `anlaegskartotek`, `afskrivninger` | `02_okonomi` |
| Stål-, energi- og valutapriser, rente | `markedsindeks` | `02_okonomi` |
| Kunder, varer, tilbud | `kunder`, `varer`, `tilbud` | `03_salg` |
| Ordrer, leverancer, fakturaer | `ordrer`, `ordrelinjer`, `leveringer`, `fakturaer`, `fakturalinjer` | `03_salg` |
| Maskiner, ruter, produktionsordrer | `arbejdscentre`, `ruter`, `produktionsordrer` | `04_produktion` |
| Timer på ordrer, maskinstop, OEE | `timeregistrering`, `maskinstop`, `oee` | `04_produktion` |
| Reklamationer (NCR) og kundehenvendelser | `reklamationer`, `henvendelser` | `05_kvalitet_kundeservice` |
| Medarbejdere, løn, fravær | `medarbejdere`, `stillingshistorik`, `afdelinger`, `loensedler`, `fravaer` | `06_hr` |
| Projekter og opgaver | `trello_kort`, `trello_handlinger` (+ `json/`) | `07_trello` |
| Mails | `mails` (indeks) + `eml/ÅÅÅÅ/*.eml` (selve teksten) | `08_mail` |
| Månedlige KPI'er (fra juli 2023) | `kpi_maaned` | `09_kpi` |

Øvrige mapper: `raw/` i hver mappe er systemeksporterne med format- og datafejl – brug dem kun, når opgaven
handler om datarensning. `excel/` har de samme tabeller som Excel-projektmapper.

## Sådan bruger du RELATIONER.md

- **Fremmednøgle-tabellen** fortæller, hvilken kolonne du joiner på. Står der
  `ordrelinjer.ordrenr + ordrelinjer.linjenr`, er nøglen sammensat – join på begge kolonner.
- **Match-kolonnen** viser, hvor stor en andel af værdierne der findes i måltabellen. 100 % betyder, at et
  inner join ikke taber rækker. Tomme værdier tæller ikke med (fx timer uden produktionsordre).
- **"eller" i Til-kolonnen** betyder, at nøglen findes i én af to tabeller (fx gamle fakturaer i
  `debitorer_primo`). Saml dem med `concat`, før du joiner.
- **Brugere:** kolonner som `saelger` og `behandlet_af` indeholder initialer (`brugerid`), ikke
  `medarbejder_nr`.
- **Faldgruber:** læs dem, før du summerer – især fortegn og årsafslutning i `posteringer`.

Eksempler på join-veje:

| Spørgsmål | Join-vej |
|---|---|
| Omsætning pr. kunde og år | `fakturaer` → `kunder` på `kundenr` (kreditnotaer er allerede negative) |
| Omsætning pr. vare/branche | `fakturalinjer` → `varer` på `varenr`; `fakturalinjer` → `fakturaer` → `kunder` |
| Leveringspræcision | `ordrer.bekraeftet_leveringsdato` mod `leveringer.leveringsdato` på `ordrenr` |
| Timer og kassation pr. ordre | `timeregistrering` → `produktionsordrer` på `prodordrenr` → `ordrelinjer` på `ordrenr` + `linjenr` |
| Reklamationer pr. kunde, vare eller maskine | `reklamationer` → `kunder` / `varer` / `produktionsordrer` (`laser_arbejdscenter`) |
| Betalingstid | `indbetalinger.fakturanumre` (split `;`) → `fakturaer.fakturanr`; sammenlign med `forfaldsdato` |
| Sygefravær pr. afdeling | `fravaer` → `medarbejdere` på `medarbejder_nr` → `afdelinger` |
| Hvad skete der i en sag | `mails` / `henvendelser` → `reklamationer` på `ncr_nr`; læs mailteksten i `08_mail/` + `mails.fil` |

## Sådan læser du data

- Kolonnenavne er danske uden æøå (`beloeb_dkk`, `aar`, `maaned`) – slå dem op i `DATA_DICTIONARY.md`.
- Tekst er på dansk; nogle mails er på engelsk og tysk.
- `clean/`: UTF-8, komma, ISO-datoer, decimalpunktum. Indlæs nøgler som tekst:
  `pd.read_csv(path, dtype={"ordrenr": str, "fakturanr": str, "kundenr": str})`.
- `raw/`: semikolon, decimalkomma, `dd-mm-åååå`; e-conomic-filer er `cp1252`, Navi-filer `utf-8-sig`.
- Systemskifte **1. marts 2024**: nummerformater skifter (fx `ordrenr` 31234 → `ORD-24-00012`).
- Store tabeller: `timeregistrering` (~460k rækker), `posteringer` (~170k), `fakturalinjer` (~115k).
  Læs kun de kolonner, du skal bruge.
- Læs faldgruberne i `RELATIONER.md`, før du summerer på `posteringer` (fortegn og årsafslutning).
