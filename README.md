# Takenbundelaar

De Takenbundelaar zet een zip met ingediende taken om in één PDF die je makkelijk kunt nakijken, afdrukken of bewaren. De PDF is alfabetisch gesorteerd per leerling, en de naam van de leerling staat onderaan elke pagina.

## Wat doet de Takenbundelaar?

### Wat heb je nodig?
Een zip-bestand met één map per leerling. De naam van de map is de naam van de leerling. In elke map zitten de bestanden die die leerling heeft ingediend. Dit is de structuur die je krijgt als je ingediende taken downloadt uit bijvoorbeeld Smartschool.

De leerlingmappen mogen ook per klas gegroepeerd zijn:

```
3A
├── Antoons Aliena
└── Bellen Warre
3B
├── Bollen Isbel
└── Cakar Julie
```

De tool herkent dat klasniveau automatisch.

### Wat gebeurt er?
1. **De zip wordt uitgepakt** in je browser.
2. **De leerlingen worden alfabetisch gesorteerd** op mapnaam. Staan de leerlingen per klas in mappen, dan wordt eerst per klas en daarna per leerling gesorteerd. Hoofdletters tellen niet mee, dus "de Mooij" staat gewoon tussen de andere namen met D.
3. **Elk bestand wordt omgezet naar PDF-pagina's:**
   - Word-documenten (.docx) worden pagina per pagina omgezet, inclusief afbeeldingen en schermafdrukken.
   - PDF-bestanden worden ongewijzigd overgenomen.
   - Afbeeldingen (.jpg, .png) krijgen elk een eigen pagina.
4. **Onderaan elke pagina komt de naam van de leerling**, eventueel met een paginanummer per leerling (bv. "Peeters Jan — 1/2"). Bij een zip met klasmappen staat de klas ervoor (bv. "3A — Peeters Jan — 1/2").
5. **Alles wordt samengevoegd tot één PDF**, die je met de knop "PDF bewaren" downloadt.

Heeft een leerling meer dan één bestand ingediend, dan staan die allemaal na elkaar onder zijn of haar naam.

### Wat zie je tijdens het verwerken?
Een lijst met alle leerlingen en hun bestanden. Per leerling zie je hoeveel pagina's er zijn toegevoegd. Bestanden die niet konden worden verwerkt, worden apart vermeld, zodat je die zelf kunt openen.

### Wat werkt niet?
- Oudere Word-bestanden (.doc) en OpenOffice/LibreOffice-bestanden (.odt) worden overgeslagen.
- Word-pagina's worden als afbeelding in de PDF gezet. De tekst is dus niet selecteerbaar en de opmaak kan licht afwijken van wat je in Word ziet.
- Erg lange Word-documenten worden in A4-stukken geknipt.

## Privacy en gegevens

**Worden taken van leerlingen ergens naartoe gestuurd?**
Nee. De zip wordt volledig in je eigen browser verwerkt en verlaat je computer niet.

**Wordt er iets opgeslagen?**
Nee. Er is geen database, er zijn geen cookies en er worden geen gegevens bewaard. Na het sluiten van de pagina is alles weg. Alleen de PDF die je zelf downloadt, blijft op je computer staan.

**Wordt er AI gebruikt of contact gemaakt met Claude?**
Nee. Het is een gewoon script, zonder API-calls.

**Welke externe diensten worden gebruikt?**
Alleen GitHub Pages, om de pagina zelf te tonen. Alle bibliotheken zitten in deze repository (map `vendor`), dus er worden geen CDN's of Google Fonts geladen.

**Wat ziet GitHub?**
Zoals elke webhost ziet GitHub technische bezoekgegevens, zoals het IP-adres. Het ziet geen bestanden of namen van leerlingen.

**Hoe kan ik dit zelf controleren?**
De code staat openbaar in `index.html`. Open in je browser de ontwikkelaarstools (F12), ga naar het tabblad **Netwerk** en verwerk een zip: je ziet dat er tijdens het verwerken niets wordt verstuurd.

## Online zetten via GitHub Pages

1. Maak een (gratis) account op <https://github.com>.
2. Klik rechtsboven op **+** → **New repository**. Geef het de naam `takenbundelaar`, kies **Public**, laat *Add .gitignore* op **None** staan en klik op **Create repository**.
3. Klik op **uploading an existing file** en sleep de **inhoud** van deze map erin (`index.html`, `README.md`, `.nojekyll` en de map `vendor`). Klik op **Commit changes**.
4. Ga naar **Settings** → **Pages**. Kies bij *Source* **Deploy from a branch**, kies de branch **main** en de map **/ (root)**, en klik op **Save**.
5. Na een paar minuten staat de tool online op:
   `https://<jouw-gebruikersnaam>.github.io/takenbundelaar/`

Die link kun je met iedereen delen. Je collega's hebben geen account nodig.

> Het bestand `.nojekyll` is op sommige computers verborgen. Ontbreekt het, dan werkt de site meestal ook, maar het is veiliger om het mee te uploaden.

## Lokaal gebruiken zonder internet

Open `index.html` via een kleine lokale webserver, bijvoorbeeld:

```bash
python -m http.server 8000
```

en ga naar <http://localhost:8000>.

## Bestanden

```
index.html   De volledige tool (HTML, CSS en JavaScript)
vendor/      Meegeleverde open-source bibliotheken
```

Bibliotheken: JSZip, docx-preview, html2canvas, UTIF.js, pako en pdf-lib (allemaal open source, MIT- of vergelijkbare licentie).
