---
date: '2026-10-12'
description: Erfahren Sie, wie Sie QR aus PDF in Java mit GroupDocs.Parser extrahieren
  und die Barcode-Daten in XML für die nachgelagerte Verarbeitung exportieren.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Erfahren Sie, wie Sie QR aus PDF in Java mit GroupDocs.Parser extrahieren
  und die Barcode-Daten in XML für die nachgelagerte Verarbeitung exportieren.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Wie man QR aus PDF in Java mit GroupDocs.Parser extrahiert
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
title: Wie man QR aus PDF in Java mit GroupDocs.Parser extrahiert
type: docs
url: /de/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Wie man QR aus PDF in Java mit GroupDocs.Parser extrahiert

Im modernen Geschäftsablauf kann das **Extrahieren von QR aus PDF**-Dateien ein manuelles Dateneingabe‑Engpass in eine vollständig automatisierte Pipeline verwandeln. Egal, ob Sie Versandmanifesten, Einzelhandelsbelegen oder Produktkatalogen bearbeiten, das schnelle und zuverlässige Abrufen von QR‑Informationen ist für nachgelagerte Systeme unerlässlich. Dieses Tutorial führt Sie durch die Verwendung von **GroupDocs.Parser for Java**, um QR‑Codes (und andere Barcodes) aus PDFs zu lesen und die Ergebnisse in eine saubere XML‑Datei zu exportieren, die Ihr ERP-, Inventar‑ oder Analyse‑System verarbeiten kann.

## Schnelle Antworten
- **Was macht GroupDocs.Parser for Java?** Es liest PDF‑Dateien und extrahiert strukturierte Daten wie Barcodes, Tabellen und Text.  
- **Wie extrahiere ich QR‑Codes?** Konfigurieren Sie `BarcodeOptions` mit dem QR‑Typ und rufen Sie `parser.getBarcodes()` auf.  
- **Kann ich QR‑Codes in Java lesen?** Ja – setzen Sie den Barcode‑Typ auf `"QR"` in den Optionen.  
- **Brauche ich eine Lizenz?** Eine Testversion funktioniert zum Testen; für die Produktion ist eine kommerzielle Lizenz erforderlich.  
- **Welche Java‑Version wird benötigt?** Java 8 oder höher wird empfohlen.

## Was bedeutet „QR aus PDF extrahieren“ im Kontext der PDF‑Verarbeitung?
Das Extrahieren von QR aus PDF bedeutet, jede Seite nach QR‑kodierten Grafiken zu durchsuchen, die eingebetteten Daten zu dekodieren und sie in einem programmfähigen Format zurückzugeben. GroupDocs.Parser abstrahiert die Low‑Level‑Bildanalyse, sodass Sie sich auf die Geschäftslogik statt auf die Pixelmanipulation konzentrieren können.

## Warum GroupDocs.Parser für die QR‑Extraktion verwenden?
GroupDocs.Parser unterstützt **über 30 Eingabeformate** und kann PDFs bis zu **500 MB** verarbeiten, ohne die gesamte Datei in den Speicher zu laden, und liefert hochpräzise Ergebnisse selbst bei niedrigauflösenden Scans. Sie können `QualityMode.Low` für Geschwindigkeit oder `QualityMode.High` für maximale Präzision wählen, und dieselbe API funktioniert für PDFs, Bilder und Office‑Dokumente, wodurch der Bedarf an mehreren Bibliotheken entfällt.

## Voraussetzungen
- **GroupDocs.Parser for Java** (Version 25.5 oder neuer).  
- Maven oder manueller JAR‑Download.  
- Java 8+ Entwicklungsumgebung (IntelliJ IDEA, Eclipse oder ein beliebiger Editor).  

## Einrichtung von GroupDocs.Parser für Java
### Verwendung von Maven
Fügen Sie das GroupDocs‑Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu:

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

### Direkter Download
Alternativ können Sie das neueste JAR von [GroupDocs.Parser Java-Dokumentation](https://releases.groupdocs.com/parser/java/) herunterladen.

#### Schritte zum Erwerb einer Lizenz
- **Free trial:** 30‑tägige Testversion mit vollem Funktionsumfang.  
- **Temporary license:** Fordern Sie einen temporären Schlüssel für eine erweiterte Evaluierung an.  
- **Purchase:** Erwerben Sie eine kommerzielle Lizenz für Produktions‑Deployments.

### Grundlegende Initialisierung und Einrichtung
Erstellen Sie eine `Parser`‑Instanz, die auf das zu analysierende PDF verweist:

`Parser` ist die Kernklasse in GroupDocs.Parser, die ein Dokument repräsentiert und Methoden zum Extrahieren von Inhalten wie Text, Tabellen und Barcodes bereitstellt.  

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

## Wie man QR‑Codes in Java‑PDFs mit GroupDocs.Parser liest
Das Lesen von QR‑Codes in Java‑PDFs mit GroupDocs.Parser umfasst das Erstellen einer Parser‑Instanz, das Konfigurieren von Barcode‑Optionen zur Zielausrichtung auf QR‑Typen, das Aufrufen der Barcode‑Extraktionsmethode und anschließend das Verarbeiten der zurückgegebenen Barcode‑Objekte. Der Vorgang ist unkompliziert, funktioniert auf jeder PDF‑Seite und liefert die dekodierten Werte zusammen mit Positions‑Metadaten für die Weiterverarbeitung.

### Schritt 1: Barcode‑Unterstützung prüfen
Stellen Sie vor dem Versuch der Extraktion sicher, dass das Dokumentformat die Barcode‑Erkennung unterstützt:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Erklärung:* Diese Prüfung verhindert Laufzeitfehler bei nicht unterstützten Dateitypen.

### Schritt 2: Barcode‑Optionen konfigurieren (QR‑Codes in Java lesen)
`BarcodeOptions` ist ein Konfigurationsobjekt, das Ihnen ermöglicht, welche Barcode‑Symbologien erkannt werden sollen, den Scan‑Qualitätsmodus festzulegen und Parameter wie Erkennungs‑Schwellenwerte fein abzustimmen, um optimale Leistung für die Ziel‑QR‑Codes zu gewährleisten.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Erklärung:* `QualityMode.Low` beschleunigt die Verarbeitung; wechseln Sie zu `High`, wenn Sie zusätzliche Genauigkeit benötigen. Das Argument "QR" weist die Engine an, nur QR‑Typ‑Barcodes zu suchen.

### Schritt 3: QR‑Daten extrahieren
`parser.getBarcodes(options)` scannt das Dokument mit den angegebenen `BarcodeOptions` und gibt eine Sammlung von `PageBarcodeArea`‑Objekten zurück, von denen jedes den dekodierten QR‑Wert, die Seitennummer und die genauen Koordinaten des Barcodes auf der Seite enthält, was eine präzise Weiterverarbeitung ermöglicht.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Erklärung:* `parser.getBarcodes` gibt eine iterierbare Sammlung von `PageBarcodeArea`‑Objekten zurück, von denen jedes den dekodierten QR‑Wert und dessen Position auf der Seite enthält.

## Exportieren extrahierter Daten nach XML
### Schritt 4: XML‑Exporter initialisieren
`XmlExporter` ist eine Hilfsklasse, die eine Sammlung von Barcode‑Objekten in ein gut strukturiertes XML‑Dokument umwandelt, automatisch Elemente für jeden Barcode mit Attributen für Seitenindex, Position und dekodierten Wert erzeugt, die dann gespeichert oder an andere Systeme gestreamt werden können.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Erklärung:* Der `XmlExporter` übernimmt die Serialisierung von Barcode‑Objekten in standard‑XML, bereit für die Integration in ERP‑ oder Inventursysteme.

### Schritt 5: XML‑Datei schreiben
Speichern Sie die extrahierten QR‑Informationen auf dem Datenträger:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Erklärung:* Die resultierende `data.xml` enthält ein `<Barcode>`‑Element pro QR‑Code, mit Attributen für Seitenzahl, Koordinaten und dekodierten Wert.

## Praktische Anwendungen
1. **Inventory management:** Automatisches Befüllen von Bestandsdatenbanken durch Lesen von QR‑Tags auf eingehenden Versand‑PDFs.  
2. **Supply‑chain visibility:** Verfolgen Sie Pakete in Echtzeit, indem Sie QR‑Kennungen aus Logistik‑Dokumenten extrahieren.  
3. **Retail receipts:** Ziehen Sie Werbe‑ oder Garantieinformationen aus QR‑Codes, die auf digitalen Belegen gedruckt sind.

## Leistungsüberlegungen
- **Memory management:** Für sehr große PDFs sollten Sie Seiten gestreamt verarbeiten, anstatt die gesamte Datei in den Speicher zu laden.  
- **QualityMode selection:** Verwenden Sie `Low` für Massenverarbeitung; wechseln Sie zu `High`, wenn Sie mit niedrigauflösenden Scans arbeiten.  
- **Library updates:** Halten Sie GroupDocs.Parser aktuell, um von den neuesten Leistungsverbesserungen und Fehlerbehebungen zu profitieren.

## Häufige Probleme & Fehlersuche
| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Keine Barcodes zurückgegeben | Falscher Barcode‑Typ angegeben | Ändern Sie `"QR"` zum passenden Typ (z. B. `"CODE_128"`). |
| Out‑of‑Memory‑Fehler bei großen PDFs | Gesamtes Dokument auf einmal geladen | Verarbeiten Sie Seiten einzeln oder erhöhen Sie die JVM‑Heap‑Größe (`-Xmx2g`). |
| Leere XML‑Datei | `exportBarcodes` vor der Extraktion aufgerufen | Stellen Sie sicher, dass `parser.getBarcodes(options)` Daten zurückgibt, bevor Sie exportieren. |

## Häufig gestellte Fragen
**Q: Kann ich Barcodes aus Bilddateien mit GroupDocs.Parser extrahieren?**  
A: Ja, die Bibliothek unterstützt die Barcode‑Extraktion aus gängigen Bildformaten (PNG, JPEG, TIFF).

**Q: Welche Barcode‑Formate werden erkannt?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 und viele weitere. Siehe die API‑Dokumentation für die vollständige Liste.

**Q: Wie gehe ich mit passwortgeschützten PDFs um?**  
A: Übergeben Sie das Passwort dem `Parser`‑Konstruktor: `new Parser(filePath, "password")`.

**Q: Ist die Testversion für Produkttests ausreichend?**  
A: Die Testversion bietet vollen Funktionsumfang, fügt jedoch ein Wasserzeichen zu den extrahierten Daten hinzu. Für die Produktion erwerben Sie eine kommerzielle Lizenz.

**Q: Was ist, wenn mein PDF sowohl QR‑ als auch lineare Barcodes enthält?**  
A: Erstellen Sie mehrere `BarcodeOptions`‑Instanzen oder übergeben Sie ein Array von Typen, um alle benötigten Formate in einem Durchlauf zu scannen.

---

**Zuletzt aktualisiert:** 2026-10-12  
**Getestet mit:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs  

## Ressourcen
- [GroupDocs.Parser Java-Dokumentation](https://docs.groupdocs.com/parser/java/)
- [API‑Referenz](https://reference.groupdocs.com/parser/java)
- [GroupDocs.Parser herunterladen](https://releases.groupdocs.com/parser/java/)
- [GitHub‑Repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Kostenloses Support‑Forum](https://forum.groupdocs.com/c/parser)
- [Antrag für temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)

## Verwandte Tutorials

- [Barcode aus PDF extrahieren GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [PDF von URL laden mit GroupDocs.Parser für Java](/parser/java/document-loading/)
- [PDF-Formulardaten mit GroupDocs.Parser in Java extrahieren](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)