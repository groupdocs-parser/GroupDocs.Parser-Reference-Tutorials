---
date: '2026-02-09'
description: Erfahren Sie, wie Sie OCR verwenden, um Text aus Bildern und Dokumenten
  in Java mit GroupDocs.Parser zu extrahieren. Dieser Leitfaden behandelt die Einrichtung,
  die Java‑Bild‑zu‑Text‑Konvertierung und praktische Anwendungsfälle für eine effiziente
  Dokumentenverarbeitung.
keywords:
- OCR Text Extraction
- GroupDocs.Parser Java
- Java OCR Integration
title: 'Wie man OCR mit GroupDocs.Parser Java verwendet: Text aus Bildern und Dokumenten
  extrahieren'
type: docs
url: /de/java/ocr-integration/ocr-text-extraction-groupdocs-parser-java/
weight: 1
---

# Wie man OCR mit GroupDocs.Parser für Java verwendet

Suchen Sie nach einer effizienten Möglichkeit, Text aus Bildern oder gescannten Dokumenten zu extrahieren? **Wie man OCR verwendet** mit der GroupDocs.Parser‑Bibliothek für Java bietet eine robuste Lösung und ermöglicht die nahtlose Integration von Optical Character Recognition (OCR) in Ihre Anwendungen. Dieser umfassende Leitfaden führt Sie durch das Extrahieren von Textbereichen aus Bilddateien mithilfe des Aspose OCR‑Connectors mit GroupDocs.Parser in Java und erweitert Ihre Dokumentenverarbeitungsfähigkeiten.

**Was Sie lernen werden**
- Einrichtung und Nutzung von GroupDocs.Parser für Java.
- Initialisierung von `ParserSettings` mit einem OCR‑Connector.
- Techniken zum Extrahieren von Textbereichen aus Bildern mithilfe der Aspose OCR‑Technologie.
- Praktische Anwendungen dieses Features in realen Szenarien wie **java image to text**‑Konvertierung und dem Extrahieren von Textpositionen in Java.

## Schnelle Antworten
- **Was bedeutet „how to use OCR“?** Es bezieht sich auf die Integration einer OCR‑Engine, um Text aus bildbasierten Dateien zu lesen.  
- **Welche Bibliothek bietet OCR für Java?** GroupDocs.Parser kombiniert mit dem Aspose OCR‑Connector.  
- **Brauche ich eine Lizenz?** Eine kostenlose Testversion ist verfügbar; für den Produktionseinsatz ist eine permanente Lizenz erforderlich.  
- **Kann ich Textkoordinaten erhalten?** Ja, die API liefert die Positionen der Textbereiche (links, oben, Breite, Höhe).  
- **Welche Java‑Version wird benötigt?** Java 8 oder neuer wird empfohlen.

## Was ist OCR‑Textextraktion?
Optical Character Recognition (OCR) wandelt visuellen Text – gefunden in gescannten Bildern, PDFs oder Fotografien – in maschinenlesbare Zeichen um. Wenn Sie **how to use OCR** in Java einsetzen, ermöglichen Sie Ihren Anwendungen, zuvor statische Dokumente zu durchsuchen, zu bearbeiten und zu analysieren.

## Warum GroupDocs.Parser für OCR verwenden?
- **Unified API** – Verarbeitet PDFs, Bilder und viele andere Formate mit einer einzigen Codebasis.  
- **Accurate Recognition** – Angetrieben von Aspose OCR, das mehrere Sprachen und Schriftarten unterstützt.  
- **Position Data** – Ruft die genauen Koordinaten jedes Textblocks ab, ideal für layout‑bewusste Verarbeitung.  
- **Scalable** – Funktioniert mit kleinen Bildern oder großen Batch‑Jobs und kann on‑premise oder in der Cloud ausgeführt werden.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

### Erforderliche Bibliotheken und Abhängigkeiten
- **GroupDocs.Parser for Java**: Version 25.5 oder neuer.  
- **Maven** oder direkte Download‑Einrichtung für die Bibliotheksinstallation.  
- **Aspose OCR Connector**: Zugriff auf die OCR‑Technologie von Aspose ist erforderlich.

### Anforderungen an die Umgebung
- Eine kompatible IDE (IntelliJ IDEA, Eclipse usw.) mit Java 8+.  
- Maven installiert, falls Sie den Maven‑Repository‑Ansatz bevorzugen.

### Wissensvoraussetzungen
- Grundlegende Java‑Programmierkenntnisse.  
- Vertrautheit mit dem Umgang mit Projektabhängigkeiten.

## Einrichtung von GroupDocs.Parser für Java

Sie können die Bibliothek über Maven hinzufügen oder sie direkt herunterladen.

### Using Maven
Add the following configurations to your `pom.xml` file:

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

### Direct Download
Alternativ können Sie die neueste Version von [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) herunterladen.

#### Schritte zum Erwerb einer Lizenz
- **Free Trial** – Evaluieren Sie die Bibliothek kostenlos.  
- **Temporary License** – Verwenden Sie einen zeitlich begrenzten Schlüssel für erweiterte Tests.  
- **Purchase** – Erwerben Sie eine Voll‑Lizenz für den Produktionseinsatz.

### Grundlegende Initialisierung und Einrichtung

Nachdem die Bibliothek verfügbar ist, können Sie den Parser initialisieren. Nachfolgend finden Sie den wesentlichen Java‑Code, der eine `ParserSettings`‑Instanz mit dem Aspose OCR‑Connector erstellt:

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.ParserSettings;
import com.groupdocs.parser.ocr.AsposeOcrOnPremise;

ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

Nachdem die Grundlagen erledigt sind, gehen wir zum Extrahieren von OCR‑Textbereichen über.

## Wie man Textbereiche mit OCR extrahiert (Schritt‑für‑Schritt)

### 1. Initialisieren Sie `ParserSettings` mit dem OCR‑Connector
Der OCR‑Connector ermöglicht die Erkennung von Text in ausschließlich bildbasierten Dokumenten.

```java
// Initialize ParserSettings with OCR Connector
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

### 2. Öffnen Sie das Dokument und konfigurieren Sie die Extraktionsoptionen
Wir verwenden `PageTextAreaOptions`, um dem Parser mitzuteilen, dass er Positionsdaten für jedes erkannte Wort zurückgeben soll.

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
    // Configure PageTextAreaOptions for OCR processing
    PageTextAreaOptions options = new PageTextAreaOptions(true);
    
    // Extract text areas from the document
    java.lang.Iterable<PageTextArea> areas = parser.getTextAreas(options);

    if (areas == null) {
        return; // Exit if text areas extraction is not supported
    }
    
    for (PageTextArea a : areas) {
        String text = a.getText();
        int leftPosition = a.getRectangle().getLeft();
        int topPosition = a.getRectangle().getTop();
        int width = a.getRectangle().getSize().getWidth();
        int height = a.getRectangle().getSize().getHeight();

        // Process the extracted data as needed
    }
} catch (java.lang.Exception ex) {
    // Handle any exceptions that occur during processing
}
```

#### Was dieser Code macht
- **Creates** eine `Parser`‑Instanz, die auf Ihren Dokumentordner zeigt.  
- **Enables** OCR über `PageTextAreaOptions(true)`.  
- **Iterates** über jedes `PageTextArea` und liefert Ihnen den erkannten Text **und** sein genaues Rechteck (Position und Größe).  
- **Allows** Ihnen, die Daten zu speichern oder zu manipulieren, z. B. indem Sie sie in eine Datenbank einfügen oder in einer UI überlagern.

### 3. Verarbeiten Sie die Ergebnisse
Sie können die extrahierten Texte und Koordinaten nun für verschiedene Szenarien nutzen:

- **Document Digitization** – Konvertieren Sie gescannte Verträge in durchsuchbare PDFs.  
- **Data Entry Automation** – Extrahieren Sie Felder wie Rechnungsnummern direkt aus Beleg‑Bildern.  
- **Content Management** – Indexieren Sie Textpositionen für erweiterte Such‑Highlighting.

## Häufige Probleme und Lösungen

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Keine Textbereiche zurückgegeben | OCR‑Connector nicht konfiguriert oder Bildpfad ist falsch | Stellen Sie sicher, dass die `AsposeOcrOnPremise`‑Instanz korrekt lizenziert ist und der Dateipfad zugänglich ist. |
| Verzerrte Zeichen | Bildqualität ist niedrig oder Sprache wird nicht unterstützt | Verwenden Sie hochauflösendere Scans und konfigurieren Sie das OCR‑Sprachpaket. |
| Out‑of‑Memory‑Fehler bei großen PDFs | Verarbeitung vieler hochauflösender Seiten gleichzeitig | Verarbeiten Sie Seiten in Batches oder aktivieren Sie den Streaming‑Modus (`ParserSettings.setEnableStreaming(true)`). |

## Häufig gestellte Fragen

**Q: Wie installiere ich GroupDocs.Parser für Java?**  
A: Fügen Sie es als Maven‑Abhängigkeit hinzu (siehe das XML‑Snippet oben) oder laden Sie es direkt von der offiziellen Release‑Seite herunter.

**Q: Was ist Aspose OCR und warum mit GroupDocs.Parser verwenden?**  
A: Aspose OCR ist eine hochpräzise Texterkennungs‑Engine. In Kombination mit GroupDocs.Parser erweitert es die Fähigkeiten des Parsers, bild‑nur Dateien zu verarbeiten und präzise Textpositionen bereitzustellen.

**Q: Kann ich mehrere Bildformate verarbeiten?**  
A: Ja. GroupDocs.Parser unterstützt JPEG, PNG, BMP, TIFF und mehr – stellen Sie nur sicher, dass der OCR‑Connector das Format lesen kann.

**Q: Was soll ich tun, wenn keine Textbereiche extrahiert werden?**  
A: Überprüfen Sie den Dateipfad, bestätigen Sie, dass der OCR‑Connector lizenziert ist, und vergewissern Sie sich, dass der Dokumenttyp von Aspose OCR unterstützt wird.

**Q: Wo finde ich weitere Ressourcen zu GroupDocs.Parser?**  
A: Besuchen Sie die [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/) für detaillierte Anleitungen und API‑Referenzen.

## Ressourcen
- [Dokumentation](https://docs.groupdocs.com/parser/java/)
- [API‑Referenz](https://reference.groupdocs.com/parser/java)
- [Neueste Version herunterladen](https://releases.groupdocs.com/parser/java/)
- [GitHub‑Repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Kostenloses Support‑Forum](https://forum.groupdocs.com/c/parser)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)

Durchstöbern Sie diese Ressourcen, um Ihr Verständnis zu vertiefen und die Möglichkeiten von GroupDocs.Parser in Ihren Projekten zu erweitern.

---

**Zuletzt aktualisiert:** 2026-02-09  
**Getestet mit:** GroupDocs.Parser 25.5 für Java  
**Autor:** GroupDocs