---
title: Barcodes mit Optionen aus Dokumenten extrahieren
linktitle: Barcodes mit Optionen aus Dokumenten extrahieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Barcodes aus Dokumenten extrahieren. Umfassendes Tutorial mit Codebeispielen und FAQs.
type: docs
weight: 14
url: /de/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## Einführung
In diesem Tutorial führen wir Sie durch den Prozess des Extrahierens von Barcodes aus einem Dokument mithilfe von GroupDocs.Parser für .NET. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Sie Text, Metadaten und Barcodes aus verschiedenen Dokumentformaten wie PDF, Microsoft Word, Excel und mehr extrahieren können.
## Voraussetzungen
Stellen Sie zunächst sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Entwicklungsumgebung: Stellen Sie sicher, dass Visual Studio auf Ihrem Computer installiert ist.
2.  GroupDocs.Parser-Bibliothek: Laden Sie die GroupDocs.Parser-Bibliothek für .NET herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/parser/net/).
3. Beispieldokument: Bereiten Sie ein Beispieldokument (z. B. PDF, DOCX) mit Barcodes zur Extraktion vor.

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren, um die GroupDocs.Parser-Funktionen zu nutzen.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Erstellen Sie zunächst eine Instanz des`Parser` Klasse, indem Sie den Pfad zu Ihrem Beispieldokument übergeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // In den nächsten Schritten hinzuzufügender Code
}
```
## Schritt 2: Überprüfen Sie die Unterstützung für die Barcode-Extraktion
 Überprüfen Sie anschließend, ob das Dokument die Barcode-Extraktion unterstützt. Verwenden Sie dazu`Features` Eigentum der`Parser` Beispiel.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Schritt 3: Optionen zur Barcode-Extraktion festlegen
 Geben Sie nun die Optionen für die Barcode-Extraktion an mit`BarcodeOptions`. Sie können Parameter wie Qualitätsmodi und Barcodetypen festlegen.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Schritt 4: Barcodes aus dem Dokument extrahieren
 Verwenden Sie die`GetBarcodes` Methode der`Parser` Klasse zum Extrahieren von Barcodes basierend auf den definierten Optionen.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Schritt 5: Extrahierte Barcodes iterieren und anzeigen
Zum Schluss durchlaufen Sie die extrahierten Barcodes und zeigen deren Seitenindex und Werte an.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Abschluss
 In diesem Tutorial haben wir gelernt, wie man Barcodes aus einem Dokument mit GroupDocs.Parser für .NET extrahiert. Dieser Prozess beinhaltet die Erstellung eines`Parser` Instanz, Definieren von Extraktionsoptionen und Durchlaufen der extrahierten Barcodes. GroupDocs.Parser vereinfacht die Aufgabe der Barcode-Extraktion aus verschiedenen Dokumentformaten und ermöglicht eine effiziente Dokumentverarbeitung in Ihren .NET-Anwendungen.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Barcodes aus PDF-Dokumenten extrahieren?
Ja, GroupDocs.Parser unterstützt die Barcode-Extraktion aus PDF-Dokumenten sowie anderen Formaten wie DOCX, XLSX usw.
### Welche Barcodetypen unterstützt GroupDocs.Parser?
GroupDocs.Parser unterstützt verschiedene Barcodetypen, darunter QR-Codes, Code 39, Code 128 und mehr.
### Benötigt GroupDocs.Parser eine Lizenz für die kommerzielle Nutzung?
 Ja, für die kommerzielle Nutzung ist eine gültige Lizenz erforderlich. Eine Lizenz erhalten Sie bei[Hier](https://purchase.groupdocs.com/buy).
### Ist GroupDocs.Parser für die Stapelverarbeitung von Dokumenten geeignet?
Ja, GroupDocs.Parser kann die Stapelverarbeitung von Dokumenten zur Textextraktion, zum Abrufen von Metadaten und zur Barcode-Extraktion effizient handhaben.
### Wo finde ich technischen Support für GroupDocs.Parser?
 Technischen Support oder Fragen können Sie über die[GroupDocs-Forum](https://forum.groupdocs.com/c/parser/17).