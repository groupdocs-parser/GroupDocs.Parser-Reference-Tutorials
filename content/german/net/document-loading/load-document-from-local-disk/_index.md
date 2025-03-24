---
title: Dokument von der lokalen Festplatte laden
linktitle: Dokument von der lokalen Festplatte laden
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus verschiedenen Dokumentformaten extrahieren. Einfache und effiziente Textextraktion mit C#.
weight: 11
url: /de/net/document-loading/load-document-from-local-disk/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Dokumenten extrahieren. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler verschiedene Dokumentformate analysieren und Textinhalte programmgesteuert extrahieren können. Wir erläutern die erforderlichen Schritte, um mit der Textextraktion mithilfe dieser Bibliothek zu beginnen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen installiert sind:
- Visual Studio ist auf Ihrem System installiert.
- Grundkenntnisse der Programmiersprache C#.
-  GroupDocs.Parser für .NET-Bibliothek installiert (Download[Hier](https://releases.groupdocs.com/parser/net/)).

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Schritt 1: Dokument von der lokalen Festplatte laden
 Laden Sie zunächst ein Dokument von Ihrer lokalen Festplatte. Ersetzen Sie`"Your Sample File"` durch den Pfad zu Ihrem Zieldokument.
```csharp
// Legen Sie den Dateipfad fest
string filePath = "Your Sample File";
// Erstellen Sie eine Instanz der Parser-Klasse mit dem Dateipfad
using (Parser parser = new Parser(filePath))
{
    // Extrahieren Sie Text in den Reader
    using (TextReader reader = parser.GetText())
    {
        //Drucken Sie den extrahierten Text aus dem Dokument
        // Wenn die Textextraktion nicht unterstützt wird, ist der Reader null
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Erläuterung der Schritte
1. Festlegen des Dateipfads: Geben Sie zunächst den Pfad zu dem Dokument an, aus dem Sie Text extrahieren möchten (`filePath` Variable).
2.  Parserinstanz erstellen: Instanziieren Sie die`Parser` Klasse durch Bestehen der`filePath`.
3.  Text extrahieren: Verwenden Sie die`GetText()` Methode der`Parser` Instanz, um eine`TextReader` Objekt, das den extrahierten Text aus dem Dokument enthält.
4.  Lesen von extrahiertem Text: Nutzen Sie die`ReadToEnd()` Methode der`TextReader` um den gesamten aus dem Dokument extrahierten Textinhalt abzurufen.
5.  Umgang mit nicht unterstützten Formaten: Wenn das Dokumentformat keine Textextraktion unterstützt,`reader` Objekt wird`null`, und Sie können dieses Szenario entsprechend handhaben.

## Abschluss
In diesem Tutorial haben wir die ersten Schritte zum Extrahieren von Text aus einem Dokument mithilfe von GroupDocs.Parser für .NET behandelt. Diese Bibliothek bietet umfangreiche Funktionen zum Parsen von Dokumenten, sodass Entwickler in ihren Anwendungen effizient mit verschiedenen Dateiformaten arbeiten können.

## Häufig gestellte Fragen
### Ist GroupDocs.Parser mit allen Dokumentformaten kompatibel?
GroupDocs.Parser unterstützt eine breite Palette von Formaten, darunter PDF, Microsoft Office-Dokumente (Word, Excel, PowerPoint) und mehr.
### Kann ich mit GroupDocs.Parser Metadaten zusammen mit Text extrahieren?
Ja, GroupDocs.Parser ermöglicht die Extraktion von Textinhalten und Metadaten aus unterstützten Dokumentformaten.
### Wo finde ich weitere Ressourcen und Support für GroupDocs.Parser?
 Besuche den[GroupDocs.Parser-Dokumentation](https://tutorials.groupdocs.com/parser/net/) für eine detaillierte API-Referenz und erkunden Sie die[GroupDocs Forum](https://forum.groupdocs.com/c/parser/17) für die Unterstützung der Community.
### Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 Sie können eine[vorläufige Lizenz](https://purchase.groupdocs.com/temporary-license/) zu Evaluierungs- und Testzwecken.
### Gibt es eine kostenlose Testversion für GroupDocs.Parser?
 Ja, Sie können ein[Kostenlose Testphase](https://releases.groupdocs.com/) Version von GroupDocs.Parser.