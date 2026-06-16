# Handleiding: WM Sign website hosten op GitHub Pages

Van Netlify naar GitHub Pages — gratis, zonder creditlimieten.

---

## Wat je nodig hebt

- Een computer met internetverbinding
- Je domeinnaam **wmsign.nl** (toegang tot de DNS-instellingen bij je domeinprovider)
- Circa 20 minuten

---

## Stap 1 — GitHub account aanmaken

1. Ga naar [github.com](https://github.com)
2. Klik op **Sign up**
3. Vul in:
   - Je e-mailadres
   - Een wachtwoord
   - Een gebruikersnaam (bijv. `wmsign` of je eigen naam)
4. Verifieer je e-mailadres via de mail die GitHub stuurt
5. Bij het kiezen van een plan: kies **Free**

---

## Stap 2 — Nieuwe repository aanmaken

Een "repository" is gewoon een map op GitHub waar je websitebestanden in komen.

1. Klik rechtsboven op het **+** icoontje → **New repository**
2. Vul in:
   - **Repository name:** `wmsign-website`
   - **Description:** Website WM Sign (optioneel)
   - Zet op **Public** (verplicht voor gratis GitHub Pages)
3. Laat alle andere opties op standaard staan
4. Klik op **Create repository**

---

## Stap 3 — Personal Access Token aanmaken

Dit is een soort tijdelijk wachtwoord waarmee de bestanden geüpload kunnen worden.

1. Klik rechtsboven op je **profielfoto** → **Settings**
2. Scroll helemaal naar beneden in het linkermenu → klik op **Developer settings**
3. Klik op **Personal access tokens** → **Tokens (classic)**
4. Klik op **Generate new token** → **Generate new token (classic)**
5. Vul in:
   - **Note:** `wmsign deploy`
   - **Expiration:** 90 days (of langer als je wilt)
   - Vink aan: **repo** (het bovenste vakje — dit selecteert alles eronder automatisch)
6. Scroll naar beneden → klik **Generate token**
7. **Kopieer de token** (begint met `ghp_...`) — je ziet hem maar één keer!

Geef deze token aan mij door in de chat, dan upload ik alle bestanden voor je.

---

## Stap 4 — GitHub Pages inschakelen

*(Dit doe je nadat de bestanden zijn geüpload)*

1. Ga naar je repository op GitHub
2. Klik op **Settings** (bovenste tabblad)
3. Klik in het linkermenu op **Pages**
4. Bij **Source**: kies **Deploy from a branch**
5. Bij **Branch**: kies **main** → map **(root)**
6. Klik **Save**

Je site is nu bereikbaar op: `https://jouwgebruikersnaam.github.io/wmsign-website/`

---

## Stap 5 — Eigen domeinnaam koppelen (wmsign.nl)

### In GitHub

1. Ga naar **Settings** → **Pages**
2. Bij **Custom domain**: typ `wmsign.nl`
3. Klik **Save**
4. Laat het vakje **Enforce HTTPS** aangevinkt staan

### Bij je domeinprovider (DNS-instellingen)

Log in bij de partij waar je wmsign.nl hebt gekocht (bijv. TransIP, Antagonist, Versio, GoDaddy, etc.) en pas de DNS-records aan:

**Verwijder of vervang de bestaande A-records en voeg deze toe:**

| Type | Naam | Waarde |
|------|------|--------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | jouwgebruikersnaam.github.io |

> Vervang `jouwgebruikersnaam` door je eigen GitHub gebruikersnaam.

DNS-wijzigingen kunnen tot 24 uur duren om wereldwijd door te voeren. Meestal is het binnen een uur al actief.

---

## Na de migratie

- Je website werkt op `https://wmsign.nl`
- HTTPS (het groene slotje) wordt automatisch ingesteld door GitHub
- Nieuwe bestanden of aanpassingen: geef ze aan mij, ik upload ze

---

## Samenvatting van de stappen

| # | Wat | Wie |
|---|-----|-----|
| 1 | GitHub account aanmaken | Jij |
| 2 | Repository aanmaken | Jij |
| 3 | Personal Access Token aanmaken en delen | Jij |
| 4 | Bestanden uploaden | Claude |
| 5 | GitHub Pages inschakelen | Jij |
| 6 | DNS instellen bij domeinprovider | Jij |

---

*Handleiding gemaakt voor WM Sign — wmsign.nl*
