---
title: Cerca testo per espressione regolare (Regex)
linktitle: Cerca testo per espressione regolare (Regex)
second_title: API GroupDocs.Parser .NET
description: Scopri come cercare testo utilizzando le espressioni regolari nei documenti utilizzando GroupDocs.Parser per .NET. Estrai contenuti specifici senza sforzo.
weight: 23
url: /it/net/text-extraction/search-text-by-regex/
type: docs
---
# Cerca testo per espressione regolare (Regex)

## introduzione
In questo tutorial, approfondiremo l'utilizzo di GroupDocs.Parser per .NET per cercare testo tramite espressione regolare (Regex) all'interno dei documenti. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di estrarre testo e metadati da vari formati di file come PDF, DOCX, XLSX e altri. La ricerca di testo utilizzando le espressioni regolari è particolarmente utile per trovare in modo efficiente modelli o contenuti specifici all'interno dei documenti.
## Prerequisiti
Prima di immergerti in questo tutorial, assicurati di avere quanto segue:
1. Visual Studio: installare l'IDE di Visual Studio per lo sviluppo .NET.
2.  GroupDocs.Parser per .NET: scarica e installa GroupDocs.Parser per .NET da[Qui](https://releases.groupdocs.com/parser/net/).
3. File di esempio: prepara un documento di esempio (PDF, DOCX, ecc.) per testare la funzionalità di ricerca.

## Importa spazi dei nomi
Innanzitutto, inizia includendo gli spazi dei nomi necessari nel codice C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: creare un'istanza della classe parser
 Istanziare il`Parser` class fornendo il percorso del file di esempio:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il codice va qui
}
```
 Sostituire`"YourSampleFile.pdf"` con il percorso del file effettivo.
## Passaggio 2: ricerca utilizzando l'espressione regolare
Definire ed eseguire la ricerca utilizzando un modello di espressione regolare. Ad esempio, per trovare sequenze numeriche (ad esempio numeri interi) all'interno del documento:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 In questo esempio,`[0-9]+` è un modello di espressione regolare che corrisponde a una o più cifre.
## Passaggio 3: controlla il supporto della ricerca
Verifica se l'operazione di ricerca è supportata per il tipo di documento:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Passaggio 4: ripetere i risultati della ricerca
Scorri i risultati della ricerca ed elabora ogni corrispondenza:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Questo ciclo stamperà la posizione e il testo corrispondente trovato all'interno del documento.

## Conclusione
In conclusione, l'utilizzo di GroupDocs.Parser per .NET consente una ricerca di testo efficiente utilizzando espressioni regolari in vari formati di documenti. Seguendo questa guida, gli sviluppatori possono integrare perfettamente l'analisi dei documenti e l'estrazione del testo basata su regex nelle loro applicazioni .NET.

## Domande frequenti
### GroupDocs.Parser può effettuare ricerche all'interno di documenti crittografati?
No, GroupDocs.Parser non può effettuare ricerche all'interno di documenti crittografati o protetti da password.
### GroupDocs.Parser supporta l'OCR (riconoscimento ottico dei caratteri)?
No, GroupDocs.Parser non esegue l'OCR. Si basa sull'estrazione del testo dalla struttura interna del documento.
### Posso cercare modelli complessi utilizzando le espressioni regolari?
Sì, GroupDocs.Parser supporta espressioni regolari complete, consentendo la corrispondenza di modelli complessi all'interno dei documenti.
### Quali formati di documento sono supportati per l'estrazione del testo?
GroupDocs.Parser supporta un'ampia gamma di formati, inclusi PDF, DOCX, XLSX, PPTX e altri.
### GroupDocs.Parser è compatibile con .NET Core?
Sì, GroupDocs.Parser è compatibile con .NET Core per lo sviluppo multipiattaforma.