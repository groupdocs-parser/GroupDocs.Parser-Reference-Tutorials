---
date: '2026-02-19'
description: Leer hoe u QR-codes in Java‑PDF’s kunt lezen met GroupDocs.Parser en
  de barcode‑gegevens naar XML kunt exporteren.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Hoe QR-codes te lezen in Java‑PDF’s met GroupDocs.Parser
type: docs
url: /nl/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Hoe QR-codes lezen in Java PDF's met GroupDocs.Parser

In moderne bedrijfsprocessen kan **hoe QR** codes uit PDF‑documenten het verschil maken tussen een handmatige gegevensinvoerknooppunt en een volledig geautomatiseerde pijplijn. Of u nu verzendingsmanifesten, kassabonnen of productcatalogi verwerkt, het snel en betrouwbaar extraheren van QR‑informatie is essentieel. Deze tutorial leidt u door het gebruik van **GroupDocs.Parser for Java** om QR‑codes (en andere barcodes) uit PDF's te lezen en de resultaten te exporteren naar een schoon XML‑bestand dat door downstream‑systemen kan worden gebruikt.

## Snelle antwoorden
- **Wat doet GroupDocs.Parser for Java?** Het leest PDF‑bestanden en extraheert gestructureerde gegevens zoals barcodes.  
- **Hoe QR‑codes extraheren?** Door `BarcodeOptions` te configureren met het QR‑type en `parser.getBarcodes()` aan te roepen.  
- **Kan ik QR‑codes lezen in Java?** Ja—stel het barcode‑type in op `"QR"` in de opties.  
- **Heb ik een licentie nodig?** Een proefversie werkt voor testen; een commerciële licentie is vereist voor productie.  
- **Welke Java‑versie is vereist?** Java 8 of hoger wordt aanbevolen.

## Wat betekent “hoe QR‑codes lezen” in de context van PDF‑verwerking?
Het lezen van QR‑codes uit PDF's betekent elke pagina scannen op QR‑gecodeerde grafische elementen, de ingebedde data decoderen en deze teruggeven in een programma‑vriendelijk formaat. GroupDocs.Parser abstraheert de low‑level beeldanalyse zodat u zich kunt richten op de bedrijfslogica in plaats van pixelmanipulatie.

## Waarom GroupDocs.Parser gebruiken voor QR‑extractie?
- **Hoge nauwkeurigheid:** Ingebouwde beeldverwerkingsalgoritmen verwerken scans met lage resolutie.  
- **Prestatie‑opties:** Kies `QualityMode.Low` voor snelheid of `QualityMode.High` voor maximale precisie.  
- **Cross‑formatondersteuning:** Werkt met PDF's, afbeeldingen en zelfs Office‑documenten, zodat u dezelfde codebasis kunt hergebruiken voor verschillende bestandstypen.

## Vereisten
- **GroupDocs.Parser for Java** (versie 25.5 of later).  
- Maven of handmatige JAR‑download.  
- Java 8+ ontwikkelomgeving (IntelliJ IDEA, Eclipse of een andere editor).  

## GroupDocs.Parser voor Java instellen
### Maven gebruiken
Add the GroupDocs repository and dependency to your `pom.xml`:

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
Alternatively, download the latest JAR from [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Stappen voor licentie‑acquisitie
- **Gratis proefversie:** 30‑daagse proef met volledige functionaliteit.  
- **Tijdelijke licentie:** Vraag een tijdelijke sleutel aan voor uitgebreide evaluatie.  
- **Aankoop:** Verkrijg een commerciële licentie voor productie‑implementaties.

### Basisinitialisatie en -configuratie
Create a `Parser` instance that points to the PDF you want to analyze:

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

## Hoe QR‑codes lezen in Java PDF's met GroupDocs.Parser
### Stap 1: Controleer barcode‑ondersteuning
Before attempting extraction, confirm that the document format supports barcode scanning:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Uitleg:* Deze controle voorkomt runtime‑fouten bij niet‑ondersteunde bestandstypen.

### Stap 2: Barcode‑opties configureren (QR‑codes lezen in Java)
Set the scanning quality and specify that you’re interested in QR codes:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Uitleg:* `QualityMode.Low` versnelt de verwerking; schakel over naar `High` als u extra nauwkeurigheid nodig heeft. Het argument `"QR"` vertelt de engine om alleen naar QR‑type barcodes te zoeken.

### Stap 3: De QR‑gegevens extraheren
Pull the barcode information from every page of the PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Uitleg:* `parser.getBarcodes` retourneert een iterabele collectie van `PageBarcodeArea`‑objecten, elk met de gedecodeerde QR‑waarde en de locatie op de pagina.

## Geëxtraheerde gegevens exporteren naar XML
### Stap 4: Initialise de XML‑exporteur
Create an exporter that will transform the barcode collection into a well‑structured XML file:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Uitleg:* De `XmlExporter` verwerkt de serialisatie van barcode‑objecten naar standaard XML, klaar voor integratie met ERP‑ of voorraadsystemen.

### Stap 5: Schrijf het XML‑bestand
Save the extracted QR information to disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Uitleg:* Het resulterende `data.xml` bevat één `<Barcode>`‑element per QR‑code, met attributen voor paginanummer, coördinaten en gedecodeerde waarde.

## Praktische toepassingen
1. **Voorraadbeheer:** Automatisch voorraaddatabases vullen door QR‑tags op binnenkomende verzend‑PDF's te lezen.  
2. **Zichtbaarheid in de toeleveringsketen:** Pakketten in realtime volgen door QR‑identifiers uit logistieke documenten te extraheren.  
3. **Kassabonnen:** Promotie‑ of garantiebepalingen ophalen uit QR‑codes die op digitale bonnen zijn afgedrukt.

## Prestatie‑overwegingen
- **Geheugenbeheer:** Voor zeer grote PDF's pagina's in streaming‑modus verwerken in plaats van het hele bestand in het geheugen te laden.  
- **QualityMode‑selectie:** Gebruik `Low` voor bulkverwerking; schakel over naar `High` bij scans met lage resolutie.  
- **Bibliotheek‑updates:** Houd GroupDocs.Parser up‑to‑date om te profiteren van de nieuwste prestatie‑verbeteringen en bug‑fixes.

## Veelvoorkomende problemen & probleemoplossing
| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|---------|--------------------------|----------|
| Geen barcodes geretourneerd | Verkeerd barcode‑type opgegeven | Verander `"QR"` naar het juiste type (bijv. `"CODE_128"`). |
| Out‑of‑memory‑fout bij grote PDF's | Het volledige document in één keer geladen | Verwerk pagina's afzonderlijk of vergroot de JVM‑heap‑grootte (`-Xmx2g`). |
| Leeg XML‑bestand | `exportBarcodes` aangeroepen vóór extractie | Zorg dat `parser.getBarcodes(options)` data retourneert vóór het exporteren. |

## Veelgestelde vragen
**V: Kan ik barcodes uit afbeeldingsbestanden extraheren met GroupDocs.Parser?**  
A: Ja, de bibliotheek ondersteunt barcode‑extractie uit gangbare afbeeldingsformaten (PNG, JPEG, TIFF).

**V: Welke barcode‑formaten worden herkend?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 en nog veel meer. Zie de API‑documentatie voor de volledige lijst.

**V: Hoe ga ik om met met wachtwoord beveiligde PDF's?**  
A: Geef het wachtwoord door aan de `Parser`‑constructor: `new Parser(filePath, "password")`.

**V: Is de proefversie voldoende voor productietesten?**  
A: De proefversie biedt volledige functionaliteit maar voegt een watermerk toe aan geëxtraheerde data. Voor productie dient u een commerciële licentie aan te schaffen.

**V: Wat als mijn PDF zowel QR‑ als lineaire barcodes bevat?**  
A: Maak meerdere `BarcodeOptions`‑instanties aan of geef een array van types door om in één keer alle benodigde formaten te scannen.

---

**Laatst bijgewerkt:** 2026-02-19  
**Getest met:** GroupDocs.Parser 25.5  
**Auteur:** GroupDocs  

## Resources
- [GroupDocs.Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- [API Reference](https://reference.groupdocs.com/parser/java)
- [Download GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub Repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/parser)
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)