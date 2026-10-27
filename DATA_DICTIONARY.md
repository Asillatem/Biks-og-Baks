# Datadictionary – Biks&Baks ApS

Alle tabeller findes i `clean/` (UTF-8, komma-separeret, ISO-datoer, decimalpunktum) og i `raw/` (som systemerne eksporterer: semikolon, decimalkomma, dd-mm-åååå; ERP-tabeller delt i e-conomic og Navi ERP ved systemskiftet 1. marts 2024 med hvert systems egne kolonnenavne).

## 01_virksomhed – Virksomheden

### stamdata

Virksomhedens stamoplysninger (som på proff.dk/CVR).

17 rækker · `01_virksomhed/clean/stamdata.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `felt` | Felt | Startdato som ApS |
| `vaerdi` | Værdi | 1998-01-01 |

### ejere

Ejere og reelle ejere med ejerandele over tid.

4 rækker · `01_virksomhed/clean/ejere.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `ejer` | Ejer (person eller selskab) | PB Holding Ikast ApS |
| `reel_ejer` | Reel ejer | Poul Baksgaard |
| `ejerandel_pct` | Ejerandel i % | 35.0 |
| `fra_dato` | Fra dato | 2023-07-01 |
| `til_dato` | Til dato (tom = fortsat) | 2023-06-30 |

### ledelse

Direktion og bestyrelse over tid.

10 rækker · `01_virksomhed/clean/ledelse.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `navn` | Navn | Gitte Rasmussen |
| `rolle` | Rolle | Bestyrelsesmedlem |
| `fra_dato` | Fra dato | 2023-07-01 |
| `til_dato` | Til dato (tom = fortsat) | 2023-06-30 |

### arbejdskalender

Virksomhedens kalender: helligdage, ferielukning og normtimer pr. dag.

1.826 rækker · `01_virksomhed/clean/arbejdskalender.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `dato` | Dato | 2022-09-01 |
| `aar` | År | 2022 |
| `kvartal` | Kvartal | 3 |
| `maaned` | Måned (1–12) | 9 |
| `iso_uge` | ISO-ugenummer | 35 |
| `ugedag` | Ugedag | Torsdag |
| `helligdag` | Navn på helligdag (tom hvis ingen) | Pinsedag |
| `lukkeperiode` | Sommerferie/julelukning | Sommerferie |
| `arbejdsdag` | Om dagen er en arbejdsdag | True |
| `normtimer` | Normtimer for en fuldtidsansat | 7.5 |

### resultatopgoerelse

Resultatopgørelse pr. år (lang tabel: én række pr. post og år).

70 rækker · `01_virksomhed/clean/resultatopgoerelse.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `post` | Regnskabspost | Skat af årets resultat |
| `aar` | År | 2022 |
| `beloeb_dkk` | Beløb i DKK | -1517240.0 |

### balance

Balance pr. 31. december (lang tabel: én række pr. post og år).

110 rækker · `01_virksomhed/clean/balance.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `post` | Regnskabspost | Gæld til pengeinstitutter |
| `aar` | År | 2022 |
| `beloeb_dkk` | Beløb i DKK | 10219682.0 |

### noegletal

Hoved- og nøgletal pr. år som i årsrapporten.

5 rækker · `01_virksomhed/clean/noegletal.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `aar` | År | 2022 |
| `nettoomsaetning_dkk` | Nettoomsætning | 123635583.0 |
| `bruttofortjeneste_dkk` | Bruttofortjeneste | 55400127.0 |
| `resultat_af_primaer_drift_dkk` | Resultat af primær drift | 7686124.0 |
| `resultat_foer_skat_dkk` | Resultat før skat | 6896543.0 |
| `aarets_resultat_dkk` | Årets resultat | 5379304.0 |
| `egenkapital_dkk` | Egenkapital ultimo | 31018354.0 |
| `balancesum_dkk` | Balancesum | 72981361.0 |
| `antal_ansatte_gns` | Gennemsnitligt antal ansatte | 80 |
| `soliditetsgrad_pct` | Egenkapital / balancesum | 42.5 |
| `likviditetsgrad_pct` | Omsætningsaktiver / kortfristet gæld | 116.3 |
| `afkastningsgrad_pct` | Primær drift / balancesum | 10.5 |
| `egenkapitalforrentning_pct` | Årets resultat / gns. egenkapital | 19.0 |
| `overskudsgrad_pct` | Primær drift / omsætning | 6.2 |

## 02_okonomi – Økonomi

### kreditorer

Leverandørkartotek (kreditorer).

60 rækker · `02_okonomi/clean/kreditorer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `kreditornr` | Kreditornummer (leverandør) | 50021 |
| `navn` | Navn | Steelskan Fragt ApS |
| `cvr_momsnr` | CVR-/momsnummer | 86475642 |
| `land` | Landekode | DK |
| `adresse` | Adresse | Energivej 38 |
| `postnr` | Postnummer | 6700 |
| `by` | By | Esbjerg |
| `kategori` | Kategori | Fragt |
| `valuta` | Valuta | DKK |
| `betalingsbetingelse` | Betalingsbetingelse (N30 = netto 30 dage, LM+30 = løbende måned + 30) | N30 |
| `bank_regnr` | Bankens registreringsnummer (læs som tekst) | 3409 |
| `bank_kontonr` | Bankkontonummer (læs som tekst) | 3365484573 |
| `iban` | IBAN | DE02802983222274146763 |
| `kontakt_email` | Kontakt-mail | info@linepro-vognmandsforretning.dk |
| `oprettet_dato` | Oprettet dato | 2024-02-26 |
| `oprettet_af` | Oprettet af (brugerid) | MIGRERING |
| `spaerret` | Spærret | False |

### kontoplan

Kontoplan med både e-conomic- og Navi-kontonumre og årsrapportlinje.

84 rækker · `02_okonomi/clean/kontoplan.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `konto` | Kontonummer i e-conomic | 2920 |
| `konto_navi` | Kontonummer i Navi ERP | 402100 |
| `navn` | Navn | Ejendomsskat |
| `navn_navi` | Kontonavn i Navi ERP | Ejendomsskat |
| `kontotype` | Drift eller status | Drift |
| `aarsrapport_linje` | Linje i årsrapporten kontoen indgår i | Andre eksterne omkostninger |

### posteringer

Alle finansposteringer 2021–2025 (hovedbogen). Debet positiv, kredit negativ.

171.811 rækker · `02_okonomi/clean/posteringer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `dato` | Dato | 2022-10-13 |
| `bilagsnr` | Bilagsnummer | 70814 |
| `konto` | Kontonummer i e-conomic | 6310 |
| `tekst` | Tekst | Faktura 70814 Vestjysk Procesudstyr ApS |
| `beloeb_dkk` | Beløb (debet +, kredit −) | -4444.81 |
| `momskode` | Momskode | U25 |
| `kilde` | Kilde (kladde/modul) | Salg |
| `reference` | Reference (fx fakturanumre) | 70806 |
| `system` | System: e-conomic (til 29/2-2024) eller Navi ERP (fra 1/3-2024) | e-conomic |
| `konto_navi` | Kontonummer i Navi ERP | 941000 |
| `kontonavn` | Kontonavn | Udgående moms |

### bankkontoudtog

Kontoudtog for driftskontoen med løbende saldo.

11.348 rækker · `02_okonomi/clean/bankkontoudtog.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `dato` | Dato | 2022-09-22 |
| `tekst` | Tekst | Indbetaling Møller & Søn A/S |
| `beloeb_dkk` | Beløb i DKK | 47708.84 |
| `saldo_dkk` | Saldo efter bevægelsen | -5216754.63 |
| `modpart` | Modpart | Møller & Søn A/S |
| `reference` | Reference (fx fakturanumre) | 69662;69726;69734;69776 |
| `bilagsnr` | Bilagsnummer | BANK22-01153 |

### indbetalinger

Indbetalinger fra kunder med de fakturaer, de dækker.

8.093 rækker · `02_okonomi/clean/indbetalinger.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `betalingsdato` | Betalingsdato | 2022-09-22 |
| `kundenr` | Kundenummer | 10007 |
| `beloeb_dkk` | Beløb i DKK | 237337.97 |
| `beloeb_valuta` | Beløb i valuta | 30808.96 |
| `valuta` | Valuta | DKK |
| `fakturanumre` | Fakturanumre betalingen dækker (;-separeret) | 69569;69608;69613;69808;69827;69890 |
| `bilagsnr` | Bilagsnummer | BANK22-01148 |

### udbetalinger

Betalinger til leverandører med de kreditorfakturaer, de dækker.

2.577 rækker · `02_okonomi/clean/udbetalinger.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `betalingsdato` | Betalingsdato | 2022-09-08 |
| `kreditornr` | Kreditornummer (leverandør) | 50047 |
| `beloeb_dkk` | Beløb i DKK | 104341.03 |
| `bilag_kreditorfakturaer` | Kreditorbilag betalingen dækker | K2200526 |
| `leverandoer_fakturanumre` | Leverandørens fakturanumre | 2200018 |
| `bilagsnr` | Bilagsnummer | BANK22-01937 |

### debitorer_primo

Åbne kundefakturaer pr. 1. januar 2021.

690 rækker · `02_okonomi/clean/debitorer_primo.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `fakturanr` | Fakturanummer (heltal i e-conomic, FAK-ÅÅ-NNNNN i Navi) | 59231 |
| `fakturadato` | Fakturadato | 2020-12-04 |
| `forfaldsdato` | Forfaldsdato | 2021-01-03 |
| `kundenr` | Kundenummer | 10010 |
| `valuta` | Valuta | DKK |
| `kurs` | Valutakurs (DKK pr. valutaenhed) | 1.0 |
| `beloeb_ex_moms_dkk` | Beløb ekskl. moms i DKK | 21230.83 |
| `moms_dkk` | Moms i DKK | 5307.71 |
| `beloeb_inkl_moms_dkk` | Beløb inkl. moms i DKK | 26538.54 |

### kreditorer_primo

Åbne leverandørfakturaer pr. 1. januar 2021.

78 rækker · `02_okonomi/clean/kreditorer_primo.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `bilagsnr` | Bilagsnummer | K2000027 |
| `kreditornr` | Kreditornummer (leverandør) | 50002 |
| `leverandoer_fakturanr` | Leverandørens fakturanummer | INV2000026 |
| `fakturadato` | Fakturadato | 2020-12-14 |
| `forfaldsdato` | Forfaldsdato | 2021-01-13 |
| `beloeb_ex_moms_dkk` | Beløb ekskl. moms i DKK | 86830.07 |
| `moms_dkk` | Moms i DKK | 21707.52 |
| `beloeb_inkl_moms_dkk` | Beløb inkl. moms i DKK | 108537.59 |
| `omkostningstype` | Omkostningstype | Materialer |
| `tekst` | Tekst | Plade 1.4301, 3.599 kg |

### kreditorfakturaer

Modtagne leverandørfakturaer (købsbilag) med bogføring og godkendelse.

4.266 rækker · `02_okonomi/clean/kreditorfakturaer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `bilagsnr` | Bilagsnummer | K2200584 |
| `kreditornr` | Kreditornummer (leverandør) | 50001 |
| `leverandoer_fakturanr` | Leverandørens fakturanummer | F-102345 |
| `fakturadato` | Fakturadato | 2022-09-09 |
| `modtaget_dato` | Modtaget dato | 2022-09-09 |
| `forfaldsdato` | Forfaldsdato | 2022-10-30 |
| `valuta` | Valuta | DKK |
| `beloeb_ex_moms_dkk` | Beløb ekskl. moms i DKK | 215729.25 |
| `moms_dkk` | Moms i DKK | 53932.31 |
| `beloeb_inkl_moms_dkk` | Beløb inkl. moms i DKK | 269661.56 |
| `omkostningstype` | Omkostningstype | Materialer |
| `tekst` | Tekst | Plade S355J2, 20.593 kg |
| `maengde_kg` | Mængde i kg (materialer) | 13555.2 |
| `indkoebsordrenr` | Indkøbsordrenummer | IK2200574 |
| `bogfoert_af` | Bogført af (brugerid) | HELU |
| `bogfoert_tidspunkt` | Bogført tidspunkt | 2022-09-13 10:26:00 |
| `godkendt_af` | Godkendt af (brugerid) | MEDA |

### anlaegskartotek

Anlægskartotek: maskiner, bygninger, inventar og software.

58 rækker · `02_okonomi/clean/anlaegskartotek.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `anlaegsnr` | Anlægsnummer | S06 |
| `beskrivelse` | Beskrivelse | Svejseplads 6 - Kemppi X5 MIG/MAG |
| `anlaegsgruppe` | Anlægsgruppe | Produktionsanlæg og maskiner |
| `anskaffet_dato` | Anskaffelsesdato | 2016-07-01 |
| `anskaffelsessum_dkk` | Anskaffelsessum | 65000 |
| `leverandoer` | Leverandør | Nordisk Maskinhandel A/S |
| `finansiering` | Eje eller finansiel leasing | Eje |
| `levetid_aar` | Afskrivningsperiode i år | 10 |
| `afhaendet_dato` | Afhændelsesdato | 2025-06-02 |
| `salgspris_dkk` | Salgspris ved afhændelse | 60000.0 |
| `akk_afskrivning_primo_2021_dkk` | Akkumulerede afskrivninger pr. 1/1-2021 | 28708.33 |

### afskrivninger

Månedlige afskrivninger pr. anlæg.

2.190 rækker · `02_okonomi/clean/afskrivninger.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `anlaegsnr` | Anlægsnummer | S12 |
| `maaned` | Måned | 2021-10 |
| `afskrivning_dkk` | Afskrivning i måneden | 541.67 |

### markedsindeks

Månedlige markedsdata: stål-, rustfrit-, aluminiums-, gas- og elindeks, EUR-kurs, rente.

60 rækker · `02_okonomi/clean/markedsindeks.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `maaned` | Måned (ÅÅÅÅ-MM) | 2022-09 |
| `staal_indeks` | Stålpladeindeks (jan. 2021 = 100) | 140.7 |
| `rustfrit_indeks` | Rustfrit-indeks | 131.1 |
| `aluminium_indeks` | Aluminiumsindeks | 117.5 |
| `gas_indeks` | Naturgasindeks | 578.0 |
| `el_indeks` | Elprisindeks | 376.2 |
| `eur_dkk` | EUR-kurs | 7.4389 |
| `nationalbank_rente_pct` | Nationalbankens foliorente | 0.65 |

## 03_salg – Salg

### kunder

Kundekartotek (debitorer).

71 rækker · `03_salg/clean/kunder.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `kundenr` | Kundenummer | 10024 |
| `navn` | Navn | Termostålbyg ApS |
| `cvr_momsnr` | CVR-/momsnummer | 69967256 |
| `land` | Landekode | DK |
| `adresse` | Adresse | Industriparken 8 |
| `postnr` | Postnummer | 6900 |
| `by` | By | Skjern |
| `branche` | Branche | Byggeri |
| `kundegruppe` | Kundegruppe | B |
| `valuta` | Valuta | DKK |
| `betalingsbetingelse` | Betalingsbetingelse (N30 = netto 30 dage, LM+30 = løbende måned + 30) | N30 |
| `kreditgraense_dkk` | Kreditgrænse | 120000 |
| `kontaktperson` | Kontaktperson | Øjvind Madsen |
| `kontakt_email` | Kontakt-mail | oejvind@termostaalbyg.dk |
| `faktura_email` | Mail til fakturaer | oejvind@termostaalbyg.dk |
| `kunde_siden` | Kunde siden | 2016-05-01 |
| `spaerret` | Spærret | False |
| `spaerret_dato` | Spærret dato | 2024-10-14 |

### varer

Varekartotek: kundespecifikke emner og ydelser.

827 rækker · `03_salg/clean/varer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `varenr` | Varenummer | BB-100276 |
| `beskrivelse` | Beskrivelse | Konsole |
| `kundenr` | Kundenummer | 10004 |
| `kunde_tegningsnr` | Kundens tegningsnummer | 593.7485.49 |
| `revision` | Tegningsrevision | C |
| `varetype` | Emne eller ydelse | Emne |
| `materiale` | Materiale | S235JR |
| `tykkelse_mm` | Pladetykkelse i mm | 3.0 |
| `vaegt_kg` | Vægt i kg | 13.461 |
| `overflade` | Overflade (RAL-farve, børstet, ubehandlet) | Ubehandlet |
| `operationer` | Operationer i ruten | LASER-BUK |
| `std_batch_stk` | Standard seriestørrelse | 25 |
| `salgspris_2021_dkk` | Listepris 2021 | 194.18 |
| `kostpris_materiale_2021_dkk` | Materialekostpris 2021 | 108.01 |
| `oprettet_dato` | Oprettet dato | 2025-02-17 |
| `status` | Status | Aktiv |

### tilbud

Afgivne tilbud og deres udfald.

2.139 rækker · `03_salg/clean/tilbud.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `tilbudsnr` | Tilbudsnummer | 7714 |
| `system` | System: e-conomic (til 29/2-2024) eller Navi ERP (fra 1/3-2024) | e-conomic |
| `tilbudsdato` | Tilbudsdato | 2022-11-30 |
| `kundenr` | Kundenummer | 10046 |
| `saelger` | Sælger (brugerid) | NIVE |
| `varenr` | Varenummer | BB-100385 |
| `beskrivelse` | Beskrivelse | Kabinetplade |
| `kunde_tegningsnr` | Kundens tegningsnummer | 10046-T309 |
| `materiale` | Materiale | DX51D+Z275 |
| `antal` | Antal | 50 |
| `stkpris_dkk` | Stykpris i DKK | 402.21 |
| `tilbudsbeloeb_dkk` | Tilbudsbeløb | 20110.5 |
| `gyldig_til` | Tilbuddet gælder til | 2022-12-30 |
| `status` | Status | Tabt |
| `afgjort_dato` | Dato for accept/afslag | 2022-12-16 |
| `tabt_aarsag` | Årsag til tabt tilbud | Pris |

### ordrer

Salgsordrer (hoveder).

31.784 rækker · `03_salg/clean/ordrer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 31445 |
| `system` | System: e-conomic (til 29/2-2024) eller Navi ERP (fra 1/3-2024) | e-conomic |
| `kundenr` | Kundenummer | 10017 |
| `kunde_ref` | Kundens reference (fx indkøbsordre) | PO2098503 |
| `ordredato` | Ordredato | 2022-10-04 |
| `oensket_leveringsdato` | Kundens ønskede leveringsdato | 2022-11-14 |
| `bekraeftet_leveringsdato` | Bekræftet leveringsdato | 2022-11-17 |
| `saelger` | Sælger (brugerid) | URSC |
| `status` | Status | Leveret |
| `annulleret_dato` | Annulleret dato | 2024-03-07 |

### ordrelinjer

Salgsordrelinjer.

73.128 rækker · `03_salg/clean/ordrelinjer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 31100 |
| `linjenr` | Linjenummer | 10 |
| `varenr` | Varenummer | BB-100432 |
| `beskrivelse` | Beskrivelse | Stützfuß |
| `antal` | Antal | 7 |
| `stkpris_dkk` | Stykpris i DKK | 337.96 |
| `linjebeloeb_dkk` | Linjebeløb i DKK | 2365.72 |
| `leveringsdato` | Leveringsdato | 2022-10-31 |

### leveringer

Leverancer (følgesedler).

32.695 rækker · `03_salg/clean/leveringer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `leveringsnr` | Følgeseddelnummer | FS22010899 |
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 31291 |
| `kundenr` | Kundenummer | 10041 |
| `leveringsdato` | Leveringsdato | 2022-10-25 |
| `antal_linjer` | Antal linjer | 2 |
| `vaegt_kg` | Vægt i kg | 117.4 |

### fakturaer

Udgående fakturaer og kreditnotaer.

33.111 rækker · `03_salg/clean/fakturaer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `fakturanr` | Fakturanummer (heltal i e-conomic, FAK-ÅÅ-NNNNN i Navi) | 71038 |
| `system` | System: e-conomic (til 29/2-2024) eller Navi ERP (fra 1/3-2024) | e-conomic |
| `fakturatype` | Faktura eller kreditnota | Faktura |
| `fakturadato` | Fakturadato | 2022-10-27 |
| `forfaldsdato` | Forfaldsdato | 2022-11-26 |
| `kundenr` | Kundenummer | 10009 |
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 31125 |
| `leveringsnr` | Følgeseddelnummer | FS22010930 |
| `valuta` | Valuta | DKK |
| `kurs` | Valutakurs (DKK pr. valutaenhed) | 1.0 |
| `beloeb_ex_moms_valuta` | Beløb ekskl. moms i fakturavaluta | 8681.85 |
| `beloeb_ex_moms_dkk` | Beløb ekskl. moms i DKK | 8681.85 |
| `moms_dkk` | Moms i DKK | 2170.46 |
| `beloeb_inkl_moms_dkk` | Beløb inkl. moms i DKK | 10852.31 |
| `momskode` | Momskode | U25 |
| `krediterer_fakturanr` | Fakturaen en kreditnota krediterer | 72498 |
| `aarsag` | Årsag | Prisdifference iht. aftale |

### fakturalinjer

Linjer på fakturaer og kreditnotaer.

113.682 rækker · `03_salg/clean/fakturalinjer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `fakturanr` | Fakturanummer (heltal i e-conomic, FAK-ÅÅ-NNNNN i Navi) | 71251 |
| `linjenr` | Linjenummer | 3 |
| `varenr` | Varenummer | BB-900001 |
| `tekst` | Tekst | Fragt |
| `antal` | Antal | 1.0 |
| `stkpris_dkk` | Stykpris i DKK | 750.0 |
| `beloeb_dkk` | Beløb i DKK | 750.0 |
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 31538 |
| `ordrelinjenr` | Ordrelinjenummer | 50 |

## 04_produktion – Produktion

### arbejdscentre

Maskiner og arbejdspladser med timesats og kapacitet.

29 rækker · `04_produktion/clean/arbejdscentre.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `arbejdscenter` | Arbejdscenter/maskine | C02 |
| `navn` | Navn | Bearbejdningscenter 2 |
| `maskine` | Maskinmodel | Mazak VCN-700 |
| `afdeling` | Afdeling | CNC |
| `operation` | Operation | CNC |
| `anskaffet_dato` | Anskaffelsesdato | 2017-10-01 |
| `anskaffelsessum_dkk` | Anskaffelsessum | 1890000 |
| `ejerform` | Eje eller leasing | Eje |
| `timesats_2021_dkk` | Timesats 2021 | 790 |
| `kapacitet_timer_dag` | Kapacitet i timer pr. arbejdsdag | 15.0 |

### ruter

Produktionsruter: operationer og standardtider pr. emne.

3.013 rækker · `04_produktion/clean/ruter.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `varenr` | Varenummer | BB-100262 |
| `operation_nr` | Operationsnummer | 10 |
| `operation` | Operation | LASER |
| `arbejdscenter` | Arbejdscenter/maskine | L02 |
| `opstart_min` | Opstillingstid i minutter | 5 |
| `tid_pr_stk_min` | Standardtid pr. stk. i minutter (maskintid) | 0.33 |
| `bemanding` | Antal operatører under operationen | 2.0 |

### produktionsordrer

Produktionsordrer – én pr. ordrelinje, plus omarbejdsordrer.

73.455 rækker · `04_produktion/clean/produktionsordrer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `prodordrenr` | Produktionsordrenummer | PO22090690 |
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 31233 |
| `linjenr` | Linjenummer | 20 |
| `varenr` | Varenummer | BB-100456 |
| `antal` | Antal | 5 |
| `planlagt_start` | Planlagt start | 2022-10-14 |
| `planlagt_slut` | Planlagt slut | 2022-10-19 |
| `faktisk_start` | Faktisk start | 2022-10-12 |
| `faktisk_slut` | Faktisk slut | 2022-11-04 |
| `kasseret_stk` | Kasserede stk. | 0 |
| `laser_arbejdscenter` | Laser brugt (L01/L02) | L02 |
| `lak_farve` | Lakfarve | RAL 9005 |
| `pulver_lot` | Pulverparti (lot-nr.) | PF-2211-8591 |
| `status` | Status | Afsluttet |
| `ordretype` | Produktion eller omarbejde | Produktion |

### maskinstop

Log over maskinstop med årsag og varighed.

8.326 rækker · `04_produktion/clean/maskinstop.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `stopnr` | Stopnummer | MS002776 |
| `arbejdscenter` | Arbejdscenter/maskine | L02 |
| `start` | Start | 2022-11-15 11:04:00 |
| `slut` | Slut | 2022-11-15 11:14:00 |
| `varighed_min` | Varighed i minutter | 10 |
| `aarsag` | Årsag | Nedbrud |
| `beskrivelse` | Beskrivelse af stoppet | Fokuseringsoptik udskiftet |
| `registreret_af` | Registreret af (brugerid) | JEJA |

### oee

OEE pr. maskine og måned (tilgængelighed × ydelse × kvalitet).

593 rækker · `04_produktion/clean/oee.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `maaned` | Måned (ÅÅÅÅ-MM) | 2022-10 |
| `arbejdscenter` | Arbejdscenter/maskine | L02 |
| `planlagt_tid_timer` | Planlagt produktionstid | 224.8 |
| `stoptid_timer` | Stoptid | 79.6 |
| `driftstid_timer` | Driftstid | 145.2 |
| `ideel_tid_timer` | Ideel tid (standardtid for producerede emner) | 116.1 |
| `producerede_stk` | Producerede stk. | 12056 |
| `kasserede_stk` | Kasserede stk. | 396 |
| `tilgaengelighed_pct` | Tilgængelighed | 64.6 |
| `ydelse_pct` | Ydelse (performance) | 80.0 |
| `kvalitet_pct` | Kvalitet (gode/producerede) | 96.7 |
| `oee_pct` | OEE | 50.0 |

### timeregistrering

Timeregistrering for timelønnede: timer pr. dag på produktionsordre eller indirekte aktivitet.

457.831 rækker · `04_produktion/clean/timeregistrering.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `registreringsnr` | Registreringsnummer | 152611 |
| `dato` | Dato | 2022-09-19 |
| `medarbejder_nr` | Medarbejdernummer | 1026 |
| `prodordrenr` | Produktionsordrenummer | PO22080143 |
| `operation` | Operation | SVEJS |
| `arbejdscenter` | Arbejdscenter/maskine | S08 |
| `aktivitet` | Operation eller indirekte aktivitet | LASER |
| `registreringstype` | Direkte (på ordre) eller indirekte | Direkte |
| `timer` | Registrerede timer (kvarte timer) | 1.25 |
| `overtid` | Overarbejde | False |

## 05_kvalitet_kundeservice – Kvalitet og kundeservice

### reklamationer

Afvigelsesrapporter (NCR): kundereklamationer, interne afvigelser og leverandørreklamationer.

920 rækker · `05_kvalitet_kundeservice/clean/reklamationer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `ncr_nr` | NCR-nummer | NCR-22-168 |
| `oprettet_dato` | Oprettet dato | 2022-11-03 |
| `ncr_type` | Kundereklamation, intern afvigelse eller leverandørreklamation | Kundereklamation |
| `kundenr` | Kundenummer | 10019 |
| `kreditornr` | Kreditornummer (leverandør) | 50001 |
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 31336 |
| `leveringsnr` | Følgeseddelnummer | FS22011271 |
| `prodordrenr` | Produktionsordrenummer | PO22090889 |
| `varenr` | Varenummer | BB-100142 |
| `antal_beroert` | Antal berørte stk. | 6 |
| `fejlkategori` | Fejlkategori | Overfladefejl |
| `beskrivelse` | Beskrivelse | Kunde reklamerer over utilstrækkelig san |
| `ansvarlig_afdeling` | Ansvarlig afdeling | LAK |
| `disposition` | Beslutning (kreditnota, omarbejde, omlevering …) | Omarbejde |
| `kreditnota_fakturanr` | Tilhørende kreditnota | 73562 |
| `omkostning_dkk` | Anslået omkostning | 1057.0 |
| `pulver_lot` | Pulverparti (lot-nr.) | PF-2304-2347 |
| `oprettet_af` | Oprettet af (brugerid) | ANHO |
| `omarbejde_prodordrenr` | Omarbejdsordre | PO22110949 |
| `lukket_dato` | Lukket dato | 2022-11-23 |
| `status` | Status | Lukket |

### henvendelser

Kundeservice-log: henvendelser pr. mail og telefon til ordrekontoret.

6.778 rækker · `05_kvalitet_kundeservice/clean/henvendelser.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `henvendelsesnr` | Henvendelsesnummer | H02260 |
| `modtaget_tidspunkt` | Modtaget tidspunkt | 2023-01-10 07:39:00 |
| `kanal` | Mail eller telefon | Mail |
| `kundenr` | Kundenummer | 10001 |
| `kontaktperson` | Kontaktperson | Carl Schmidt |
| `kategori` | Kategori | Leveringstid/status |
| `emne` | Emnelinje | Kan levering af 32770 fremrykkes? |
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 32770 |
| `ncr_nr` | NCR-nummer | NCR-22-183 |
| `behandlet_af` | Behandlet af (brugerid) | KAVE |
| `besvaret_tidspunkt` | Besvaret tidspunkt | 2023-01-10 09:51:00 |
| `loest_dato` | Løst dato | 2023-01-11 |
| `svartid_timer` | Svartid i timer | 2.2 |
| `status` | Status | Løst |

## 06_hr – HR og løn

### medarbejdere

Medarbejdere (nuværende og fratrådte).

143 rækker · `06_hr/clean/medarbejdere.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `medarbejder_nr` | Medarbejdernummer | 1048 |
| `brugerid` | Brugerid (initialer) | DAHA |
| `fornavn` | Fornavn | Danny |
| `efternavn` | Efternavn | Hansen |
| `koen` | Køn | M |
| `foedselsdato` | Fødselsdato | 2000-08-28 |
| `nationalitet` | Nationalitet | DK |
| `adresse` | Adresse | Engvej 101B |
| `postnr` | Postnummer | 8620 |
| `by` | By | Kjellerup |
| `email` | Mail | kave@biksbaks.dk |
| `afdeling` | Afdeling | SVEJ |
| `stilling` | Stilling | Lærling (smed) |
| `loenform` | Lønform | Lærling |
| `ugentlige_timer` | Ugentlige timer | 37 |
| `ansat_dato` | Ansat dato | 2020-10-19 |
| `fratraadt_dato` | Fratrådt dato | 2025-09-19 |
| `fratraedelsesaarsag` | Fratrædelsesårsag | Egen opsigelse |
| `naermeste_leder_nr` | Nærmeste leders medarbejdernummer | 1010 |
| `bank_regnr` | Bankens registreringsnummer (læs som tekst) | 9280 |
| `bank_kontonr` | Bankkontonummer (læs som tekst) | 3442533538 |

### stillingshistorik

Stillinger og arbejdstid over tid pr. medarbejder.

148 rækker · `06_hr/clean/stillingshistorik.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `medarbejder_nr` | Medarbejdernummer | 1046 |
| `fra_dato` | Fra dato | 2019-12-27 |
| `til_dato` | Til dato (tom = fortsat) | 2023-04-07 |
| `afdeling` | Afdeling | SVEJ |
| `stilling` | Stilling | Klejnsmed |
| `ugentlige_timer` | Ugentlige timer | 37 |

### afdelinger

Afdelinger.

10 rækker · `06_hr/clean/afdelinger.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `afdeling` | Afdeling | PLAN |
| `navn` | Navn | Produktionsplanlægning |

### loensedler

Lønsedler: 14-dagesløn for timelønnede, månedsløn for funktionærer.

8.837 rækker · `06_hr/clean/loensedler.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `medarbejder_nr` | Medarbejdernummer | 1046 |
| `loenart` | Lønart | Timeløn 14 dage |
| `periode_fra` | Lønperiode fra | 2022-09-19 |
| `periode_til` | Lønperiode til | 2022-10-02 |
| `udbetalingsdato` | Udbetalingsdato | 2022-10-06 |
| `timer` | Timer | 74.0 |
| `overtidstimer` | Overtidstimer | 3.75 |
| `timeloen_dkk` | Timeløn | 212.06 |
| `bruttoloen_dkk` | Bruttoløn (normaltimer / månedsløn) | 16068.36 |
| `overtidsbetaling_dkk` | Overtidsbetaling | 1221.41 |
| `fritvalg_dkk` | Fritvalgslønkonto | 1901.87 |
| `feriepenge_udbetalt_dkk` | Udbetalte feriepenge | 0.0 |
| `feriepenge_optjent_dkk` | Optjente feriepenge (12,5 %) | 2161.22 |
| `pension_firma_dkk` | Pension, arbejdsgiver | 1383.18 |
| `pension_medarbejder_dkk` | Pension, medarbejder | 691.59 |
| `atp_firma_dkk` | ATP, arbejdsgiver | 94.8 |
| `atp_medarbejder_dkk` | ATP, medarbejder | 47.4 |
| `am_bidrag_dkk` | AM-bidrag | 1476.21 |
| `a_skat_dkk` | A-skat | 5523.0 |
| `nettoloen_dkk` | Nettoløn | 11453.45 |

### fravaer

Fravær: ferie, feriefridage, sygdom, barns sygedag, barsel og kurser.

5.758 rækker · `06_hr/clean/fravaer.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `medarbejder_nr` | Medarbejdernummer | 1034 |
| `fravaerstype` | Fraværstype | Feriefridag |
| `fra_dato` | Fra dato | 2021-12-17 |
| `til_dato` | Til dato (tom = fortsat) | 2021-12-17 |
| `arbejdsdage` | Antal arbejdsdage | 1 |

## 07_trello – Trello

### trello_kort

Trello-kort fra alle boards (fladt udtræk af JSON-eksporten).

360 rækker · `07_trello/clean/trello_kort.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `board` | Trello-board | Produktion – planlægning |
| `kort_id` | Kort-id | 635a5754fafaff6cd707de41 |
| `titel` | Titel | C01 Bearbejdningscenter 1 – nedbrud 27/1 |
| `liste` | Nuværende liste | Løst |
| `oprettet` | Oprettet | 2022-10-27 10:03:00 |
| `deadline` | Deadline | 2023-08-31 |
| `afsluttet` | Afsluttet | False |
| `medlemmer` | Medlemmer | CANO, JEKJ |
| `labels` | Labels | Maskinstop |
| `beskrivelse` | Kortets beskrivelse | Stop kl. 07:58, forventet retur 17/10 16 |

### trello_handlinger

Handlinger på Trello-kort: oprettelse, flytning mellem lister og kommentarer.

984 rækker · `07_trello/clean/trello_handlinger.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `board` | Trello-board | Produktion – planlægning |
| `tidspunkt` | Tidspunkt | 2023-03-27 15:59:00 |
| `bruger` | Bruger (brugerid) | CANO |
| `handling` | Handling | updateCard |
| `kort_id` | Kort-id | 64214b5cf9f964e8c26c2c67 |
| `kort` | Kort | B03 Kantpresse 220 t – nedbrud 27/03 |
| `fra_liste` | Fra liste | Ny |
| `til_liste` | Til liste | Løst |
| `kommentar` | Kommentar | 2024-03: 0,83 % |

## 08_mail – Mail

### mails

Indeks over alle mails i eml/ (én række pr. mail).

4.194 rækker · `08_mail/clean/mails.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `message_id` | Message-ID | <tilbud-01116.2.202211211114@biksbaks.dk |
| `traad_id` | Tråd-id | tilbud-01116 |
| `nr_i_traad` | Nummer i tråden | 2 |
| `tidspunkt` | Tidspunkt | 2022-11-21 11:14:00 |
| `fra` | Afsender | nive@biksbaks.dk |
| `fra_navn` | Afsendernavn | Nils Vestergaard |
| `til` | Modtagere | bent.noergaard@svendsen-og-soen.dk |
| `cc` | Cc | ordre@biksbaks.dk |
| `emne` | Emne | SV: Tilbudsforespørgsel: Sideplade (1001 |
| `sprog` | Sprog | da |
| `type` | Type | tilbud |
| `vedhaeftninger` | Vedhæftninger (filnavne) | Tilbud_7707.pdf |
| `fil` | Sti til .eml-filen | eml/2022/2022-11-21_1114_tilbud-01116_2. |
| `henvendelsesnr` | Henvendelsesnummer | H02245 |
| `kundenr` | Kundenummer | 10021 |
| `ordrenr` | Ordrenummer (heltal i e-conomic, ORD-ÅÅ-NNNNN i Navi) | 32408 |
| `ncr_nr` | NCR-nummer | NCR-22-192 |
| `tilbudsnr` | Tilbudsnummer | 7718 |
| `arbejdscenter` | Arbejdscenter/maskine | L02 |
| `kreditornr` | Kreditornummer (leverandør) | 50052 |

## 09_kpi – KPI

### kpi_maaned

Månedligt KPI-board – indført af direktionen fra juli 2023.

30 rækker · `09_kpi/clean/kpi_maaned.csv`

| Kolonne | Beskrivelse | Eksempel |
|---|---|---|
| `maaned` | Måned (ÅÅÅÅ-MM) | 2024-05 |
| `omsaetning_dkk` | Omsætning | 9912869 |
| `ordreindgang_dkk` | Ordreindgang | 8493331 |
| `antal_ordrer` | Antal ordrer | 547 |
| `leveringspraecision_pct` | Andel ordrer leveret senest bekræftet dato | 71.5 |
| `gns_forsinkelse_arbejdsdage` | Gns. forsinkelse for forsinkede ordrer | 4.0 |
| `kundereklamationer` | Antal kundereklamationer | 3 |
| `reklamationer_pr_100_leveringer` | Kundereklamationer pr. 100 leverancer | 0.48 |
| `kassation_pct` | Kassation i % | 0.89 |
| `oee_laser_pct` | OEE for laserne | 74.6 |
| `kundehenvendelser` | Antal kundehenvendelser | 314 |
| `median_svartid_timer` | Median svartid | 6.2 |
| `dso_dage` | Kredittid (DSO) i dage | 54.5 |
| `antal_ansatte` | Antal ansatte ultimo | 77 |
| `sygefravaer_pct` | Sygefravær i % | 2.4 |

## Øvrige filer

- `01_virksomhed/aarsrapporter/` – offentliggjorte årsrapporter 2021–2025 (Markdown)
- `07_trello/json/` – Trello-eksport (ét JSON-dokument pr. board, Trellos eget format)
- `08_mail/eml/` – mails som .eml-filer (åbnes i Outlook/Thunderbird eller med Pythons `email`-modul)
- `05_kvalitet_kundeservice/raw/` – NCR-log og kundeservice-log som Excel-ark
