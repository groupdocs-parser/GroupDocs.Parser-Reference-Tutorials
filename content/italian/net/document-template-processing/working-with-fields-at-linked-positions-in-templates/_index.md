---
title: Lavorare con i campi nelle posizioni collegate nei modelli
linktitle: Lavorare con i campi nelle posizioni collegate nei modelli
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre i dati in modo efficiente dai documenti utilizzando GroupDocs.Parser per .NET. Tutorial passo passo con esempi di codice.
weight: 12
url: /it/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## introduzione
GroupDocs.Parser per .NET è una solida libreria progettata per facilitare le attività di analisi dei documenti e di estrazione dei dati. Supporta un'ampia gamma di formati di file, inclusi PDF, DOCX, XLSX e altri. Una delle sue caratteristiche principali è l'estrazione dei dati basata su modelli, che consente di definire campi all'interno di un documento ed estrarre dati specifici in base a questi modelli predefiniti.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Conoscenza di base della programmazione C#
- Visual Studio installato nel sistema
-  GroupDocs.Parser per la libreria .NET (scarica da[Qui](https://releases.groupdocs.com/parser/net/))
- File di documenti di esempio con cui lavorare

## Importazione di spazi dei nomi
Inizia includendo gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Passaggio 1: definire i campi del modello
Innanzitutto, definisci i campi del modello utilizzando espressioni regolari e posizioni collegate:
```csharp
// Definire un campo con un'espressione regolare
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Definire un campo collegato con impostazioni di posizione specifiche
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Passaggio 2: crea un modello
Successivamente, crea un modello contenente i campi definiti:
```csharp
// Crea un modello con i campi definiti
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Passaggio 3: analizzare il documento con il modello
 Ora inizializza il file`Parser` class e analizzare il documento utilizzando il modello:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analizzare il documento in base al modello
    DocumentData data = parser.ParseByTemplate(template);
    // Scorri i dati estratti e stampa i risultati
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusione
GroupDocs.Parser per .NET semplifica il processo di estrazione dei dati strutturati dai documenti utilizzando i modelli. Definendo i campi e applicando modelli, puoi estrarre in modo efficiente le informazioni rilevanti, migliorando l'automazione e la produttività nelle attività di elaborazione dei documenti.

## Domande frequenti
### GroupDocs.Parser può estrarre dati da file PDF crittografati?
Sì, GroupDocs.Parser supporta l'analisi di file PDF crittografati fornendo la password durante l'analisi.
### Quali formati di file sono supportati per l'estrazione basata su modelli?
GroupDocs.Parser supporta un'ampia gamma di formati di file tra cui PDF, DOCX, XLSX, PPTX, TXT e altri.
### È disponibile una versione di prova per GroupDocs.Parser?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Posso utilizzare GroupDocs.Parser per l'elaborazione batch di documenti?
Sì, GroupDocs.Parser consente l'elaborazione batch per analizzare più documenti contemporaneamente.
### Dove posso ottenere supporto tecnico per GroupDocs.Parser?
 Puoi cercare supporto tecnico e interagire con la community all'indirizzo[Forum di GroupDocs](https://forum.groupdocs.com/c/parser/17).