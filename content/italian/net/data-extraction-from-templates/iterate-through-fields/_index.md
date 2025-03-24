---
title: Scorri i campi
linktitle: Scorri i campi
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre dati strutturati dai documenti utilizzando GroupDocs.Parser per .NET. Migliora le tue applicazioni .NET con funzionalità di estrazione dei dati dei documenti.
weight: 11
url: /it/net/data-extraction-from-templates/iterate-through-fields/
---
## introduzione
GroupDocs.Parser per .NET è una potente libreria che consente agli sviluppatori di estrarre dati da vari formati di documenti come PDF, Microsoft Word, Excel e PowerPoint. Questo tutorial ti guiderà attraverso il processo di utilizzo di GroupDocs.Parser per scorrere i campi del documento ed estrarre dati specifici utilizzando i modelli. Al termine di questo tutorial sarai in grado di estrarre in modo efficiente dati strutturati dai documenti nelle tue applicazioni .NET.
## Prerequisiti
Prima di iniziare, assicurati di aver configurato i seguenti prerequisiti:
- Conoscenza base della programmazione C#.
- Visual Studio installato sul tuo computer.
- Libreria GroupDocs.Parser per .NET installata e referenziata nel progetto.

## Importa spazi dei nomi
Per iniziare, aggiungi gli spazi dei nomi necessari al file C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Analizziamo il processo in istruzioni passo passo.
## Passaggio 1: definire i campi del modello
Innanzitutto, definisci i campi che desideri estrarre dal documento utilizzando le espressioni regolari.
```csharp
// Definire un campo "prezzo".
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Definire un campo "e-mail".
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Crea un modello con campi definiti
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
In questo passaggio abbiamo definito due campi: uno per l'estrazione dei prezzi (identificati dal simbolo del dollaro e dalle cifre) e un altro per l'estrazione degli indirizzi email.
## Passaggio 2: analizzare il documento
 Successivamente, utilizzare il file`Parser` classe per analizzare il documento utilizzando il modello definito.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analizzare il documento in base al modello
    DocumentData data = parser.ParseByTemplate(template);
    // Scorrere i dati estratti
    for (int i = 0; i < data.Count; i++)
    {
        // Stampa il nome del campo
        Console.Write(data[i].Name + ": ");
        // Controlla se l'area estratta è testo
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Qui inizializziamo il file`Parser` con il percorso del documento di esempio e quindi analizzare il documento utilizzando il modello definito. Quindi iteriamo attraverso i dati estratti e stampiamo i nomi dei campi insieme al testo estratto.
## Conclusione
In questo tutorial abbiamo esplorato come utilizzare GroupDocs.Parser per .NET per estrarre dati specifici da documenti utilizzando modelli. Sfruttando le espressioni regolari e i modelli, puoi estrarre in modo efficiente informazioni strutturate da vari formati di documenti. Sperimenta diversi modelli e tipi di documenti per soddisfare le tue specifiche esigenze di estrazione.

## Domande frequenti
### GroupDocs.Parser può estrarre dati da documenti scansionati?
Sì, GroupDocs.Parser può estrarre testo e metadati sia da documenti PDF scansionati che ricercabili.
### GroupDocs.Parser è compatibile con le applicazioni .NET Core?
Sì, GroupDocs.Parser supporta .NET Core insieme a .NET Framework.
### Quali formati di documenti supporta GroupDocs.Parser?
GroupDocs.Parser supporta un'ampia gamma di formati tra cui PDF, Microsoft Word, Excel, PowerPoint e altri.
### Come posso gestire documenti di grandi dimensioni con GroupDocs.Parser?
GroupDocs.Parser fornisce opzioni per estrarre dati da pagine o sezioni specifiche di documenti di grandi dimensioni, garantendo un'elaborazione efficiente.
### Posso utilizzare GroupDocs.Parser solo per l'estrazione del testo?
Sì, puoi estrarre contenuto di testo semplice dai documenti utilizzando GroupDocs.Parser senza la necessità di formattazioni complesse.