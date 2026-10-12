---
date: '2026-10-12'
description: Leer hoe je QR uit PDF kunt extraheren in Java met GroupDocs.Parser en
  de barcode-gegevens kunt exporteren naar XML voor downstream verwerking.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Leer hoe je QR uit PDF kunt extraheren in Java met GroupDocs.Parser
  en de barcode-gegevens kunt exporteren naar XML voor downstream verwerking.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Hoe QR uit PDF te extraheren in Java met GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: Hoe QR uit PDF te extraheren in Java met GroupDocs.Parser
type: docs
url: /nl/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Hoe QR uit PDF te extraheren in Java met GroupDocs.Parser

In moderne bedrijfsprocessen kan **het extraheren van QR uit PDF**-bestanden een handmatige gegevensinvoerknelpunt omzetten in een volledig geautomatiseerde pijplijn. Of u nu verzendingsmanifesten, kassabonnen of productcatalogi verwerkt, het snel en betrouwbaar ophalen van QR‑informatie is essentieel voor downstream‑systemen. Deze tutorial leidt u door het gebruik van **GroupDocs.Parser for Java** om QR‑codes (en andere barcodes) uit PDF’s te lezen en de resultaten te exporteren naar een schoon XML‑bestand dat uw ERP-, voorraad- of analyseplatform kan gebruiken.

## Snelle antwoorden
- **Wat doet GroupDocs.Parser for Java?** Het leest PDF‑bestanden en extraheert gestructureerde gegevens zoals barcodes, tabellen en tekst.  
- **Hoe QR‑codes te extraheren?** Configureer `BarcodeOptions` met het QR‑type en roep `parser.getBarcodes()` aan.  
- **Kan ik QR‑codes lezen in Java?** Ja—stel het barcode‑type in op `"QR"` in de opties.  
- **Heb ik een licentie nodig?** Een proefversie werkt voor testen; een commerciële licentie is vereist voor productie.  
- **Welke Java‑versie is vereist?** Java 8 of hoger wordt aanbevolen.

## Wat betekent “QR uit PDF extraheren” in de context van PDF‑verwerking?
Het extraheren van QR uit PDF betekent elke pagina scannen op QR‑gecodeerde afbeeldingen, de ingebedde gegevens decoderen en deze teruggeven in een programma‑vriendelijk formaat. GroupDocs.Parser abstraheert de low‑level beeldanalyse zodat u zich kunt richten op bedrijfslogica in plaats van pixelmanipulatie.

## Waarom GroupDocs.Parser gebruiken voor QR‑extractie?
GroupDocs.Parser ondersteunt **meer dan 30 invoerformaten** en kan PDF’s verwerken tot **500 MB** zonder het volledige bestand in het geheugen te laden, waardoor nauwkeurige resultaten worden geleverd, zelfs bij scans met lage resolutie. U kunt `QualityMode.Low` kiezen voor snelheid of `QualityMode.High` voor maximale precisie, en dezelfde API werkt voor PDF’s, afbeeldingen en Office‑documenten, waardoor de noodzaak voor meerdere bibliotheken verdwijnt.

## Voorvereisten
- **GroupDocs.Parser for Java** (versie 25.5 of later).  
- Maven of handmatige JAR‑download.  
- Java 8+ ontwikkelomgeving (IntelliJ IDEA, Eclipse, of een andere editor).  

## GroupDocs.Parser voor Java instellen
### Maven gebruiken
Voeg de GroupDocs‑repository en afhankelijkheid toe aan uw `pom.xml`:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

### Directe download
U kunt ook de nieuwste JAR downloaden van [GroupDocs.Parser Java documentatie](https://releases.groupdocs.com/parser/java/).

#### Stappen voor licentie‑acquisitie
- **Gratis proefversie:** 30‑daagse proef met volledige functionaliteit.  
- **Tijdelijke licentie:** Vraag een tijdelijke sleutel aan voor uitgebreide evaluatie.  
- **Aankoop:** Verkrijg een commerciële licentie voor productie‑implementaties.

### Basisinitialisatie en -configuratie
Maak een `Parser`‑instantie aan die naar de PDF wijst die u wilt analyseren:

`Parser` is de kernklasse in GroupDocs.Parser die een document vertegenwoordigt en methoden biedt voor het extraheren van inhoud zoals tekst, tabellen en barcodes.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Hoe QR‑codes in Java‑PDF’s te lezen met GroupDocs.Parser
Het lezen van QR‑codes in Java‑PDF’s met GroupDocs.Parser omvat het maken van een parser‑instantie, het configureren van barcode‑opties om QR‑typen te targeten, het aanroepen van de barcode‑extractiemethode, en vervolgens het verwerken van de geretourneerde barcode‑objecten. Het proces is eenvoudig, werkt op elke PDF‑pagina en retourneert de gedecodeerde waarden samen met positionele metadata voor verdere verwerking.

### Stap 1: controleer barcode‑ondersteuning
Controleer vóór het proberen te extraheren of het documentformaat barcode‑scannen ondersteunt:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Uitleg:* Deze controle voorkomt runtime‑fouten bij niet‑ondersteunde bestandstypen.

### Stap 2: configureer barcode‑opties (QR‑codes lezen Java)
`BarcodeOptions` is een configuratie‑object waarmee u kunt opgeven welke barcode‑symbologieën moeten worden gedetecteerd, de scan‑kwaliteitsmodus kunt instellen en parameters zoals detectiedrempels kunt afstemmen, zodat optimale prestaties voor de doel‑QR‑codes worden gegarandeerd.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Uitleg:* `QualityMode.Low` versnelt de verwerking; schakel over naar `High` als u extra nauwkeurigheid nodig heeft. Het argument `"QR"` vertelt de engine om alleen naar QR‑type barcodes te zoeken.

### Stap 3: extraheer de QR‑gegevens
`parser.getBarcodes(options)` scant het document met de opgegeven `BarcodeOptions` en retourneert een collectie van `PageBarcodeArea`‑objecten, elk met de gedecodeerde QR‑waarde, het paginanummer en de exacte coördinaten van de barcode op de pagina, waardoor precieze downstream‑verwerking mogelijk is.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Uitleg:* `parser.getBarcodes` retourneert een iterabele collectie van `PageBarcodeArea`‑objecten, elk met de gedecodeerde QR‑waarde en de locatie op de pagina.

## Geëxtraheerde gegevens exporteren naar XML
### Stap 4: initialiseer de XML‑exporteur
`XmlExporter` is een hulpprogrammaklasse die een collectie van barcode‑objecten omzet in een goed gestructureerd XML‑document, automatisch elementen genereert voor elke barcode met attributen voor paginanaam, positie en gedecodeerde waarde, die vervolgens kan worden opgeslagen of gestreamd naar andere systemen.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Uitleg:* De `XmlExporter` verwerkt de serialisatie van barcode‑objecten naar standaard XML, klaar voor integratie met ERP‑ of voorraad‑systemen.

### Stap 5: schrijf het XML‑bestand
Sla de geëxtraheerde QR‑informatie op op schijf:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Uitleg:* Het resulterende `data.xml` bevat één `<Barcode>`‑element per QR‑code, met attributen voor paginanummer, coördinaten en gedecodeerde waarde.

## Praktische toepassingen
1. **Voorraadbeheer:** Automatisch voorraaddatabases vullen door QR‑tags op inkomende verzend‑PDF’s te lezen.  
2. **Zichtbaarheid in de supply‑chain:** Pakketten in realtime volgen door QR‑identifiers die in logistieke documenten zijn ingebed te extraheren.  
3. **Kassabonnen:** Promotie‑ of garantiebepalingen ophalen uit QR‑codes die op digitale kassabonnen zijn afgedrukt.

## Prestatie‑overwegingen
- **Geheugenbeheer:** Verwerk bij zeer grote PDF’s pagina’s in streaming‑modus in plaats van het volledige bestand in het geheugen te laden.  
- **QualityMode‑selectie:** Gebruik `Low` voor bulkverwerking; schakel over naar `High` bij scans met lage resolutie.  
- **Bibliotheek‑updates:** Houd GroupDocs.Parser up‑to‑date om te profiteren van de nieuwste prestatie‑verbeteringen en bug‑fixes.

## Veelvoorkomende problemen & foutopsporing
| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| Geen barcodes geretourneerd | Verkeerd barcode‑type gespecificeerd | Verander `"QR"` naar het juiste type (bijv. `"CODE_128"`). |
| Out‑of‑memory‑fout bij grote PDF’s | Volledig document in één keer geladen | Verwerk pagina’s afzonderlijk of vergroot de JVM‑heap‑grootte (`-Xmx2g`). |
| Leeg XML‑bestand | `exportBarcodes` aangeroepen vóór extractie | Zorg ervoor dat `parser.getBarcodes(options)` gegevens retourneert vóór het exporteren. |

## Veelgestelde vragen
**Q: Kan ik barcodes extraheren uit afbeeldingsbestanden met GroupDocs.Parser?**  
A: Ja, de bibliotheek ondersteunt barcode‑extractie uit gangbare afbeeldingsformaten (PNG, JPEG, TIFF).

**Q: Welke barcode‑formaten worden herkend?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417, en nog veel meer. Raadpleeg de API‑documentatie voor de volledige lijst.

**Q: Hoe moet ik wachtwoord‑beveiligde PDF’s behandelen?**  
A: Geef het wachtwoord door aan de `Parser`‑constructor: `new Parser(filePath, "password")`.

**Q: Is de proefversie voldoende voor productie‑testen?**  
A: De proefversie biedt volledige functionaliteit maar voegt een watermerk toe aan de geëxtraheerde gegevens. Voor productie, verkrijg een commerciële licentie.

**Q: Wat als mijn PDF zowel QR‑ als lineaire barcodes bevat?**  
A: Maak meerdere `BarcodeOptions`‑instanties aan of geef een array van types door om in één scan alle benodigde formaten te detecteren.

---

**Laatst bijgewerkt:** 2026-10-12  
**Getest met:** GroupDocs.Parser 25.5  
**Auteur:** GroupDocs  

## Bronnen
- [GroupDocs.Parser Java documentatie](https://docs.groupdocs.com/parser/java/)
- [API‑referentie](https://reference.groupdocs.com/parser/java)
- [GroupDocs.Parser downloaden](https://releases.groupdocs.com/parser/java/)
- [GitHub‑repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Gratis ondersteuningsforum](https://forum.groupdocs.com/c/parser)
- [Aanvraag tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)

## Gerelateerde tutorials
- [Barcode PDF extraheren GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [PDF laden vanaf URL met GroupDocs.Parser voor Java](/parser/java/document-loading/)
- [PDF‑formuliergegevens extraheren met GroupDocs.Parser in Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)