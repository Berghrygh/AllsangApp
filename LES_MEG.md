# 🎸 Allsang – sangbok-app for lystig lag

En enkel, frittstående HTML-app for å samle sanger og lage trykkeklare PDF-sangbøker for allsang.

## Filer i denne pakken

- **`Allsang.html`** – selve appen. Åpne i nettleser for å bruke.
- **`sangdatabase.json`** – startdatabase med to eksempler. Du importerer denne én gang for å teste, og bruker den deretter som mal for din egen.
- **`LES_MEG.md`** – denne fila.

## Slik kommer du i gang (første gang)

1. Last begge filene `Allsang.html` og `sangdatabase.json` opp til en mappe på Google Drive (f.eks. `Drive › Allsang/`).
2. På PC: høyreklikk `Allsang.html` i Drive → *Åpne med* → Chrome / Firefox / Safari (eller last den ned og dobbeltklikk).
3. På mobil: åpne Drive-appen, trykk på `Allsang.html`, velg *Åpne i nettleser*. Tips: legg den til på hjem-skjermen for ett-trykks tilgang.
4. I appen: gå til **💾 Data**-fanen → **⬆️ Last opp database** → velg `sangdatabase.json`. Du har nå to eksempelsanger og en eksempel-set-list.

## Daglig bruk

### Legge til en sang
1. **📚 Sanger** → **＋ Ny sang**.
2. Skriv inn artist og tittel.
3. Klikk en av søkeknappene (Google, Ultimate Guitar, Viseboka, osv.) – de åpner søk i ny fane.
4. Marker tekst+besifring på siden du fant, kopier (Ctrl/Cmd+C).
5. Lim inn (Ctrl/Cmd+V) i tekstfeltet i appen.
6. Hak av "Inneholder besifring" hvis det er akkorder over linjene – da brukes monospace-skrift i PDF-en så akkordene treffer riktig sted.
7. Lagre.

### Lage en set-list
1. **🎵 Set-lister** → **＋ Ny set-list**.
2. Gi den et navn (f.eks. *17. mai i hagen 2026*) og evt. beskrivelse.
3. Plukk sanger fra biblioteket til høyre.
4. Bruk ▲ ▼ for å endre rekkefølge, ✕ for å fjerne.
5. Lagre.

### Lage PDF-en
1. Inne i set-listen, eller fra set-list-oversikten, trykk **📄 Lag PDF**.
2. PDF-en lastes ned automatisk og inneholder:
   - Forside med navn og dato
   - Innholdsfortegnelse med sidenummer
   - Hver sang på egen side (lange sanger fortsetter på neste side, aldri to ulike sanger på samme side)
   - Sidenummerering nederst på alle sider
3. Skriv ut, eller last opp til Drive og del lenken med deltakerne.

### Synkronisere mellom enheter

**Alternativ A: GitHub-synk (anbefalt – fullautomatisk)**

Hvis du allerede hoster appen på GitHub Pages, kan du la appen lagre databasen i samme repo:

1. Lag en *Personal Access Token (PAT)* på GitHub:
   - Gå til [github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens)
   - "Generate new token" → velg **Fine-grained personal access token**
   - Repository access: **Only select repositories** → velg ditt allsang-repo
   - Permissions → Repository permissions → **Contents: Read and write**
   - Generer og kopier tokenet (det vises bare én gang!)
2. I appen: gå til **💾 Data** → **🐙 GitHub-synk**.
3. Fyll inn brukernavn, repo-navn, branch (vanligvis `main`), sti (`sangdatabase.json`), og lim inn tokenet.
4. Hak av **Auto-synk** og trykk **💾 Lagre innstillinger**.
5. Trykk **⬇️ Hent fra GitHub** første gang (eller **⬆️ Lagre til GitHub** hvis fila ikke finnes).

Etterpå: hver gang du åpner appen henter den siste versjon fra GitHub, og hver endring lagres automatisk tilbake (3 sekunders forsinkelse for å samle endringer). På en ny enhet er det bare å fylle inn samme brukernavn/repo/token, så er du i gang.

> ⚠️ **Tokenet lagres bare lokalt** i nettleseren. Del det aldri, og IKKE legg det inn i selve repoet (det skal kun limes inn i appens innstillinger).

**Alternativ B: Manuell eksport/import (uten GitHub)**

Hvis du ikke vil bruke GitHub-synk:
1. Etter en arbeidsøkt: **💾 Data** → **⬇️ Last ned database**.
2. Last opp den nye `sangdatabase_yyyy-mm-dd.json` til Google Drive (overskriv den gamle hvis du vil).
3. På annen enhet: åpne `Allsang.html` → **💾 Data** → **⬆️ Last opp database** → velg den nyeste fila.

> 💡 **Anbefalt rutine:** Last ned database etter hver arbeidsøkt som ekstra sikkerhetskopi – også når du bruker GitHub-synk.

## Tekniske notater

- All data ligger i nettleserens **localStorage** mens du jobber. Eksport-fila er den autoritative kopien.
- Appen krever internett for å laste jsPDF (PDF-biblioteket) første gang – nettleseren cacher det etterpå.
- Søkeknappene åpner bare nye nettleserfaner; de henter ikke tekst automatisk (det er for å unngå brudd med tjenestenes vilkår, og fordi mange sider blokkerer automatisk uthenting).
- PDF-en bruker A4 med ca. 5 cm marg og standard fonter. Du kan endre skriftstørrelse i set-list-redigereren.
- Norske spesialtegn (æ ø å) støttes både i appen, JSON-fila og PDF-en.

## Tips

- **Lange tekster:** la "skriftstørrelse" stå på 10–11 pt så får du mer tekst per side.
- **Akkord-låter:** sett alltid hak på "Inneholder besifring" så bevares akkordplasseringen perfekt.
- **Sortering:** sangene sorteres alfabetisk på artist+tittel i biblioteket. Bruk søkefeltet for raskt å finne fram.
- **Sikkerhetskopi:** ta vare på flere generasjoner av JSON-fila – f.eks. `sangdatabase_2026-05-03.json`, `sangdatabase_2026-09-12.json` osv.

Lykke til med allsangen! 🎶
