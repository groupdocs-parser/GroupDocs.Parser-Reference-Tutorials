---
title: Formatierten Text aus Dokument extrahieren
linktitle: Formatierten Text aus Dokument extrahieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET formatierten Text aus Dokumenten extrahieren. Einfache und effiziente Textextraktion für Ihre Anwendungen.
weight: 10
url: /de/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET formatierten Text aus verschiedenen Dokumenttypen extrahieren. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler auf einfache und effiziente Weise mit Dokumenten arbeiten können. Am Ende dieses Handbuchs können Sie Textextraktionsfunktionen nahtlos in Ihre .NET-Anwendungen integrieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem System installiert ist.
-  GroupDocs.Parser für .NET: Laden Sie die GroupDocs.Parser-Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/parser/net/).
- Dokumentbeispiele: Bereiten Sie Beispieldokumente (z. B. PDF, DOCX) für die Textextraktion vor.
## Namespaces importieren
Fügen Sie zunächst die erforderlichen Namespaces in Ihren C#-Code ein:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Beginnen Sie mit der Initialisierung eines`Parser` Objekt durch den Pfad zu Ihrem Beispieldokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Der Code zur Textextraktion kommt hier rein
}
```
 Ersetzen`"YourSampleFile.pdf"` durch den Pfad zu Ihrer Dokumentdatei.

## Schritt 2: Formatierten Text extrahieren
 Innerhalb der`using` Block, verwenden Sie die`GetFormattedText` Methode, um formatierten Text aus dem Dokument zu extrahieren. Geben Sie das gewünschte Ausgabeformat (z. B. HTML) an mit`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extrahieren Sie formatierten Text in den Reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Überprüfen Sie, ob die Extraktion unterstützt wird
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Lesen und Anzeigen des extrahierten Textes
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Abschluss
Herzlichen Glückwunsch! Sie haben gelernt, wie Sie mit GroupDocs.Parser für .NET formatierten Text aus Dokumenten extrahieren. Diese vielseitige Bibliothek eröffnet Möglichkeiten zur Textverarbeitung und -analyse in Ihren Anwendungen.

## Häufig gestellte Fragen
### F: Kann GroupDocs.Parser Text aus passwortgeschützten Dokumenten extrahieren?
A: Ja, GroupDocs.Parser unterstützt das Extrahieren von Text aus passwortgeschützten Dokumenten.
### F: Welche Dokumentformate werden von GroupDocs.Parser unterstützt?
A: GroupDocs.Parser unterstützt eine Vielzahl von Formaten, darunter PDF, DOCX, XLSX, PPTX und mehr.
### F: Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 A: Sie erhalten eine temporäre Lizenz von[Hier](https://purchase.groupdocs.com/temporary-license/).
### F: Bietet GroupDocs.Parser Unterstützung für die Bildextraktion aus Dokumenten?
A: Ja, GroupDocs.Parser unterstützt neben der Textextraktion auch die Bildextraktion.
### F: Wo kann ich zusätzliche Unterstützung finden oder Fragen zu GroupDocs.Parser stellen?
 A: Besuchen Sie die[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17)für Unterstützung und Diskussionen.