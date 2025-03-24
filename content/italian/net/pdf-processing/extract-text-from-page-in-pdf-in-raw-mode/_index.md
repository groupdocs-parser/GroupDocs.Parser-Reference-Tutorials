---
title: Estrai testo dalla pagina in PDF in modalità Raw
linktitle: Estrai testo dalla pagina in PDF in modalità Raw
second_title: API GroupDocs.Parser .NET
description: Estrai testo da PDF utilizzando GroupDocs.Parser in C#. Scopri un'estrazione efficiente del testo PDF con questa potente libreria .NET.
weight: 16
url: /it/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# Estrai testo dalla pagina in PDF in modalità Raw

## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per estrarre testo dalle pagine dei documenti PDF utilizzando la modalità raw. GroupDocs.Parser è un potente strumento che consente agli sviluppatori di lavorare a livello di codice con vari formati di documenti.
## Prerequisiti
Prima di iniziare questo tutorial, assicurati di avere quanto segue:
- Visual Studio installato sul tuo computer.
- Conoscenza base della programmazione C#.
- GroupDocs.Parser per la libreria .NET, che puoi[scarica qui](https://releases.groupdocs.com/parser/net/).
- Un file PDF di esempio a scopo di test.

## Importa spazi dei nomi
Innanzitutto, assicurati di importare gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: creare un'istanza della classe parser
 Per iniziare, istanziare il file`Parser`class fornendo il percorso del file PDF di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il tuo codice va qui
}
```
## Passaggio 2: ottieni informazioni sul documento e ripeti le pagine
Successivamente, recupera le informazioni del documento ed esegui l'iterazione su ciascuna pagina per estrarre il testo.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Il tuo codice per l'estrazione del testo va qui
}
```
## Passaggio 3: estrai il testo da ciascuna pagina
 All'interno del ciclo, utilizzare il file`GetText` metodo per estrarre il testo da ogni pagina e stamparlo.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusione
 In questo tutorial, abbiamo imparato come estrarre testo dalle pagine PDF in modalità raw utilizzando GroupDocs.Parser per .NET. Questo processo prevede la creazione di un file`Parser` esempio, ottenendo informazioni sul documento, scorrendo ogni pagina ed estraendo il testo utilizzando il file`GetText` metodo.

## Domande frequenti
### Cos'è GroupDocs.Parser per .NET?
GroupDocs.Parser per .NET è un'API di analisi dei documenti che consente agli sviluppatori di estrarre testo, metadati e altre informazioni da vari formati di file a livello di codice.
### Come posso scaricare GroupDocs.Parser per .NET?
 È possibile scaricare la libreria da[Sito web di GroupDocs](https://releases.groupdocs.com/parser/net/).
### È disponibile una prova gratuita?
 Sì, puoi accedere a una prova gratuita di GroupDocs.Parser per .NET da[Qui](https://releases.groupdocs.com/).
### Dove posso trovare supporto per GroupDocs.Parser per .NET?
 Per assistenza tecnica e supporto comunitario, visitare il[Forum di GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Come posso acquistare una licenza per GroupDocs.Parser per .NET?
 È possibile acquistare una licenza da[pagina di acquisto](https://purchase.groupdocs.com/buy) o acquisire una licenza temporanea[Qui](https://purchase.groupdocs.com/temporary-license/).