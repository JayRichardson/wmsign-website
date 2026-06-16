# Handleiding: WM Sign website live brengen

Je website is al klaar (index.html + fotos + logo). Je hebt twee dingen nodig om live te gaan:

1. **Hosting** — een server die jouw bestanden online zet
2. **Domeinnaam** — jouw webadres (bijv. `wmsign.nl`)

---

## Aanbevolen aanpak: Netlify + Antagonist

- **Netlify** → gratis hosting, eenvoudig uploaden via drag & drop
- **Antagonist** → Nederlandse registrar voor je .nl domeinnaam (~€12/jaar)

---

## Stap 1 — Maak een gratis Netlify-account aan

1. Ga naar [netlify.com](https://netlify.com) en klik op **Sign up**
2. Kies **Sign up with email** en maak een account aan
3. Je hoeft geen creditcard in te voeren

---

## Stap 2 — Upload je website naar Netlify

1. Log in op Netlify en ga naar het **dashboard**
2. Scroll helemaal naar beneden — je ziet een grijs vlak:
   > *"Want to deploy a new site without connecting to Git? Drag and drop your site output folder here"*
3. Open Finder en ga naar de map **WM Sign** (jouw projectmap)
4. Selecteer alle bestanden: `index.html`, `wmsign_logo.png` en de map `fotos`
5. Sleep alles naar het grijze vlak in Netlify
6. Netlify geeft je direct een tijdelijk adres zoals `random-name-123.netlify.app` — je site is nu online!

---

## Stap 3 — Koop een domeinnaam

1. Ga naar [antagonist.nl](https://www.antagonist.nl) en zoek op `wmsign.nl` (of een andere naam)
2. Voeg de domeinnaam toe aan je winkelwagen en reken af
3. Na betaling krijg je toegang tot het **DNS-beheer** van jouw domein

---

## Stap 4 — Koppel je domeinnaam aan Netlify

Dit is de stap waarbij je jouw domeinnaam (gekocht bij Antagonist) verbindt met jouw site op Netlify. Je doet dit door Netlify te vertellen dat jij de eigenaar bent van het domein, en Antagonist te vertellen dat Netlify de site mag hosten.

### 4a — Domein toevoegen in Netlify

1. Log in op [netlify.com](https://netlify.com)
2. Klik op jouw site in het dashboard (de naam die Netlify automatisch heeft gegeven)
3. Ga naar het tabblad **Domain management** (bovenin de sitepagina)
4. Klik op de knop **Add a domain**
5. Typ `wmsign.nl` in het veld en klik op **Verify**
6. Netlify vraagt of jij de eigenaar bent — klik op **Yes, add domain**
7. Je ziet nu `wmsign.nl` in de lijst staan, maar nog met een oranje waarschuwing. Dat is normaal — we lossen dat op in de volgende stap.

### 4b — Nameservers kopiëren uit Netlify

Netlify beheert jouw DNS het liefst zelf. Daarvoor geeft het je eigen nameservers.

1. Scroll op dezelfde pagina omlaag naar het blok **Netlify DNS**
2. Klik op **Activate Netlify DNS for wmsign.nl**
3. Netlify toont je 4 nameservers, die er ongeveer zo uitzien:
   ```
   dns1.p01.nsone.net
   dns2.p01.nsone.net
   dns3.p01.nsone.net
   dns4.p01.nsone.net
   ```
4. Kopieer alle vier de regels (of laat dit tabblad open staan)

### 4c — Nameservers instellen in Antagonist

Nu vertel je Antagonist dat Netlify voortaan het domein beheert.

1. Ga naar [antagonist.nl](https://www.antagonist.nl) en log in
2. Klik bovenin op **Mijn account** → **Domeinen**
3. Klik op `wmsign.nl` in de lijst
4. Zoek de sectie **Nameservers** of **DNS-instellingen** en klik op **Wijzigen**
5. Je ziet standaard de nameservers van Antagonist staan — verwijder die
6. Vul de 4 Netlify nameservers in die je net gekopieerd hebt
7. Klik op **Opslaan**

> **Wacht even:** het kan 1 tot 24 uur duren voordat de wijziging wereldwijd actief is. Meestal gaat dit binnen 1–2 uur. Je kunt de voortgang checken op [dnschecker.org](https://dnschecker.org) — zoek op `wmsign.nl` en kijk of de nameservers al naar Netlify wijzen.

---

## Stap 5 — HTTPS inschakelen (gratis)

Als de domeinnaam actief is, zorgt Netlify automatisch voor een beveiligde verbinding (het groene slotje in de browser). Je hoeft hier bijna niets voor te doen.

1. Ga in Netlify naar jouw site → **Domain management**
2. Scroll omlaag naar het blok **HTTPS**
3. Als het goed is zie je de melding: *"Your site has HTTPS enabled"* — dan ben je klaar.
4. Staat er nog een knop **Verify DNS configuration**? Klik daarop. Daarna verschijnt **Provision certificate** — klik ook daarop.
5. Even wachten (paar minuten) en je site is bereikbaar via `https://wmsign.nl`

> Als de knop nog grijs is, is het domein nog niet volledig overgezet. Wacht nog even en ververs de pagina.

---

## Stap 6 — Formulier activeren in Netlify

Het formulier op de website is al klaargemaakt voor **Netlify Forms** — je hoeft de code niet aan te passen. Netlify detecteert het formulier automatisch zodra je de site uploadt.

### 6a — Controleer of het formulier herkend is

1. Ga in Netlify naar jouw site
2. Klik op het tabblad **Forms** (bovenin)
3. Je ziet hier het formulier **"offerte"** staan met het aantal inzendingen
4. Staat er niets? Dan is de upload nog niet verwerkt — wacht even en ververs de pagina

### 6b — E-mailmelding instellen

Zodat jij een berichtje krijgt bij elke nieuwe offerteaanvraag:

1. Klik op het formulier **"offerte"** in de lijst
2. Klik rechtsboven op **Form notifications**
3. Klik op **Add notification** → kies **Email notification**
4. Vul bij **Email to notify** in: `wm_sign@hotmail.com`
5. Laat de rest op de standaardinstellingen staan
6. Klik op **Save**

Vanaf nu krijg jij een e-mail op Hotmail zodra iemand het formulier invult, met daarin alle ingevulde gegevens (naam, telefoonnummer, soort dienst, etc.). Gratis tot 100 inzendingen per maand.

---

## Klaar!

Je website is live op `wmsign.nl`. Bezoekers worden automatisch doorgestuurd van `www.wmsign.nl` naar `wmsign.nl`.

**Later aanpassingen maken?**
Bewerk je bestanden lokaal → ga naar Netlify → **Deploys** → sleep je bijgewerkte bestanden opnieuw naar het upload-vlak.

---

### Alternatieven (als je liever iets anders gebruikt)

| Optie | Kosten | Moeilijkheidsgraad |
|---|---|---|
| Netlify (aanbevolen) | Gratis hosting | Makkelijk |
| GitHub Pages | Gratis | Technischer |
| Hostinger | ~€3/maand (incl. domein) | Makkelijk |
| TransIP | ~€3/maand (NL-gebaseerd) | Gemiddeld |
