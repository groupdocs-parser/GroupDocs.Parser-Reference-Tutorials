---
title: Estrai tabelle dalla pagina del documento
linktitle: Estrai tabelle dalla pagina del documento
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre tabelle dai documenti a livello di codice utilizzando GroupDocs.Parser per .NET. Questo tutorial completo fornisce una guida passo passo.
weight: 11
url: /it/net/table-extraction/extract-tables-from-document-page/
type: docs
---
# Estrai tabelle dalla pagina del documento

## introduzione
In questo tutorial esploreremo come estrarre tabelle da una pagina di documento utilizzando GroupDocs.Parser per .NET. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di lavorare con vari formati di documenti come PDF, DOCX, XLSX e altri. Sfruttando le sue funzionalità, possiamo estrarre in modo efficiente dati strutturati come tabelle da questi documenti, consentendoci di manipolare e analizzare le informazioni in modo programmatico.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Visual Studio installato sul tuo computer.
- Conoscenza di base dello sviluppo C# e .NET.
-  GroupDocs.Parser per la libreria .NET. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/parser/net/).
- Accesso a un documento di esempio (PDF, DOCX, ecc.) contenente tabelle per l'estrazione.

## Importa spazi dei nomi
Innanzitutto, inizia importando gli spazi dei nomi necessari nel tuo progetto C#:
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
 Istanziare il`Parser` class fornendo il percorso del documento di esempio:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Il tuo codice continua qui...
}
```
## Passaggio 2: verificare il supporto per l'estrazione della tabella documenti
Prima di procedere, verifica se il documento supporta l'estrazione della tabella:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Passaggio 3: definire il layout della tabella
Definire il layout delle tabelle da estrarre dal documento. Specifica la larghezza delle colonne e l'altezza delle righe in base alla struttura del documento:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Larghezze delle colonne
    new double[] { 325, 340, 365, 395 });         // Altezze delle file
```
## Passaggio 4: configurare le opzioni di estrazione della tabella
Crea opzioni per l'estrazione della tabella utilizzando il layout specificato:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Passaggio 5: recuperare le informazioni sul documento
Recupera informazioni sul documento, incluso il numero di pagine:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Passaggio 6: scorrere le pagine del documento
Scorri ogni pagina del documento per estrarre le tabelle:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Estrai tabelle dalla pagina corrente
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Itera sulle tabelle estratte
    foreach (PageTableArea table in tables)
    {
        // Iterare sulle righe della tabella
        for (int row = 0; row < table.RowCount; row++)
        {
            // Itera sulle colonne della tabella
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Ottieni la cella della tabella
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Stampa il testo della cella della tabella
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Conclusione
In questo tutorial, abbiamo trattato il processo di estrazione delle tabelle dalle pagine dei documenti utilizzando GroupDocs.Parser per .NET. Seguendo i passaggi forniti, puoi integrare perfettamente la funzionalità di estrazione delle tabelle nelle tue applicazioni .NET, consentendo una gestione e manipolazione efficiente dei dati strutturati all'interno dei documenti.

## Domande frequenti
### GroupDocs.Parser può estrarre tabelle da tutti i tipi di documenti?
GroupDocs.Parser supporta vari formati di documenti come PDF, DOCX, XLSX e altri, consentendo l'estrazione di tabelle da tipi di file compatibili.
### GroupDocs.Parser per .NET è adatto per l'elaborazione di documenti su larga scala?
Sì, GroupDocs.Parser è progettato per gestire documenti di grandi dimensioni in modo efficiente, rendendolo adatto all'elaborazione di set di dati estesi.
### GroupDocs.Parser preserva la formattazione durante l'estrazione della tabella?
Sì, GroupDocs.Parser conserva i dettagli di formattazione come bordi delle celle, stili di testo e allineamenti durante l'estrazione della tabella.
### Posso estrarre tabelle specifiche in base a criteri di contenuto?
GroupDocs.Parser offre opzioni flessibili per indirizzare tabelle specifiche in base a modelli di layout o condizioni di contenuto per l'estrazione.
### GroupDocs.Parser è compatibile con .NET Core?
Sì, GroupDocs.Parser è compatibile sia con gli ambienti .NET Framework che .NET Core.