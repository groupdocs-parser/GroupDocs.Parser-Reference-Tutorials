---
title: Durch Felder iterieren
linktitle: Durch Felder iterieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET strukturierte Daten aus Dokumenten extrahieren. Erweitern Sie Ihre .NET-Anwendungen mit Funktionen zur Dokumentdatenextraktion.
weight: 11
url: /de/net/data-extraction-from-templates/iterate-through-fields/
type: docs
---
# Durch Felder iterieren

## Einführung
GroupDocs.Parser für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler Daten aus verschiedenen Dokumentformaten wie PDF, Microsoft Word, Excel und PowerPoint extrahieren können. Dieses Tutorial führt Sie durch den Prozess der Verwendung von GroupDocs.Parser, um Dokumentfelder zu durchlaufen und mithilfe von Vorlagen bestimmte Daten zu extrahieren. Am Ende dieses Tutorials können Sie strukturierte Daten effizient aus Dokumenten in Ihren .NET-Anwendungen extrahieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
- Grundkenntnisse der C#-Programmierung.
- Visual Studio ist auf Ihrem Computer installiert.
- GroupDocs.Parser für die .NET-Bibliothek ist in Ihrem Projekt installiert und referenziert.

## Namespaces importieren
Fügen Sie zunächst die erforderlichen Namespaces zu Ihrer C#-Datei hinzu:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Lassen Sie uns den Vorgang in Schritt-für-Schritt-Anleitungen aufschlüsseln.
## Schritt 1: Vorlagenfelder definieren
Definieren Sie zunächst mit regulären Ausdrücken die Felder, die Sie aus dem Dokument extrahieren möchten.
```csharp
// Definieren Sie ein "Preis"-Feld
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Definieren Sie ein "E-Mail"-Feld
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Erstellen einer Vorlage mit definierten Feldern
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
In diesem Schritt haben wir zwei Felder definiert: eines zum Extrahieren von Preisen (gekennzeichnet durch das Dollarzeichen und Ziffern) und ein anderes zum Extrahieren von E-Mail-Adressen.
## Schritt 2: Analysieren Sie das Dokument
 Verwenden Sie als nächstes die`Parser` Klasse zum Parsen des Dokuments mithilfe der definierten Vorlage.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analysieren Sie das Dokument anhand der Vorlage
    DocumentData data = parser.ParseByTemplate(template);
    // Durch extrahierte Daten iterieren
    for (int i = 0; i < data.Count; i++)
    {
        // Feldname drucken
        Console.Write(data[i].Name + ": ");
        // Überprüfen Sie, ob der extrahierte Bereich Text ist
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Hier initialisieren wir die`Parser` mit dem Pfad zu Ihrem Beispieldokument und analysieren das Dokument dann mithilfe der definierten Vorlage. Anschließend durchlaufen wir die extrahierten Daten und drucken die Feldnamen zusammen mit dem extrahierten Text.
## Abschluss
In diesem Tutorial haben wir untersucht, wie Sie mit GroupDocs.Parser für .NET bestimmte Daten aus Dokumenten mithilfe von Vorlagen extrahieren können. Durch die Nutzung regulärer Ausdrücke und Vorlagen können Sie strukturierte Informationen effizient aus verschiedenen Dokumentformaten extrahieren. Experimentieren Sie mit verschiedenen Vorlagen und Dokumenttypen, um Ihren spezifischen Extraktionsanforderungen gerecht zu werden.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Daten aus gescannten Dokumenten extrahieren?
Ja, GroupDocs.Parser kann Text und Metadaten sowohl aus gescannten als auch aus durchsuchbaren PDF-Dokumenten extrahieren.
### Ist GroupDocs.Parser mit .NET Core-Anwendungen kompatibel?
Ja, GroupDocs.Parser unterstützt .NET Core zusammen mit .NET Framework.
### Welche Dokumentformate unterstützt GroupDocs.Parser?
GroupDocs.Parser unterstützt eine breite Palette von Formaten, darunter PDF, Microsoft Word, Excel, PowerPoint und mehr.
### Wie kann ich mit GroupDocs.Parser große Dokumente verarbeiten?
GroupDocs.Parser bietet Optionen zum Extrahieren von Daten aus bestimmten Seiten oder Abschnitten großer Dokumente und gewährleistet so eine effiziente Verarbeitung.
### Kann ich GroupDocs.Parser nur zur Textextraktion verwenden?
Ja, Sie können mit GroupDocs.Parser einfachen Textinhalt aus Dokumenten extrahieren, ohne dass eine komplexe Formatierung erforderlich ist.