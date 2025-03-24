---
title: Bilder aus Dokument extrahieren
linktitle: Bilder aus Dokument extrahieren
second_title: GroupDocs.Parser .NET API
description: Extrahieren Sie mühelos Bilder aus Dokumenten mit GroupDocs.Parser für .NET. Ihre Dokumentverarbeitungsfunktionen und die Optimierung von Bildextraktionsaufgaben sind effizient.
weight: 11
url: /de/net/image-extraction/extract-images-from-document/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Bilder aus Dokumenten extrahieren. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler Text, Metadaten, Bilder und mehr aus verschiedenen Dokumentformaten extrahieren können.
## Voraussetzungen
Stellen Sie vor dem Beginn sicher, dass die folgenden Voraussetzungen erfüllt sind:
- Visual Studio: Installieren Sie Visual Studio auf Ihrem Computer.
-  GroupDocs.Parser für .NET: Laden Sie GroupDocs.Parser herunter und installieren Sie es von der[Download-Seite](https://releases.groupdocs.com/parser/net/).
- Beispieldokument: Bereiten Sie ein Beispieldokument (PDF, DOCX usw.) vor, aus dem Sie Bilder extrahieren möchten.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Erstellen Sie zunächst eine Instanz des`Parser` Klasse, indem Sie den Pfad zu Ihrem Beispieldokument angeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ihr Code kommt hier rein
}
```
 Ersetzen`"YourSampleFile.pdf"` durch den Pfad zu Ihrer Dokumentdatei.
## Schritt 2: Bilder aus dem Dokument extrahieren
 Als nächstes extrahieren Sie Bilder aus dem Dokument mit dem`GetImages()` Methode.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 Der`GetImages()` Methode gibt eine Sammlung von`PageImageArea` Objekte, die im Dokument gefundene Bilder darstellen.
## Schritt 3: Überprüfen Sie die Unterstützung für die Bildextraktion
Überprüfen Sie vor dem Durchlaufen der Bilder, ob die Bildextraktion für das Dokument unterstützt wird.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Dieser Schritt stellt sicher, dass das Dokument extrahierbare Bilder enthält.
## Schritt 4: Über extrahierte Bilder iterieren
Iterieren Sie nun über die extrahierten Bilder, um auf ausführliche Informationen zu jedem Bild zuzugreifen, etwa Seitenindex, Rechteckkoordinaten und Bildtyp.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Diese Schleife druckt Informationen zu jedem extrahierten Bild aus, einschließlich Speicherort und Typ.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Parser für .NET Bilder programmgesteuert aus Dokumenten extrahiert. Indem Sie diese Schritte befolgen, können Sie die Funktion zur Dokumentbildextraktion nahtlos in Ihre .NET-Anwendungen integrieren.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Bilder aus allen Dokumentformaten extrahieren?
GroupDocs.Parser unterstützt das Extrahieren von Bildern aus verschiedenen Formaten, darunter PDF, DOCX, XLSX und mehr.
### Gibt es eine kostenlose Testversion für GroupDocs.Parser?
 Ja, Sie können eine kostenlose Testversion von GroupDocs.Parser über die[Webseite](https://releases.groupdocs.com/).
### Wo finde ich Dokumentation für GroupDocs.Parser?
 Eine ausführliche Dokumentation zu GroupDocs.Parser finden Sie[Hier](https://tutorials.groupdocs.com/parser/net/).
### Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 Eine vorläufige Lizenz erhalten Sie bei der[Seite mit der temporären Lizenz](https://purchase.groupdocs.com/temporary-license/).
### Wo erhalte ich Support für GroupDocs.Parser?
 Technischen Support und Hilfe erhalten Sie im[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17).