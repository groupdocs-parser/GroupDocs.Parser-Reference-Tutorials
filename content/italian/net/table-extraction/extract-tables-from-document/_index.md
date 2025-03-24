---
title: Estrai tabelle dal documento
linktitle: Estrai tabelle dal documento
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre tabelle dai documenti utilizzando Groupdocs.Parser per .NET. Segui la guida dettagliata sull'integrazione di questa funzionalità.
weight: 10
url: /it/net/table-extraction/extract-tables-from-document/
---

# Estrai tabelle dal documento

## introduzione
Groupdocs.Parser per .NET è una libreria completa che facilita l'analisi dei documenti, consentendoti di estrarre informazioni preziose come tabelle, testo, metadati e altro dai documenti. In questo tutorial, ci concentreremo specificamente sull'estrazione di tabelle dai documenti utilizzando l'API Groupdocs.Parser.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Visual Studio installato nel sistema.
- .NET Framework o .NET Core installato.
- Conoscenza base della programmazione C#.

## Importa spazi dei nomi
Innanzitutto, è necessario importare gli spazi dei nomi necessari per accedere alle classi e ai metodi Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Passaggio 1: creare un'istanza della classe parser
 Inizializza una nuova istanza di`Parser` class fornendo il percorso del documento di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Il tuo codice va qui
}
```
## Passaggio 2: verificare il supporto per l'estrazione della tabella
 Verifica se il documento supporta l'estrazione della tabella utilizzando il file`Features` proprietà del`Parser` classe.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Passaggio 3: definire il layout della tabella
Definisci il layout delle tabelle che desideri estrarre utilizzando`TemplateTableLayout`. Specifica la larghezza delle colonne e l'altezza delle righe in base alla struttura del documento.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Passaggio 4: imposta le opzioni di estrazione della tabella
 Creare`PageTableAreaOptions` con il layout definito per specificare come devono essere estratte le tabelle.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Passaggio 5: estrazione delle tabelle
 Utilizza il`GetTables` metodo del`Parser` classe per estrarre le tabelle dal documento in base alle opzioni specificate.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Passaggio 6: iterazione e accesso ai dati della tabella
Scorri le tabelle estratte e le rispettive righe e colonne per accedere ai dati della cella.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Conclusione
In questo tutorial abbiamo spiegato come utilizzare Groupdocs.Parser per .NET per estrarre tabelle dai documenti in modo efficiente. Sfruttando le funzionalità di questa libreria, puoi integrare perfettamente l'estrazione delle tabelle nelle tue applicazioni .NET.

## Domande frequenti
### Groupdocs.Parser può gestire diversi formati di documenti?
Sì, Groupdocs.Parser supporta un'ampia gamma di formati di documenti tra cui DOCX, PDF, XLSX e altri.
### È disponibile una versione di prova per Groupdocs.Parser per .NET?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto per le query relative a Groupdocs.Parser?
 Puoi visitare il[Forum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) per assistenza.
### Dove posso acquistare una licenza per Groupdocs.Parser?
 Puoi acquistare una licenza da[Qui](https://purchase.groupdocs.com/buy).
### Come posso ottenere una licenza temporanea a scopo di valutazione?
 È possibile ottenere una licenza temporanea[Qui](https://purchase.groupdocs.com/temporary-license/).