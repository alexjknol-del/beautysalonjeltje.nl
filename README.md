# Beautysalon Jeltje — beautysalonjeltje.nl

Statische website (platte HTML/CSS, geen build-stap nodig). Klaar om te hosten op Cloudflare Pages via GitHub.

## Structuur

- `index.html`, `over.html`, `redactie.html`, `contact.html`, `privacybeleid.html`, `cookiebeleid.html`
- `behandelingen/` — overzicht + 9 pagina's per behandeling
- `nieuws/` — overzicht + 4 nieuwsartikelen
- `assets/css/style.css`, `assets/img/` — stijl en illustraties
- `.github/workflows/deploy.yml` — GitHub Actions workflow die bij elke push naar `main` automatisch naar Cloudflare Pages deployt

## Eenmalig instellen

1. **GitHub repo**: maak een lege repository aan (bijv. `beautysalonjeltje`) en push deze map naar de `main`-branch.
2. **Cloudflare Pages project**: maak in het Cloudflare dashboard een Pages-project aan met de naam `beautysalonjeltje` (moet overeenkomen met `projectName` in `.github/workflows/deploy.yml`).
3. **GitHub secrets**: voeg in de repo-instellingen (Settings → Secrets and variables → Actions) twee secrets toe:
   - `CLOUDFLARE_API_TOKEN` — een Cloudflare API-token met de rechten "Cloudflare Pages: Edit"
   - `CLOUDFLARE_ACCOUNT_ID` — het Cloudflare account-ID
4. **Custom domain**: koppel `beautysalonjeltje.nl` aan het Cloudflare Pages-project via het dashboard (Pages-project → Custom domains). Zorg dat de domeinnaam als zone in hetzelfde Cloudflare-account staat, of wijzig de nameservers naar Cloudflare.
5. Push naar `main` → de GitHub Action deployt automatisch.

## Analytics (optioneel)

De privacy- en cookiepagina's gaan uit van Cloudflare Web Analytics (cookieloos). Voeg dit toe via Cloudflare dashboard → Pages-project → Analytics → "Enable Web Analytics", dit voegt automatisch een script toe zonder dat de code hier hoeft te wijzigen.

## Google Search Console

1. Voeg het domein toe als property in Google Search Console.
2. Verifieer eigendom via de DNS-TXT-record methode (aan te maken bij de DNS-instellingen van de zone in Cloudflare).
3. Dien na verificatie de sitemap in: `https://beautysalonjeltje.nl/sitemap.xml`.
4. Vraag via "URL-inspectie" indexering van de homepage aan.

## Gemaakte keuzes rond concurrentie

Bij het samenstellen van dit platform is expliciet gelet op het niet uitlichten van concurrenten van de drie aangeleverde partners (Tattoo No More, De Browerij, Body Sculpting Concept):

- **Botox & fillers**: twee eerder onderzochte kandidaten (The Body Clinic, Joost Kroon) bleken ook tattoo-/PMU-laserverwijdering aan te bieden en zijn daarom niet gebruikt. In plaats daarvan is Gaaf Injectables (Den Haag) uitgelicht, geverifieerd zonder overlap met tattoo- of PMU-verwijdering.
- **Bodysculpting & cellulite**: een aanvankelijk overwogen tweede consumentenkliniek (Next Fatfreeze Clinics) is niet gebruikt om overlap met Body Sculpting Concept te vermijden. Deze pagina behandelt de technieken generiek voor consumenten en licht Body Sculpting Concept uitsluitend uit als leverancier voor salons/professionals, niet als consumentenoptie.
