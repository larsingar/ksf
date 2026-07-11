# Koppang Sportsfiskere — nettside

Statisk nettside for Koppang Sportsfiskere. Én enkelt HTML-fil, ingen PHP, ingen database, ingen byggesteg. Kan hostes gratis.

## Filer

| Fil / mappe | Hva det er |
|---|---|
| `index.html` | Selve nettsiden (alt av HTML, CSS og JS ligger i denne ene fila) |
| `assets/logo.jpg` | Foreningens logo (brukt i meny, hero og favicon) |
| `.nojekyll` | Slår av GitHub sin Jekyll-prosessering (vi serverer ren HTML) |

## Slik ser du siden lokalt

Dobbeltklikk `index.html`, eller kjør en liten lokal server (anbefalt — Facebook-feeden trenger `http`, ikke `file://`):

```bash
cd ~/Code/ksf
python3 -m http.server 8000
```

Åpne så <http://localhost:8000>.

## Slik publiserer du med GitHub Pages (gratis)

1. Opprett et nytt, **offentlig** repo på <https://github.com/new> (f.eks. `ksf-nettside`).
2. Koble den lokale mappa til repoet og push:
   ```bash
   cd ~/Code/ksf
   git remote add origin https://github.com/<brukernavn>/<repo>.git
   git push -u origin main
   ```
3. På GitHub: **Settings → Pages**. Under *Build and deployment*:
   - **Source:** Deploy from a branch
   - **Branch:** `main` / `/ (root)` → **Save**
4. Etter et par minutter er siden live på `https://<brukernavn>.github.io/<repo>/`.
   HTTPS ordnes automatisk — da fungerer også Facebook-feeden.

## Koble til eget domene (koppangsportsfiskere.no)

Når siden er verifisert på `.github.io`-adressen:

1. GitHub: **Settings → Pages → Custom domain** → skriv `koppangsportsfiskere.no` → **Save**.
   (Dette lager en `CNAME`-fil i repoet automatisk.)
2. Hos domeneforhandleren, sett DNS:
   - `A`-records for rot-domenet mot GitHub sine IP-er:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` for `www` mot `<brukernavn>.github.io`
3. Kryss av for **Enforce HTTPS** i Pages-innstillingene når sertifikatet er klart.

## Oppdatere innhold senere

Rediger `index.html` (tekst, priser, bilder) og push endringen — GitHub Pages oppdaterer siden automatisk innen et par minutter. Enkle tekstendringer kan også gjøres rett i GitHub sitt web-grensesnitt.
