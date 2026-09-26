# Podnica

**Cena ispod koje ne ideš.**

Kalkulator cene projekta za freelancere i male biznise. Uneseš sate, troškove i kakav je klijent — dobiješ tri cene: **podnicu** (minimum), **fer cenu** i **premium**, sa razlaganjem kako je svaka izračunata.

Deo Trosku 30-day challenge serije — aplikacija živi 24 sata na Netlify-u, pa se briše.

## Šta je drugačije

Računa ono što niko ne računa:

- **Nevidljivi sati** — sastanci, mejlovi, revizije, čekanje materijala, administracija (+46% na osnovne sate, sve se može menjati)
- **Rizik od klijenta** — osam crvenih zastavica (nema brief, "što pre" rok, neće avans...), svaka nosi procenat koji ulazi u cenu
- **Šta ti radi popust** — slajder koji pokazuje pad profita, ne pad cene
- **Rečenica za klijenta** — gotova ponuda koja se kopira jednim dugmetom

## Struktura

```
index.html   ← cela aplikacija (HTML + CSS + JS, ~60 KB)
README.md
```

Jedan fajl, nula zavisnosti osim Google Fonts. Bez baze, login-a, API poziva i analytics-a. Satnica korisnika ostaje u localStorage i nikad ne napušta uređaj.

## Pokretanje

Najjednostavnije — otvori fajl direktno u browseru:

```bash
open index.html
```

Ili preko lokalnog servera (preporučeno, ponaša se identično produkciji):

```bash
# Python (ugrađen na macOS)
python3 -m http.server 8000
# → http://localhost:8000

# ili Node
npx serve .
# → http://localhost:3000
```

## Deploy na Netlify

Drag-and-drop `index.html` (ili ceo folder) na [app.netlify.com/drop](https://app.netlify.com/drop) — ili preko CLI-ja:

```bash
npx netlify-cli deploy --prod --dir .
```

## Podešavanja

Sve konstante su u `CONFIG` objektu na vrhu `<script>` bloka u `index.html`, pod komentarom **"MENJAJ SAMO OVDE"**:

- marža (25%), premium faktor (×1,4), prag upozorenja rizika (60%)
- procenti nevidljivih sati i crvenih zastavica
- **prosečna neto plata** (RZS 2025, okvirno 109.000 din) i **kurs** (NBS, ~117,2 din/€) — proveri i ažuriraj pre objave

## Testiranje

Ručno kroz tok, ili headless (potreban Chrome/Brave + `puppeteer-core`):

```bash
npm install puppeteer-core
node podnica_e2e.js   # ako sačuvaš E2E skriptu iz razvoja
```

Provereno: ceo tok na 390×844 bez horizontalnog skrola, nula grešaka u konzoli, matematika, konverzija valuta, localStorage, slika za deljenje 1080×1350.
# PODNICA
