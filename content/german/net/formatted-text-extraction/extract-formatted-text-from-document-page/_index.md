---
title: Extrahieren Sie formatierten Text aus der Dokumentseite
linktitle: Extrahieren Sie formatierten Text aus der Dokumentseite
second_title: GroupDocs.Parser .NET API
description: Extrahieren Sie formatierten Text aus Dokumentseiten mit GroupDocs.Parser für .NET. Effiziente und zuverlässige Textextraktionslösung.
weight: 11
url: /de/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## Einführung
In diesem Tutorial führen wir Sie durch den Prozess des Extrahierens von formatiertem Text aus Dokumentseiten mithilfe von GroupDocs.Parser für .NET. Mit dieser Bibliothek können Sie Text aus verschiedenen Dokumentformaten wie PDF, Word, Excel und mehr effizient analysieren und extrahieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Visual Studio ist auf Ihrem System installiert.
- Grundkenntnisse der C#-Programmierung.
-  GroupDocs.Parser für .NET-Bibliothek. Sie können es herunterladen[Hier](https://releases.groupdocs.com/parser/net/).

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Beginnen Sie mit der Erstellung einer Instanz des`Parser` Klasse, indem Sie den Pfad zu Ihrer Beispieldatei angeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Der Code kommt hierhin
}
```
## Schritt 2: Überprüfen Sie, ob die Extraktion formatierten Textes unterstützt wird
Bevor Sie mit der Textextraktion fortfahren, überprüfen Sie, ob das Dokument die Extraktion formatierten Textes unterstützt.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Schritt 3: Dokumentinformationen abrufen
Rufen Sie Informationen zum Dokument ab, beispielsweise die Seitenanzahl.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Schritt 4: Über Dokumentseiten iterieren und formatierten Text extrahieren
Iterieren Sie durch jede Seite des Dokuments und extrahieren Sie formatierten Text mit angegebenen Optionen (z. B. Markdown-Format).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Abschluss
Jetzt wissen Sie, wie Sie mit GroupDocs.Parser für .NET formatierten Text aus Dokumentseiten extrahieren. Diese Bibliothek bietet eine leistungsstarke und benutzerfreundliche Lösung für die Textextraktion aus verschiedenen Dateiformaten.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser verschiedene Dateiformate verarbeiten?
Ja, GroupDocs.Parser unterstützt eine breite Palette von Dokumentformaten, darunter PDF, DOCX, XLSX, PPTX und mehr.
### Ist GroupDocs.Parser mit .NET Core kompatibel?
Ja, GroupDocs.Parser unterstützt .NET Core und .NET Framework.
### Behält GroupDocs.Parser die Textformatierung während der Extraktion bei?
Ja, GroupDocs.Parser kann beim Extrahieren von Text Formatierungen wie Stile und Schriftarten beibehalten.
### Kann ich mit GroupDocs.Parser Bilder und Metadaten extrahieren?
Ja, GroupDocs.Parser ermöglicht das Extrahieren von Bildern, Metadaten und Text aus Dokumenten.
### Wie kann ich Support für GroupDocs.Parser erhalten?
 Unterstützung erhalten Sie vom[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17).