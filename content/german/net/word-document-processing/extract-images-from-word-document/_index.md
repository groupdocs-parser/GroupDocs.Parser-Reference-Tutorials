---
title: Bilder aus Word-Dokument extrahieren
linktitle: Bilder aus Word-Dokument extrahieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Bilder aus einem Word-Dokument extrahieren. Dieses Tutorial bietet eine Schritt-für-Schritt-Anleitung zum Integrieren von Bildern in Ihr .NET.
weight: 11
url: /de/net/word-document-processing/extract-images-from-word-document/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Bilder aus einem Word-Dokument extrahieren. GroupDocs.Parser ist eine leistungsstarke .NET-Bibliothek, mit der Sie Text, Metadaten, Bilder und mehr aus verschiedenen Dokumentformaten, einschließlich Word (DOCX), analysieren und extrahieren können.
## Voraussetzungen
Stellen Sie vor dem Beginn sicher, dass die folgenden Voraussetzungen erfüllt sind:
- Visual Studio ist auf Ihrem Computer installiert.
- Grundkenntnisse der C#-Programmierung.
- GroupDocs.Parser für .NET-Bibliothek installiert. Sie können es herunterladen von[Hier](https://releases.groupdocs.com/parser/net/).
## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren, um die GroupDocs.Parser-Funktionen nutzen zu können:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Lassen Sie uns nun den Vorgang des Extrahierens von Bildern aus einem Word-Dokument in einfache Schritte unterteilen:
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Sie beginnen mit der Erstellung einer Instanz des`Parser`Klasse, die den Pfad zu Ihrem Word-Dokument als Eingabe bereitstellt.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code zur Bildextraktion kommt hier rein
}
```
## Schritt 2: Bilder aus dem Word-Dokument extrahieren
 Verwenden Sie als nächstes die`GetImages()` Methode der`Parser` Objekt, um Bilder aus dem Dokument zu extrahieren.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Schritt 3: Bildspeicheroptionen festlegen
Geben Sie die Optionen zum Speichern der extrahierten Bilder an. Sie können beispielsweise das Bildformat (z. B. PNG) auswählen und andere Einstellungen konfigurieren.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Schritt 4: Über extrahierte Bilder iterieren und speichern
Durchlaufen Sie jedes extrahierte Bild und speichern Sie es mit den angegebenen Optionen in einer Datei.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Speichern Sie das Bild als PNG-Datei
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Abschluss
In diesem Tutorial haben Sie gelernt, wie Sie mit GroupDocs.Parser für .NET Bilder aus einem Word-Dokument extrahieren. Indem Sie diese Schritte befolgen, können Sie Dokumentanalyse- und Bildextraktionsfunktionen problemlos in Ihre .NET-Anwendungen integrieren.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Bilder aus anderen Dokumentformaten außer Word extrahieren?
Ja, GroupDocs.Parser unterstützt verschiedene Dokumentformate, darunter PDF, PowerPoint, Excel und mehr.
### Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 Eine temporäre Lizenz zu Testzwecken erhalten Sie bei[Hier](https://purchase.groupdocs.com/temporary-license/).
### Wo finde ich weitere Dokumentation zu GroupDocs.Parser für .NET?
 Die vollständige Dokumentation finden Sie[Hier](https://tutorials.groupdocs.com/parser/net/).
### Gibt es eine kostenlose Testversion für GroupDocs.Parser?
 Ja, Sie können die Funktionen von GroupDocs.Parser mit einer kostenlosen Testversion erkunden[Hier](https://releases.groupdocs.com/).
### Wie kann ich Support erhalten oder Fragen zu GroupDocs.Parser stellen?
 Sie können Ihre Fragen auf der[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17).