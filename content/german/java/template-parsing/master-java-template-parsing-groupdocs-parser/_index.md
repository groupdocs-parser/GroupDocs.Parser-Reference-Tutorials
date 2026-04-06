---
date: '2026-02-11'
description: Erfahren Sie, wie Sie Rechnungsdaten mit GroupDocs.Parser für Java extrahieren.
  Dieser Leitfaden zeigt, wie Sie die Dokumentextraktion automatisieren, verknüpfte
  Felder erstellen und die Stapelverarbeitung von Dokumenten handhaben.
keywords:
- Java template parsing
- GroupDocs.Parser
- regular expressions in Java
title: Rechnungsdaten mit Java-Parsing extrahieren – GroupDocs.Parser
type: docs
url: /de/java/template-parsing/master-java-template-parsing-groupdocs-parser/
weight: 1
---

# Rechnungsdaten mit Java Parsing extrahieren – GroupDocs.Parser

In der heutigen schnelllebigen Geschäftsumgebung ist das **extrahieren von Rechnungsdaten** schnell und genau ein kritischer Schritt zur Automatisierung von Finanz‑Workflows. Egal, ob Sie eine einzelne Rechnung bearbeiten oder Tausende im Batch verarbeiten, GroupDocs.Parser für Java ermöglicht das Definieren flexibler Vorlagen, die Verwendung von regulären Ausdrücken und das **Erstellen verknüpfter Felder**, die sich an jedes Dokumentlayout anpassen. In diesem Tutorial führen wir Sie durch die Einrichtung der Bibliothek, den Aufbau einer Vorlage, die **Rechnungsdaten extrahiert**, und das Parsen von Dokumenten in großem Umfang.

## Schnelle Antworten
- **Was bedeutet „Rechnungsdaten extrahieren“?** Es bezieht sich darauf, Felder wie Rechnungsnummer, Datum, Steuer und Gesamtbetrag programmgesteuert aus PDF-, DOCX- oder Bilddateien zu ziehen.  
- **Welche Bibliothek sollte ich verwenden?** GroupDocs.Parser für Java bietet leistungsstarke, vorlagenbasierte Extraktion mit Regex‑Unterstützung.  
- **Kann ich viele Dateien gleichzeitig verarbeiten?** Ja – kombinieren Sie den Parser mit Batch‑Dokumentenverarbeitungstechniken.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion oder temporäre Lizenz reicht für die Evaluierung; für die Produktion ist eine gekaufte Lizenz erforderlich.  
- **Ist sie für Java 8+ geeignet?** Absolut – die Bibliothek unterstützt JDK 8 und neuere Versionen.

## Was bedeutet „Rechnungsdaten extrahieren“?
Das Extrahieren von Rechnungsdaten bedeutet, automatisch wichtige Informationen wie Rechnungsnummer, Datum, Steuerbetrag und Gesamtsumme direkt aus digitalen Dokumenten zu finden und abzurufen, wodurch manuelle Dateneingabe entfällt.

## Warum GroupDocs.Parser für Java verwenden?
- **Hohe Genauigkeit** dank Regex und Positionierung verknüpfter Felder.  
- **Unterstützt viele Formate** (PDF, DOCX, Bilder).  
- **Skalierbar** – ideal für sowohl Einzel‑ als auch Batch‑Dokumentenverarbeitungsszenarien.  
- **Einfache Integration** in bestehende Java‑Anwendungen.

## Voraussetzungen
- JDK 8 oder höher.  
- Eine IDE (IntelliJ IDEA, Eclipse usw.).  
- Zugriff auf die GroupDocs.Parser für Java Bibliothek (Download oder Maven).

### Erforderliche Bibliotheken, Versionen und Abhängigkeiten
Fügen Sie das Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu:

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

Sie können auch das **neueste JAR** von [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) herunterladen.

### Wissensvoraussetzungen
Grundlegende Java‑Programmierung und Vertrautheit mit Datei‑I/O erleichtern die Schritte.

## Einrichtung von GroupDocs.Parser für Java
1. **Fügen Sie die Maven‑Abhängigkeit** (oder das JAR) zu Ihrem Projekt hinzu.  
2. **Erwerben Sie eine Lizenz** – Sie können mit einer kostenlosen Testversion oder einer temporären Lizenz von [hier](https://purchase.groupdocs.com/temporary-license/) beginnen.  
3. **Initialisieren Sie den Parser** – das Code‑Snippet unten zeigt die erforderlichen Importe und eine einfache Initialisierung.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.*;
import com.groupdocs.parser.templates.*;
```

## Wie man verknüpfte Felder in einer Vorlage erstellt
Verknüpfte Felder ermöglichen das Erfassen von Daten, die in einem festen Abstand zu einem anderen bekannten Feld erscheinen (z. B. der Steuerwert, der dem Wort „Tax“ folgt).

### Definieren eines regulären Ausdrucks‑Feldes
Zuerst finden wir das Label **Tax** mithilfe eines Regex‑Musters.

```java
// Create a template field with a regex position
TemplateField regexField = new TemplateField(
        new TemplateRegexPosition("Tax"), 
        "Tax");
```

### Konfigurieren eines verknüpften Feldes
Als Nächstes definieren wir das Feld, das den tatsächlichen Steuerbetrag enthält, positioniert relativ zum **Tax**‑Label.

```java
// Create a linked field based on the position of 'Tax'
TemplateField linkedField = new TemplateField(
        new TemplateLinkedPosition(
                "Tax",
                new Size(100, 20),
                new TemplateLinkedPositionEdges(false, false, true, false)),
        "TaxValue");
```

### Zusammenstellen der Vorlage
Kombinieren Sie das Regex‑Feld und das verknüpfte Feld zu einem einzigen Vorlagenobjekt.

```java
// Combine both fields into a comprehensive template
Template templateWithRegexAndLink = new Template(Arrays.asList(
        new TemplateItem[]{regexField, linkedField}));
```

## Wie man Rechnungsdaten mit der definierten Vorlage extrahiert
Jetzt, da die Vorlage fertig ist, können wir eine Rechnung parsen und die gewünschten Werte abrufen.

### Dokument parsen
Öffnen Sie das PDF (oder ein beliebiges unterstütztes Format) und wenden Sie die Vorlage an.

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY/InvoiceSample.pdf")) {
    // Extract data according to the defined template
    DocumentData data = parser.parseByTemplate(templateWithRegexAndLink);
```

### Durch die extrahierten Daten iterieren
Durchlaufen Sie die Ergebnisse und geben Sie den Namen und Wert jedes Feldes aus.

```java
    // Loop through all extracted data items
    for (int i = 0; i < data.getCount(); i++) {
        Object pageArea = data.get(i).getPageArea();
        if (pageArea instanceof PageTextArea) {
            PageTextArea area = (PageTextArea) pageArea;
            System.out.println(data.get(i).getName() + ": " + area.getText());
        } else {
            System.out.println(data.get(i).getName() + ": Not a template field");
        }
    }
}
```

#### Tipps zur Fehlersuche
- Überprüfen Sie den Dateipfad und stellen Sie sicher, dass das Dokument zugänglich ist.  
- Testen Sie Ihren regulären Ausdruck mit einem Tool wie regex101.com, bevor Sie ihn einbetten.  
- Passen Sie die `Size`‑ und Rand‑Einstellungen in `TemplateLinkedPosition` an, falls das verknüpfte Feld nicht korrekt erfasst wird.

## Praktische Anwendungen
### Praxisnahe Anwendungsfälle
- **Rechnungsbearbeitung** – automatisch Rechnungsnummern, Daten, Steuern und Gesamtsummen für Buchhaltungssysteme extrahieren.  
- **Vertragsmanagement** – Parteien, Wirksamkeitsdaten und wichtige Klauseln extrahieren.  
- **Kundendatenextraktion** – Bestelldetails aus ausgefüllten Formularen ziehen.

### Integrationsmöglichkeiten
Kombinieren Sie die extrahierten Daten mit ERP‑ oder CRM‑Plattformen, um End‑zu‑End‑automatisierte Workflows zu erstellen.

## Tipps zur Batch‑Dokumentenverarbeitung
Beim Umgang mit **Batch‑Dokumentenverarbeitung** sollten Sie Folgendes beachten:
- Wiederverwenden einer einzelnen `Parser`‑Instanz für mehrere Dateien, um den Aufwand zu reduzieren.  
- Ausführen von Parsing‑Aufgaben in parallelen Streams oder Executor‑Services.  
- Speichern der extrahierten Ergebnisse in einer Datenbank oder CSV für nachgelagerte Berichte.

## Leistungsüberlegungen
- **Vorlagen vereinfachen** – weniger Felder und einfachere Regex‑Muster beschleunigen das Parsen.  
- **Speicher verwalten** – schließen Sie `Parser`‑Objekte umgehend (wie mit try‑with‑resources gezeigt).  
- **In Batches verarbeiten** – Dokumente gruppieren, um CPU‑ und I/O‑Nutzung auszubalancieren.

## Häufig gestellte Fragen

**Q: Was ist GroupDocs.Parser für Java?**  
A: Es ist eine Java‑Bibliothek, die strukturierte Daten aus PDFs, Word‑Dokumenten, Bildern und mehr mithilfe anpassbarer Vorlagen extrahiert.

**Q: Wie richte ich ein Maven‑Projekt mit GroupDocs.Parser ein?**  
A: Fügen Sie das im Maven‑Block oben gezeigte Repository und `<dependency>` zu Ihrer `pom.xml` hinzu.

**Q: Kann ich GroupDocs.Parser ohne Kauf einer Lizenz nutzen?**  
A: Ja, Sie können mit einer kostenlosen Testversion beginnen oder für Evaluierungszwecke eine temporäre Lizenz erhalten.

**Q: Was sind verknüpfte Felder in Vorlagen?**  
A: Verknüpfte Felder sind Vorlagenelemente, deren Position relativ zu einem anderen Feld definiert ist, wodurch eine präzise Extraktion basierend auf dem Layout ermöglicht wird.

**Q: Wie kann ich die Lösung für Tausende von Rechnungen skalieren?**  
A: Implementieren Sie Batch‑Dokumentenverarbeitung, wiederverwenden Sie Parser‑Instanzen und erwägen Sie Multithreading, um große Mengen effizient zu verarbeiten.

## Fazit
Durch das Befolgen dieser Anleitung wissen Sie jetzt, wie man **Rechnungsdaten** mit Java Parsing **extrahiert**, reguläre Ausdrücke nutzt und **verknüpfte Felder** erstellt, die sich an jedes Rechnungslayout anpassen. Experimentieren Sie mit verschiedenen Vorlagen, integrieren Sie die Ausgabe in Ihre Finanz‑Infrastruktur und erkunden Sie erweiterte Funktionen wie benutzerdefinierte Datenkonverter und OCR‑Unterstützung.

---

**Zuletzt aktualisiert:** 2026-02-11  
**Getestet mit:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs