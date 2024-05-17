---
title: Extrahieren Sie Text aus einem Word-Dokument als HTML
linktitle: Extrahieren Sie Text aus einem Word-Dokument als HTML
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Word-Dokumenten extrahieren und als HTML speichern. Schritt-für-Schritt-Anleitung mit Codebeispielen.
type: docs
weight: 16
url: /de/net/word-document-processing/extract-text-from-word-document-as-html/
---
## Einführung
GroupDocs.Parser für .NET ist eine leistungsstarke Dokumentanalysebibliothek, mit der Entwickler Text und Metadaten nahtlos aus verschiedenen Dateiformaten extrahieren können. In diesem Tutorial konzentrieren wir uns auf die Nutzung von GroupDocs.Parser, um Text aus Word-Dokumenten zu extrahieren und als HTML zu speichern. Dieser Prozess ist für Aufgaben wie Inhaltsanalyse, Indizierung oder Konvertierung von Dokumenten in webfreundliche Formate unerlässlich. Am Ende dieses Handbuchs haben Sie ein klares Verständnis dafür, wie Sie GroupDocs.Parser effizient in Ihren .NET-Anwendungen verwenden können.
## Voraussetzungen
Bevor Sie mit diesem Tutorial beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
- Grundkenntnisse der C#-Programmierung.
- Visual Studio ist auf Ihrem Entwicklungscomputer installiert.
-  GroupDocs.Parser für .NET-Bibliothek. Sie können es herunterladen von[Hier](https://releases.groupdocs.com/parser/net/).
- Zugriff auf ein Beispiel-Word-Dokument zu Testzwecken.
## Namespaces importieren
Zu Beginn müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Befolgen Sie diese detaillierten Schritte, um Text aus einem Word-Dokument zu extrahieren und ihn mit GroupDocs.Parser für .NET als HTML zu speichern:
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Erstellen Sie zunächst eine Instanz des`Parser` Klasse, indem Sie den Pfad zu Ihrem Word-Beispieldokument angeben:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Fahren Sie mit Schritt 2 fort ...
}
```
 Ersetzen`"YourSampleFile.docx"`durch den Pfad zu Ihrem Word-Dokument.
## Schritt 2: Formatierten Text als HTML extrahieren
 Verwenden Sie als nächstes die`GetFormattedText` Methode zusammen mit`FormattedTextOptions`um den Text im HTML-Format zu extrahieren:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extrahieren Sie einen formatierten Text in den Reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Fahren Sie mit Schritt 3 fort ...
    }
}
```
## Schritt 3: Lesen und Ausgeben des extrahierten HTML
 Lesen Sie abschließend den extrahierten HTML-Inhalt aus dem`TextReader` und geben Sie es auf der Konsole aus:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extrahieren Sie einen formatierten Text in den Reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Drucken Sie den formatierten Text als HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Abschluss
In diesem Tutorial haben wir untersucht, wie man mit GroupDocs.Parser für .NET Text aus einem Word-Dokument extrahiert und als HTML speichert. Diese Bibliothek bietet eine einfache und effiziente Möglichkeit, Dokumentinhalte zu analysieren, und ist damit ein unverzichtbares Werkzeug für Dokumentverarbeitungsaufgaben in .NET-Anwendungen.

## Häufig gestellte Fragen
### Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 Sie können eine temporäre Lizenz anfordern bei[Hier](https://purchase.groupdocs.com/temporary-license/).
### Wo finde ich weitere Dokumentation für GroupDocs.Parser?
 Detaillierte Dokumentation ist verfügbar[Hier](https://reference.groupdocs.com/parser/net/).
### Gibt es eine kostenlose Testversion für GroupDocs.Parser?
 Ja, Sie können auf die kostenlose Testversion zugreifen[Hier](https://releases.groupdocs.com/).
### Wie erhalte ich Unterstützung für GroupDocs.Parser?
 Besuchen Sie das Support-Forum[Hier](https://forum.groupdocs.com/c/parser/17).
### Welche Dokumenttypen unterstützt GroupDocs.Parser?
GroupDocs.Parser unterstützt verschiedene Dokumentformate, darunter Word, PDF, Excel, PowerPoint und mehr.