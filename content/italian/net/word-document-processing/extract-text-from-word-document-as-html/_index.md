---
title: Estrai testo da un documento Word come HTML
linktitle: Estrai testo da un documento Word come HTML
second_title: API GroupDocs.Parser .NET
description: Scopri come utilizzare GroupDocs.Parser per .NET per estrarre testo da documenti Word e salvarlo come HTML. Tutorial passo passo con esempi di codice.
weight: 16
url: /it/net/word-document-processing/extract-text-from-word-document-as-html/
---
## introduzione
GroupDocs.Parser per .NET è una potente libreria di analisi dei documenti che consente agli sviluppatori di estrarre testo e metadati da vari formati di file senza problemi. In questo tutorial, ci concentreremo sull'utilizzo di GroupDocs.Parser per estrarre testo da documenti Word e salvarlo come HTML. Questo processo è essenziale per attività come l'analisi dei contenuti, l'indicizzazione o la conversione di documenti in formati web-friendly. Al termine di questa guida avrai una chiara comprensione di come utilizzare GroupDocs.Parser in modo efficiente nelle tue applicazioni .NET.
## Prerequisiti
Prima di immergerti in questo tutorial, assicurati di possedere i seguenti prerequisiti:
- Conoscenza base della programmazione C#.
- Visual Studio installato nel computer di sviluppo.
-  GroupDocs.Parser per la libreria .NET. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/parser/net/).
- Accesso a un documento Word di esempio a scopo di test.
## Importa spazi dei nomi
Per iniziare, devi importare gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Segui questi passaggi dettagliati per estrarre il testo da un documento Word e salvarlo come HTML utilizzando GroupDocs.Parser per .NET:
## Passaggio 1: creare un'istanza della classe parser
 Innanzitutto, crea un'istanza di`Parser` class fornendo il percorso del documento Word di esempio:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Continua al passaggio 2...
}
```
 Sostituire`"YourSampleFile.docx"`con il percorso del documento Word.
## Passaggio 2: estrai il testo formattato come HTML
 Successivamente, utilizzare il file`GetFormattedText` metodo insieme a`FormattedTextOptions`per estrarre il testo in formato HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Estrarre un testo formattato nel lettore
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Continua al passaggio 3...
    }
}
```
## Passaggio 3: leggere e generare l'HTML estratto
 Infine, leggi il contenuto HTML estratto dal file`TextReader` e stamparlo sulla console:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Estrarre un testo formattato nel lettore
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Stampa il testo formattato come HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Conclusione
In questo tutorial, abbiamo esplorato come utilizzare GroupDocs.Parser per .NET per estrarre testo da un documento Word e salvarlo come HTML. Questa libreria offre un modo semplice ed efficiente per analizzare il contenuto dei documenti, rendendola uno strumento prezioso per le attività di elaborazione dei documenti nelle applicazioni .NET.

## Domande frequenti
### Come posso ottenere una licenza temporanea per GroupDocs.Parser?
 È possibile richiedere una licenza temporanea da[Qui](https://purchase.groupdocs.com/temporary-license/).
### Dove posso trovare ulteriore documentazione per GroupDocs.Parser?
 È disponibile la documentazione dettagliata[Qui](https://tutorials.groupdocs.com/parser/net/).
### È disponibile una prova gratuita per GroupDocs.Parser?
 Sì, puoi accedere alla versione di prova gratuita[Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto per GroupDocs.Parser?
 Visita il forum di supporto[Qui](https://forum.groupdocs.com/c/parser/17).
### Quali tipi di documenti supporta GroupDocs.Parser?
GroupDocs.Parser supporta vari formati di documenti tra cui Word, PDF, Excel, PowerPoint e altri.