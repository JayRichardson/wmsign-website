# Master Prompt: Website bouwen vanuit Instagram

Herbruikbaar stappenplan + prompt voor het bouwen van een professionele bedrijfswebsite,  
gebaseerd op een Instagram-pagina en een logo.

**Input:** logo-bestand (PNG/SVG/PDF) + Instagram-link  
**Output:** complete HTML-website + deploymenthandleiding

---

## Stappenplan (voor de begeleider)

### Stap 1 — Voorbereiding: input verzamelen
Vraag de ondernemer om:
- Het logo-bestand (PNG met transparantie heeft voorkeur; PDF of SVG ook goed)
- De link naar hun Instagram-pagina (`https://www.instagram.com/[naam]/`)
- Eventueel: telefoonnummer, e-mailadres, KvK-locatie (als dat niet op Instagram staat)

---

### Stap 2 — Instagram-analyse
Claude opent de Instagram-pagina en haalt op:
- **Diensten / producten** — wat biedt het bedrijf aan? (uit posts + bio)
- **Werkgebied** — stad of regio (uit bio of posts)
- **Merkstijl** — kleurpalet, tone-of-voice, formeel vs. informeel
- **Foto's** — minimaal 6–10 representatieve werkfoto's (screenshots of directe URL's)
- **Contactinfo** — telefoonnummer, e-mail, website (als die al bestaat)
- **Bio-tekst** — slogan, USP's, jaren ervaring

---

### Stap 3 — Website bouwen
Claude bouwt één `index.html`-bestand met:

#### Structuur
- **Hero-sectie** — logo, headline, subheadline, CTA-knop ("Vraag een offerte aan")
- **Over ons** — kort, op basis van bio + posts
- **Diensten** — kaarten per service (uit Instagram-analyse)
- **Werkgebied** — stad/regio + eventueel "door heel Nederland"
- **Fotogalerij** — grid met werkfoto's
- **Offerte-formulier** — naam, telefoon, soort dienst (dropdown), bericht, verzendknop
- **Footer** — contactinfo, links naar Instagram/WhatsApp, copyright

#### Technisch
- Volledig responsive (mobiel-first)
- Kleurpalet afgeleid van logo + Instagram-stijl
- Google Fonts passend bij de branche
- `<meta>` SEO-tags (title, description, canonical)
- Open Graph tags (WhatsApp/social preview)
- Structured data: `LocalBusiness` + `FAQPage` (schema.org JSON-LD)
- Formulier gemarkeerd als `data-netlify="true"` (Netlify Forms)
- Smooth scroll, hover-effecten, CSS transitions

#### Ondersteunende bestanden
- `sitemap.xml` — voor Google-indexering
- `robots.txt` — standaard permissief

---

### Stap 4 — Review & aanpassingen
Laat de ondernemer de website bekijken (als lokaal HTML-bestand of screenshot).  
Pas kleuren, teksten of diensten aan op basis van feedback.

---

### Stap 5 — Live zetten
Gebruik de deploymenthandleiding (zie sectie hieronder):
1. Netlify — gratis hosting via drag & drop
2. Antagonist — `.nl` domeinnaam (~€12/jaar)
3. DNS koppelen (nameservers van Netlify invullen bij Antagonist)
4. HTTPS automatisch activeren
5. Formulier-notificaties instellen (e-mail bij offerteaanvraag)

---

## Master Prompt (kopieer dit naar Claude)

Plak onderstaande prompt in een nieuw gesprek met Claude, voeg het logo toe als bijlage, en stuur mee.

---

```
Je gaat een professionele, SEO-geoptimaliseerde bedrijfswebsite bouwen voor een ondernemer.

**Input:**
- Logo: [bijgevoegd bestand]
- Instagram: [VUL HIER DE INSTAGRAM-LINK IN]

---

**Stap 1 — Analyseer Instagram**

Open de Instagram-pagina en verzamel:
- Alle diensten/producten die het bedrijf aanbiedt
- Vestigingsplaats / werkgebied
- Slogan, USP's en tone-of-voice (formeel of informeel?)
- Kleurpalet en visuele stijl
- Minimaal 6 foto's van het werk (gebruik de directe URL's van Instagram-afbeeldingen)
- Contactgegevens (telefoon, e-mail, WhatsApp indien zichtbaar)

Als informatie ontbreekt op Instagram, vraag er dan kort naar.

---

**Stap 2 — Bouw de website**

Maak één bestand: `index.html`. Geen externe CSS- of JS-bestanden — alles inline.

Verplichte secties:
1. **Navigatiebalk** — logo links, menu-items rechts (Over ons, Diensten, Galerij, Contact), hamburger-menu op mobiel
2. **Hero** — grote headline met de kernbelofte van het bedrijf, subheadline, twee knoppen: "Offerte aanvragen" (anker naar formulier) en "Bekijk ons werk" (anker naar galerij)
3. **Over ons** — 2–3 zinnen over het bedrijf, op basis van Instagram-bio en posts
4. **Diensten** — kaarten (minimaal 4), elke kaart heeft een icoon (emoji of SVG), titel en korte beschrijving
5. **Werkgebied** — kaart-achtige weergave of tekst: stad + "door heel [land]"
6. **Fotogalerij** — CSS grid, 3 kolommen desktop / 2 kolommen mobiel / 1 kolom klein scherm, foto's met hover-effect
7. **FAQ** — minimaal 4 veelgestelde vragen over het bedrijf/dienst
8. **Offerte-formulier** — velden: naam (tekst), telefoon (tel), dienst (select met opties), bericht (textarea), verzendknop; formulier-attribuut: `data-netlify="true" name="offerte"`
9. **Footer** — adres/stad, e-mail, telefoon, Instagram-link, WhatsApp-link, copyright

Technische vereisten:
- Volledig responsive, mobiel-first
- Kleurpalet gebaseerd op logo en Instagram-stijl (minimaal primary + accent + neutraal)
- Google Font passend bij de branche (importeer via `<link>`)
- Smooth scroll: `html { scroll-behavior: smooth; }`
- CSS variabelen voor kleuren: `--color-primary`, `--color-accent`, etc.
- Meta-tags: title, description (max 155 tekens), canonical URL (gebruik `https://[domeinnaam].nl/`)
- Open Graph tags: og:title, og:description, og:image (gebruik eerste werkfoto als og:image), og:url, og:locale
- JSON-LD structured data: `LocalBusiness` (naam, beschrijving, url, telephone, address, sameAs met Instagram) + `FAQPage`
- Netlify Forms: `<form name="offerte" method="POST" data-netlify="true">`

---

**Stap 3 — Maak ondersteunende bestanden**

Maak ook:
- `sitemap.xml` — met de homepage-URL en vandaag als lastmod-datum
- `robots.txt` — standaard: `User-agent: * / Allow: /` + verwijzing naar sitemap

---

**Stap 4 — Deploymenthandleiding**

Schrijf een bestand `handleiding-live-zetten.md` met stap-voor-stap instructies voor:
1. Gratis account aanmaken op Netlify
2. Bestanden uploaden via drag & drop
3. Domeinnaam kopen bij Antagonist (of TransIP als alternatief)
4. DNS koppelen: nameservers van Netlify invullen bij de domeinnaam-registrar
5. HTTPS activeren in Netlify
6. E-mailnotificaties instellen voor het offerte-formulier (ga naar: Site → Forms → [formuliernaam] → Form notifications)

Schrijf de handleiding in eenvoudig Nederlands, alsof je het uitlegt aan iemand die dit voor het eerst doet.

---

**Stijlrichtlijnen:**
- Gebruik de dominante kleur van het logo als `--color-primary`
- Kies een accentkleur die goed combineert (contrastverhouding minimaal 4.5:1 op wit)
- Houd koppen krachtig en actiegericht ("Jouw auto in een nieuw jasje" i.p.v. "Onze diensten")
- Gebruik dezelfde tone-of-voice als op Instagram (check of het bedrijf "je" of "u" gebruikt)
- Voeg geen nepreviews of -beoordelingen toe tenzij de ondernemer die aanlevert

Lever alle bestanden op zodra ze klaar zijn.
```

---

## Checklist vóór oplevering

- [ ] Alle teksten gebaseerd op echte Instagram-content (geen verzonnen info)
- [ ] Logo correct weergegeven (niet uitgerekt, juiste achtergrond)
- [ ] Telefoonnummer en e-mailadres correct
- [ ] Formulier heeft `data-netlify="true"` attribuut
- [ ] Open Graph afbeelding ingesteld (og:image)
- [ ] Sitemap.xml aanwezig met juiste domeinnaam
- [ ] Handleiding geschreven met correcte e-mailadres voor formuliernotificaties
- [ ] Getest op mobiel (responsive)
- [ ] Getest of alle ankerkoppelingen werken (#diensten, #contact, etc.)

---

## Tips voor beste resultaat

**Logo-formaat:** PNG met transparantie werkt het best. Als het bedrijf alleen een JPEG of PDF heeft, vraag Claude dan om het logo te plaatsen op een witte of gekleurde achtergrond die past bij het ontwerp.

**Instagram-toegang:** Sommige Instagram-pagina's blokkeren automatisch scrapen. Als Claude de pagina niet kan openen, vraag de ondernemer om een screenshot van hun bio + 6–10 posts te sturen, of vraag ze de Instagram-posts handmatig te beschrijven.

**Fotokwaliteit:** Instagram-foto's zijn gecomprimeerd. Voor de definitieve website is het beter om de originele foto's te gebruiken. Vraag de ondernemer om hun beste werkfoto's te sturen (WhatsApp-kwaliteit is prima voor een website).

**Domeinnaam:** Check eerst of `[bedrijfsnaam].nl` beschikbaar is via [antagonist.nl](https://www.antagonist.nl) voordat je die naam in de website-code verwerkt.

**Tijd die het kost:** Met dit proces duurt het bouwen van de website gemiddeld 20–40 minuten. Live zetten (hosting + domein koppelen) duurt nog eens 30–60 minuten, inclusief DNS-propagatie.
