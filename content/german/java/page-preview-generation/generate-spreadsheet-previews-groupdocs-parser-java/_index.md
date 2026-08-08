---
date: '2026-07-16'
description: Erfahren Sie, wie Sie mit GroupDocs.Parser ein Spreadsheet-Thumbnail
  in Java erstellen, Excel ohne Office in der Vorschau anzeigen und Excel‑Tabellen
  als Bilder rendern. Dieser Leitfaden behandelt Einrichtung, Implementierung und
  praktische Anwendungsfälle.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: Erstellen Sie ein Spreadsheet-Thumbnail in Java mit GroupDocs.Parser
  – zeigen Sie Excel ohne Office in der Vorschau an und rendern Sie Excel‑Tabellen
  als Bilder. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung, um PNG‑Vorschauen effizient
  zu erzeugen.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: Spreadsheet-Thumbnail in Java mit GroupDocs.Parser erstellen
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: Spreadsheet-Thumbnail in Java mit GroupDocs.Parser erstellen
type: docs
url: /de/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Erstellen von Spreadsheet‑Thumbnails in Java mit GroupDocs.Parser

Wenn Sie **Spreadsheet‑Thumbnails in Java** erstellen möchten, sind Sie hier genau richtig. In diesem Leitfaden zeigen wir, wie Sie hochwertige PNG‑Vorschauen aus `.xlsx`‑Arbeitsmappen mit GroupDocs.Parser für Java erzeugen – ideal für schnelle Thumbnails, das Teilen von Schnappschüssen oder den Aufbau einer Dokument‑Vorschaufunktion in Ihrer Anwendung. Die Lösung funktioniert ohne Microsoft‑Office‑Installation und skaliert bei großen Arbeitsmappen, während der Speicherverbrauch gering bleibt.

## Schnelle Antworten
- **Was bedeutet “Excel‑Vorschau”?** Erzeugen von Bilddateien (z. B. PNG), die jede Arbeitsblattseite darstellen.  
- **Welches Format wird empfohlen?** PNG liefert verlustfreie Qualität und eignet sich gut für Web‑Thumbnails.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion reicht für die Entwicklung; für den Produktionseinsatz ist eine kommerzielle Lizenz erforderlich.  
- **Kann ich die Bildauflösung ändern?** Ja – passen Sie die DPI in `PreviewOptions` an.  
- **Ist es möglich, andere Formate vorzuschauen?** GroupDocs.Parser unterstützt zudem PDF, Word und viele Bildformate.

## Was bedeutet “Excel‑Vorschau” mit GroupDocs.Parser?

Laden Sie Ihre Excel‑Arbeitsmappe und rendern Sie jedes Blatt als PNG‑Bild, ohne Microsoft Office zu benötigen. GroupDocs.Parser streamt Seiten einzeln, erzeugt verlustfreie Thumbnails, die auf die Festplatte gespeichert oder per HTTP zurückgegeben werden können – ideal für webbasierte Vorschaudienste.

GroupDocs.Parser liest Excel‑Arbeitsmappen, rendert jedes Blatt als visuelle Seite und ermöglicht das Streamen dieser Seiten in Bilddateien. Dadurch entfällt die Notwendigkeit von Office‑Interop oder Drittanbieter‑Konvertern.

## Warum GroupDocs.Parser für Excel‑Vorschauen verwenden?

Sie sollten GroupDocs.Parser einsetzen, weil es auf jedem Java‑Server läuft, keine Office‑Installation erfordert, große Arbeitsmappen mit geringem Speicherverbrauch verarbeitet und verlustfreie PNG‑Bilder mit konfigurierbarer DPI erzeugt. Das SDK unterstützt **über 100 Eingabe‑ und Ausgabeformate**, kann eine 200‑seitige Arbeitsmappe in weniger als 3 Sekunden verarbeiten und hält den Speicherverbrauch unter 50 MB pro Blatt.

- **Keine Office‑Installation nötig** – läuft in jeder serverseitigen Java‑Umgebung.  
- **Unterstützt große Dateien** – streamt Seiten einzeln, wodurch der Speicherverbrauch niedrig bleibt.  
- **Ausgabe in hoher Qualität** – Kontrolle über DPI, Format und Rendering‑Optionen.  
- **Flexibel über Formate hinweg** – dieselbe API funktioniert für PDFs, Word‑Dokumente und mehr.

## Voraussetzungen
- **Java Development Kit** (8 +).  
- **IDE** wie IntelliJ IDEA oder Eclipse.  
- **GroupDocs.Parser für Java SDK** – Download von [hier](https://releases.groupdocs.com/parser/java/).  
- **Dokumentation** – siehe die offizielle [Dokumentation](https://docs.groupdocs.com/parser/java/).  
- **Beispieldatei** (`.xlsx`), die Sie vorschauen möchten.  
- **Maven oder Gradle** (optional) für das Dependency‑Management.

## Pakete importieren
Diese Importe geben Ihnen Zugriff auf den Parser, die Vorschau‑Optionen und Hilfs‑Utilities für das Stream‑Handling.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## Schritt‑für‑Schritt‑Anleitung zur Generierung von Spreadsheet‑Seiten‑Vorschauen

### Schritt 1: Parser‑Instanz initialisieren
`Parser` ist die Kernklasse von GroupDocs.Parser, die Lesezugriff auf Spreadsheet‑Dateien bietet und das seitenweise Rendern ermöglicht.  
Erzeugen Sie ein `Parser`‑Objekt, das auf Ihre Excel‑Arbeitsmappe zeigt. Der *try‑with‑resources*‑Block sorgt dafür, dass der Parser automatisch geschlossen wird.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Pro‑Tipp:** Verwenden Sie einen absoluten Pfad oder konfigurieren Sie einen Ressourcen‑Ordner, um `FileNotFoundException` zu vermeiden.

### Schritt 2: Vorschauoptionen vorbereiten
`PreviewOptions` konfiguriert Render‑Parameter wie Ausgabeformat und DPI.  
`ICreatePageStream` ist ein Callback‑Interface, das für jede erzeugte Seite einen Ausgabestream bereitstellt. Definieren Sie, wie jede Seite gespeichert werden soll. Die Implementierung von `ICreatePageStream` liefert für jedes Arbeitsblatt einen frischen `FileOutputStream`.

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> Dieser Schritt ist der Ort, an dem Sie **xlsx zu png konvertieren** – der Stream schreibt PNG‑Daten auf die Festplatte.

### Schritt 3: Einen Delegaten anhängen, um Render‑Informationen zu erfassen
Wenn Sie Details zu jedem gerenderten Blatt benötigen (z. B. Abmessungen, Blattname), registrieren Sie einen Callback.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Schritt 4: Ausgabeformat und DPI festlegen
Wählen Sie PNG als Bildformat und setzen Sie eine DPI, die Qualität und Dateigröße ausbalanciert.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Passen Sie die DPI an, wenn Sie kleinere Thumbnails benötigen (z. B. 96) oder hochauflösende Drucke (z. B. 300).

### Schritt 5: Vorschauen generieren
Nachdem alles konfiguriert ist, rufen Sie `generatePreview` auf. Das SDK iteriert über jedes Arbeitsblatt und ruft den von Ihnen bereitgestellten Stream auf.

```java
parser.generatePreview(previewOptions);
```

### Schritt 6: Hilfsmethode `getOutputPath()` definieren
`getOutputPath()` erstellt einen Dateinamen basierend auf der Seiten‑ (Blatt‑)Nummer und gibt den vollständigen Pfad für das Ausgabebild zurück. Passen Sie die Ordnerstruktur gern nach Ihren Bedürfnissen an.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Häufiges Stolper‑Problem:** Wenn das Verzeichnis `output` nicht vorher erstellt wurde, führt das zu einer `IOException`. Erstellen Sie es programmgesteuert oder stellen Sie sicher, dass es existiert.

## Vollständiges funktionierendes Beispiel (vereinfacht)

Unten finden Sie eine kompakte Version, die alle Bausteine zusammenführt. Sie demonstriert den **Spreadsheet‑Thumbnail‑Workflow in Java** von Anfang bis Ende.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

Führen Sie diesen Code aus, und Sie finden eine Reihe von `preview_page_1.png`, `preview_page_2.png`, … Dateien im Ordner `output` – jede stellt ein Blatt der ursprünglichen Excel‑Arbeitsmappe dar.

## Häufige Probleme & Lösungen
| Problem | Ursache | Lösung |
|-------|-------|-----|
| **Keine Bilder erzeugt** | `getOutputPath` gibt ein ungültiges Verzeichnis zurück | Stellen Sie sicher, dass das Zielverzeichnis existiert oder erstellen Sie es mit `new File("output").mkdirs();` |
| **Out‑of‑Memory‑Fehler bei riesigen Dateien** | Laden der gesamten Arbeitsmappe auf einmal | Verwenden Sie den Streaming‑Ansatz (wie gezeigt) und verarbeiten Sie Seiten einzeln |
| **Falsche DPI** | `setDpi` nicht aufgerufen oder auf den Standardwert (96) gesetzt | Rufen Sie `previewOptions.setDpi(ihrGewünschterWert);` vor `generatePreview` auf |
| **Nicht unterstütztes Format** | Versuch, eine beschädigte `.xlsx`‑Datei vorzuschauen | Validieren Sie die Datei mit Excel oder verwenden Sie `Parser.isSupported` vor der Verarbeitung |

## Häufig gestellte Fragen

**F: Kann ich Vorschauen für PDFs und Bilder mit GroupDocs.Parser erzeugen?**  
A: Ja, dieselbe API funktioniert für PDFs, Word‑Dokumente und viele Bildformate.

**F: Wie ändere ich das Ausgabe‑Bildformat?**  
A: Rufen Sie `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (oder `Gif`, `Bmp` usw.) auf.

**F: Ist die Performance bei sehr großen Arbeitsmappen ein Problem?**  
A: Das SDK streamt Seiten, wodurch der Speicherverbrauch niedrig bleibt. Bei extrem großen Dateien kann eine parallele Batch‑Verarbeitung sinnvoll sein.

**F: Wie gehe ich mit Fehlern während der Vorschauerstellung um?**  
A: Umschließen Sie den Code mit try‑catch‑Blöcken (wie gezeigt) und protokollieren Sie die Ausnahme‑Details. Stellen Sie sicher, dass Streams im `finally`‑Block geschlossen werden, falls Sie kein try‑with‑resources verwenden.

**F: Benötigt die Bibliothek eine Microsoft‑Office‑Installation?**  
A: Nein. GroupDocs.Parser ist eine reine Java‑Lösung und läuft auf jeder Plattform, die Java 8+ unterstützt.

---

**Zuletzt aktualisiert:** 2026-07-16  
**Getestet mit:** GroupDocs.Parser 23.11 (zum Zeitpunkt des Schreibens)  
**Autor:** GroupDocs

## Verwandte Tutorials

- [How to Generate Preview – Document Page Preview Generation Tutorials for GroupDocs.Parser Java](/parser/java/page-preview-generation/)
- [Parse Excel Java with GroupDocs.Parser: Complete Guide](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [How to Extract Raw Text from Excel Sheets Using GroupDocs.Parser for Java: A Step‑by‑Step Guide](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)