---
title: Dokument aus Stream laden
linktitle: Dokument aus Stream laden
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser Text aus verschiedenen Dokumentformaten in .NET extrahieren. Schritt-für-Schritt-Anleitung mit Codebeispielen.
type: docs
weight: 12
url: /de/net/document-loading/load-document-from-stream/
---
## Einführung
Im Bereich der Dokumentenverarbeitung in .NET-Anwendungen ist das Extrahieren von Text aus verschiedenen Dateiformaten eine häufige Anforderung. GroupDocs.Parser für .NET bietet eine leistungsstarke Lösung zum nahtlosen Parsen und Extrahieren von Text aus einer Vielzahl von Dokumenten. Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess der Verwendung von GroupDocs.Parser zum Extrahieren von Text aus Dokumenten.
## Voraussetzungen
Bevor Sie GroupDocs.Parser für .NET verwenden, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
-  GroupDocs.Parser für .NET-Paket: Laden Sie die GroupDocs.Parser für .NET-Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/parser/net/).
- Dokumentbeispiele: Halten Sie Beispieldokumente für die Textextraktion bereit.
## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr .NET-Projekt, um auf die GroupDocs.Parser-Funktionen zuzugreifen.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Die folgenden Schritte zeigen, wie Sie mit GroupDocs.Parser Text aus einem Dokument aus einem Stream extrahieren.
## Schritt 1: Dokument aus Stream laden
```csharp
// Erstellen des Streams
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Erstellen Sie eine Instanz der Parser-Klasse mit dem Stream
    using (Parser parser = new Parser(stream))
    {
        // Extrahieren Sie Text in den Reader
        using (TextReader reader = parser.GetText())
        {
            // Drucken Sie Text aus dem Dokument
            // Wenn die Textextraktion nicht unterstützt wird, ist der Reader null
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
In diesem Beispiel:
- Wir öffnen einen Dateistream für die Dokumentdatei (`YourSampleFile.docx`).
-  Initialisieren Sie einen`Parser` Instanz mit dem Stream.
-  Verwenden`parser.GetText()` zum Abrufen eines`TextReader` enthält den extrahierten Text.
- Drucken Sie den extrahierten Text oder eine Meldung aus, wenn die Textextraktion für das Dokumentformat nicht unterstützt wird.
## Abschluss
GroupDocs.Parser für .NET vereinfacht die Textextraktion aus verschiedenen Dokumentformaten und ermöglicht Entwicklern, Textinhalte effizient zu verarbeiten und in ihren Anwendungen zu nutzen. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie die Funktionen zur Dokumenttextextraktion nahtlos in Ihre .NET-Projekte integrieren.

## Häufig gestellte Fragen
### Welche Dokumentformate werden von GroupDocs.Parser für .NET unterstützt?
GroupDocs.Parser unterstützt eine breite Palette von Dokumentformaten, darunter DOCX, PDF, XLSX, PPTX, EPUB und mehr.
### Kann GroupDocs.Parser Bilder oder Metadaten aus Dokumenten extrahieren?
Ja, GroupDocs.Parser kann Bilder, Metadaten und Text aus verschiedenen Dokumenttypen extrahieren.
### Ist GroupDocs.Parser mit .NET Core-Anwendungen kompatibel?
Ja, GroupDocs.Parser ist sowohl mit .NET Framework- als auch mit .NET Core-Anwendungen kompatibel.
### Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 Eine vorläufige Lizenz erhalten Sie bei[Hier](https://purchase.groupdocs.com/temporary-license/).
### Wo finde ich weiteren Support oder Dokumentation für GroupDocs.Parser?
 Weitere Unterstützung erhalten Sie im[GroupDocs.Parser Forum](https://forum.groupdocs.com/c/parser/17) oder siehe[Dokumentation](https://reference.groupdocs.com/parser/net/).
