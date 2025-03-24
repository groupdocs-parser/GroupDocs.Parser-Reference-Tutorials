---
title: Estrai testo da un documento Excel come HTML
linktitle: Estrai testo da un documento Excel come HTML
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre testo da documenti Excel e convertirlo in HTML utilizzando GroupDocs.Parser per .NET.
weight: 13
url: /it/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per estrarre testo da un documento Excel e convertirlo in formato HTML. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di lavorare con vari formati di documenti, estraendo testo e metadati in modo efficiente.
## Prerequisiti
Prima di iniziare, assicurati di avere la seguente configurazione:
- Visual Studio installato nel sistema.
- Conoscenza di base della programmazione C#.
-  Libreria GroupDocs.Parser per .NET. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/parser/net/).
## Importa spazi dei nomi
Inizia includendo gli spazi dei nomi necessari nel tuo progetto C# per accedere alle funzionalità GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: creare un'istanza della classe parser
 Innanzitutto, istanziare il file`Parser` classe fornendo il percorso del documento Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Ulteriore codice andrà qui
}
```
 Sostituire`"YourSampleFile.xlsx"` con il percorso del file Excel.
## Passaggio 2: estrai il testo come HTML
 All'interno del`using` blocco del`Parser` ad esempio, utilizzare il file`GetFormattedText` metodo per estrarre testo formattato in modalità HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Ulteriore codice andrà qui
    }
}
```
## Passaggio 3: leggere e stampare il testo HTML estratto
 Successivamente, leggi il testo HTML estratto dal file`TextReader` e stamparlo sulla console.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Una volta eseguito, questo codice estrarrà il testo dal documento Excel e lo visualizzerà in formato HTML nella console.
## Conclusione
In questo tutorial, abbiamo imparato come utilizzare GroupDocs.Parser per .NET per estrarre testo da un documento Excel e convertirlo in formato HTML. Questa libreria fornisce un modo semplice per lavorare con vari formati di documenti, consentendo agli sviluppatori di gestire in modo efficiente le attività di estrazione del testo nelle loro applicazioni.

## Domande frequenti
### GroupDocs.Parser può gestire altri formati di documenti oltre a Excel?
Sì, GroupDocs.Parser supporta un'ampia gamma di formati di file tra cui PDF, Word, PowerPoint e altri.
### GroupDocs.Parser è compatibile con .NET Core?
Sì, GroupDocs.Parser è compatibile sia con .NET Framework che con .NET Core.
### GroupDocs.Parser preserva la formattazione durante l'estrazione del testo?
Sì, GroupDocs.Parser può preservare la formattazione come caratteri, stili e layout durante l'estrazione del testo.
### Posso estrarre metadati dai documenti utilizzando GroupDocs.Parser?
Sì, GroupDocs.Parser consente di estrarre metadati come autore, data di creazione e altro dai tipi di documenti supportati.
### È disponibile una prova gratuita per GroupDocs.Parser?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).