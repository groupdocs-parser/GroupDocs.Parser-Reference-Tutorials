---
title: Arbeiten mit Feldern an festen Positionen in Vorlagen
linktitle: Arbeiten mit Feldern an festen Positionen in Vorlagen
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Daten aus Dokumenten extrahieren. Umfassendes Tutorial mit Codebeispielen.
weight: 11
url: /de/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit Feldern an festen Positionen in Vorlagen mithilfe von GroupDocs.Parser für .NET arbeiten. GroupDocs.Parser ist eine leistungsstarke Dokumentanalysebibliothek, mit der Entwickler Daten aus verschiedenen Dokumentformaten wie PDF, Word, Excel und mehr extrahieren können. Insbesondere konzentrieren wir uns auf das Definieren und Verwenden von Vorlagenfeldern, um gezielte Informationen basierend auf ihren festen Positionen zu extrahieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Grundlegende Kenntnisse der C#- und .NET-Entwicklung.
- Visual Studio ist auf Ihrem System installiert.
- GroupDocs.Parser für .NET-Bibliothek installiert. Sie können es herunterladen von[Hier](https://releases.groupdocs.com/parser/net/).
- Beispieldokumentdateien zum Testen.

## Namespaces importieren
Beginnen Sie, indem Sie die erforderlichen Namespaces in Ihr C#-Projekt einbinden:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Schritt 1: Definieren Sie ein Vorlagenfeld
Definieren Sie zunächst ein Feld mit einer festen Position innerhalb einer Vorlage. Dieses Feld stellt den Bereich dar, aus dem Daten extrahiert werden.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Hier:
- `Rectangle` Gibt die Position und Größe des Feldes an.
- `Point(35, 135)` stellt die Koordinaten der oberen linken Ecke dar.
- `Size(100, 10)` definiert die Breite und Höhe des Feldes.
- `"FromCompany"` ist der diesem Feld zugewiesene Name.
## Schritt 2: Erstellen Sie eine Vorlage
Erstellen Sie eine Vorlage mithilfe des definierten Felds.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 Der`Template` Objekt enthält die definierten Felder.
## Schritt 3: Dokument mithilfe der Vorlage analysieren
 Instanziieren Sie den`Parser` Klasse mit dem Zieldokumentpfad und analysieren Sie das Dokument dann mithilfe der erstellten Vorlage.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Durch extrahierte Daten iterieren
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Hier:
- `Parser` wird mit dem Beispieldokumentdateipfad initialisiert.
- `ParseByTemplate` Die Methode wird verwendet, um Daten basierend auf der bereitgestellten Vorlage zu extrahieren.
-  Der Zugriff auf die extrahierten Daten erfolgt über`DocumentData`wobei jedes Element einem definierten Feld entspricht.

## Abschluss
In diesem Tutorial haben wir den Prozess der Arbeit mit Feldern an festen Positionen in Vorlagen mithilfe von GroupDocs.Parser für .NET behandelt. Durch die Definition von Vorlagen mit bestimmten Feldpositionen können Entwickler gezielt Daten aus verschiedenen Dokumentformaten extrahieren.

## Häufig gestellte Fragen
### Ist GroupDocs.Parser mit allen Dokumentformaten kompatibel?
 GroupDocs.Parser unterstützt eine Vielzahl von Dateiformaten, darunter PDF, Microsoft Word, Excel, PowerPoint und mehr. Weitere Informationen finden Sie im[Dokumentation](https://tutorials.groupdocs.com/parser/net/) für eine detaillierte Liste.
### Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 Eine temporäre Lizenz zu Testzwecken erhalten Sie bei[Hier](https://purchase.groupdocs.com/temporary-license/).
### Wo finde ich Unterstützung für GroupDocs.Parser?
 Für technische Unterstützung und Diskussionen besuchen Sie die[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17).
### Kann ich GroupDocs.Parser vor dem Kauf ausprobieren?
 Ja, Sie können die Bibliothek mit einer kostenlosen Testversion erkunden.[Hier](https://releases.groupdocs.com/).
### Wie erwerbe ich eine Lizenz für GroupDocs.Parser?
 Um eine Lizenz zu kaufen, besuchen Sie die[Kaufseite](https://purchase.groupdocs.com/buy).