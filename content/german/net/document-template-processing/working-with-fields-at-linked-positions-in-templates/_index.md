---
title: Arbeiten mit Feldern an verknüpften Positionen in Vorlagen
linktitle: Arbeiten mit Feldern an verknüpften Positionen in Vorlagen
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET effizient Daten aus Dokumenten extrahieren. Schritt-für-Schritt-Anleitung mit Codebeispielen.
type: docs
weight: 12
url: /de/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## Einführung
GroupDocs.Parser für .NET ist eine robuste Bibliothek, die das Parsen von Dokumenten und die Datenextraktion erleichtert. Sie unterstützt eine Vielzahl von Dateiformaten, darunter PDF, DOCX, XLSX und mehr. Eines ihrer wichtigsten Features ist die vorlagenbasierte Datenextraktion, mit der Sie Felder in einem Dokument definieren und bestimmte Daten basierend auf diesen vordefinierten Vorlagen extrahieren können.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Grundlegende Kenntnisse der C#-Programmierung
- Visual Studio auf Ihrem System installiert
-  GroupDocs.Parser für .NET-Bibliothek (Download von[Hier](https://releases.groupdocs.com/parser/net/))
- Beispieldokumentdateien zum Arbeiten

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
## Schritt 1: Vorlagenfelder definieren
Definieren Sie zunächst die Vorlagenfelder mit regulären Ausdrücken und verknüpften Positionen:
```csharp
// Definieren Sie ein Feld mit einem regulären Ausdruck
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Definieren Sie ein verknüpftes Feld mit bestimmten Positionseinstellungen
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Schritt 2: Erstellen Sie eine Vorlage
Erstellen Sie als Nächstes eine Vorlage mit den definierten Feldern:
```csharp
// Erstellen Sie eine Vorlage mit den definierten Feldern
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Schritt 3: Dokument mit Vorlage analysieren
 Initialisieren Sie nun den`Parser` Klasse und analysieren Sie das Dokument mithilfe der Vorlage:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analysieren Sie das Dokument anhand der Vorlage
    DocumentData data = parser.ParseByTemplate(template);
    // Durch extrahierte Daten iterieren und Ergebnisse drucken
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Abschluss
GroupDocs.Parser für .NET vereinfacht das Extrahieren strukturierter Daten aus Dokumenten mithilfe von Vorlagen. Durch das Definieren von Feldern und Anwenden von Vorlagen können Sie relevante Informationen effizient extrahieren und so die Automatisierung und Produktivität bei der Dokumentenverarbeitung verbessern.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Daten aus verschlüsselten PDF-Dateien extrahieren?
Ja, GroupDocs.Parser unterstützt das Parsen verschlüsselter PDF-Dateien, indem während des Parsens das Kennwort angegeben wird.
### Welche Dateiformate werden für die vorlagenbasierte Extraktion unterstützt?
GroupDocs.Parser unterstützt eine Vielzahl von Dateiformaten, darunter PDF, DOCX, XLSX, PPTX, TXT und mehr.
### Gibt es eine Testversion für GroupDocs.Parser?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Kann ich GroupDocs.Parser zur Stapelverarbeitung von Dokumenten verwenden?
Ja, GroupDocs.Parser ermöglicht die Stapelverarbeitung, um mehrere Dokumente gleichzeitig zu analysieren.
### Wo erhalte ich technischen Support für GroupDocs.Parser?
 Technischen Support und die Möglichkeit, sich mit der Community auszutauschen finden Sie unter[GroupDocs-Forum](https://forum.groupdocs.com/c/parser/17).