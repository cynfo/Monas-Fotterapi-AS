# SEO – Hva som ble gjort og hva som gjenstår

## Alt som ble implementert i index.html

### Tittel og meta
| Tag | Verdi |
|-----|-------|
| `<title>` | "Autorisert fotterapeut i Trondheim \| Mona's Fotterapi AS" (55 tegn) |
| `meta description` | 160 tegn med call-to-action ("Bestill time i dag") |
| `meta keywords` | 17 søkeord inkl. kallositeter, forfotsortoser, diabetesføtter, byneset, persaunet |
| `meta robots` | `index, follow, max-image-preview:large` |
| `link canonical` | `https://monasfotterapi.no/` |

### Open Graph (deling på Facebook, LinkedIn m.fl.)
- `og:title`, `og:description`, `og:url`, `og:site_name`, `og:locale`, `og:type`
- `og:image` + `og:image:width/height/alt` — **TODO: se nedenfor**

### Twitter Card
- `twitter:card`, `twitter:title`, `twitter:description`, `twitter:image/alt`

### Favicon
- `<link rel="icon">` og `<link rel="apple-touch-icon">` lagt inn — **TODO: se nedenfor**

### Strukturert data (JSON-LD) — 4 schema-blokker

#### 1. HealthAndBeautyBusiness
Bedriftens fulle profil: navn, beskrivelse, telefon, e-post, adresse (Byneset),
geo-koordinater, åpningstider, begge lokasjoner, bilde-URL, prisklasse og Facebook.

#### 2. Person
Mona som enkeltperson: `jobTitle: "Autorisert fotterapeut"`, beskrivelse og kobling til bedriften.

#### 3. FAQPage
Alle 6 spørsmål/svar fra FAQ-seksjonen. Google kan vise disse direkte i søkeresultatet
som utvidede fragmenter ("rich results"), noe som gir mye mer synlighet.

#### 4. ItemList med 6 × MedicalTherapy
En strukturert liste over alle behandlinger. Gjør det enklere for Google å forstå
hva slags helsetjenester siden tilbyr, og kan utløse rike søkeresultater for spesifikke behandlinger.

### Tilgjengelighet og SEO i HTML-body
- `aria-label` på nav-logo, hamburger, FAQ-knapper og begge "Bestill time"-lenker
- `rel="noopener"` på alle eksterne lenker (sikkerhet + ytelse)
- `title`-attributt på Google Maps-iframe (tilgjengelighet + validering)

---

## TODO – Mona må fylle inn / levere

### 1. Bilde for deling (viktigst!)
Lag et bilde på **1200 × 630 px** av klinikken, logoen eller Mona.
Last det opp som `/og-image.jpg` i rotmappen på serveren.
Dette bildet vises automatisk når noen deler siden på Facebook, LinkedIn osv.

Søk og erstatt `https://monasfotterapi.no/og-image.jpg` med riktig URL hvis
bildet heter noe annet.

### 2. Favicon
Lag to ikoner og legg dem i rotmappen:
- `favicon.png` — 32 × 32 px (nettleser-fane)
- `apple-touch-icon.png` — 180 × 180 px (iOS-hjemskjerm)

Gratis verktøy: https://realfavicongenerator.net/

### 3. Geo-koordinater
JSON-LD-blokken har koordinatene `63.3477, 10.2155` (omtrentlig for Leinstrand-området).
Sjekk eksakt posisjon for Leinstrandvegen 181 i Google Maps og oppdater om nødvendig:
```json
"geo": {
  "@type": "GeoCoordinates",
  "latitude": "SJEKK_OG_OPPDATER",
  "longitude": "SJEKK_OG_OPPDATER"
}
```

### 4. Prisklasse
I JSON-LD-bedrifts-schemaet er `"priceRange": "kr 200–800"` lagt inn som estimat.
Oppdater med ekte prisintervall basert på Monas prisliste.

---

## Neste steg for å maksimere lokal SEO

### Viktigst av alt: Google Business Profile
Dette er det enkeltsteget som gir størst lokal synlighet.

1. Gå til https://business.google.com
2. Søk på "Mona's Fotterapi AS"
3. Krev eierskap (eller opprett ny profil)
4. Fyll ut:
   - Navn, adresse, telefon (identisk med det på nettsiden!)
   - Åpningstider
   - Kategori: "Fotpleier" eller "Helseklinikk"
   - Last opp bilder av klinikken
   - Legg inn nettsidens URL
5. Verifiser med postkort eller telefonkode

**Resultat:** Bedriften dukker opp i Google Maps og i "lokalboks" (kartet over søkeresultatene)
ved søk som "fotterapeut trondheim" og "fotpleie nær meg". Dette er gull for lokal synlighet.

### Google Search Console
1. Gå til https://search.google.com/search-console/
2. Legg til domenet `monasfotterapi.no`
3. Verifiser eierskap (via DNS-record hos domeneregistrator)
4. Send inn sitemapen: `https://monasfotterapi.no/sitemap.xml`
5. Her kan du følge med på hvilke søkeord siden vises for og eventuelle tekniske feil

### Tilbakekoblinger (lenkebygging)
- Be om lenke fra Norsk Fotterapeuters Forbund (NFF) hvis Mona er medlem
- Be om lenke fra lokale helserelaterte kataloger (finn.no bedriftsside, 1881.no)
- Bli omtalt i lokale Trondheim-blogger eller -aviser

---

## Verifiser at alt er riktig

Test schema-markup på: https://search.google.com/test/rich-results
Test Open Graph-deling på: https://developers.facebook.com/tools/debug/
Test meta-tags på: https://metatags.io/

Siden ser **identisk ut visuelt** som før – alt SEO-arbeid ligger i `<head>`,
i JSON-LD-script-blokker og i aria/title-attributter på eksisterende HTML-elementer.
Ingen synlig tekst er endret utover Monas egne tekstønsker.
