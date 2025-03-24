---
title: Estrai testo formattato dalla pagina del documento
linktitle: Estrai testo formattato dalla pagina del documento
second_title: API GroupDocs.Parser .NET
description: Estrai testo formattato dalle pagine dei documenti utilizzando GroupDocs.Parser per .NET. Soluzione di estrazione del testo efficiente e affidabile.
weight: 11
url: /it/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## introduzione
In questo tutorial ti guideremo attraverso il processo di estrazione del testo formattato dalle pagine dei documenti utilizzando GroupDocs.Parser per .NET. Questa libreria ti consente di analizzare ed estrarre in modo efficiente il testo da vari formati di documenti come PDF, Word, Excel e altri.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Visual Studio installato nel sistema.
- Conoscenza base della programmazione C#.
-  GroupDocs.Parser per la libreria .NET. Puoi scaricarlo[Qui](https://releases.groupdocs.com/parser/net/).

## Importa spazi dei nomi
Innanzitutto, inizia importando gli spazi dei nomi necessari nel tuo progetto C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Passaggio 1: creare un'istanza della classe parser
 Inizia creando un'istanza di`Parser` class fornendo il percorso del file di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il codice andrà qui
}
```
## Passaggio 2: controlla se l'estrazione del testo formattato è supportata
Prima di procedere con l'estrazione del testo, verificare se il documento supporta l'estrazione del testo formattato.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Passaggio 3: ottieni informazioni sul documento
Recuperare informazioni sul documento, ad esempio il numero di pagine.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Passaggio 4: scorrere le pagine del documento ed estrarre il testo formattato
Scorri ogni pagina del documento ed estrai il testo formattato utilizzando le opzioni specificate (ad esempio, formato Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusione
Ora sai come estrarre testo formattato dalle pagine dei documenti utilizzando GroupDocs.Parser per .NET. Questa libreria fornisce una soluzione potente e facile da usare per l'estrazione del testo da vari formati di file.

## Domande frequenti
### GroupDocs.Parser può gestire diversi formati di file?
Sì, GroupDocs.Parser supporta un'ampia gamma di formati di documenti, inclusi PDF, DOCX, XLSX, PPTX e altri.
### GroupDocs.Parser è compatibile con .NET Core?
Sì, GroupDocs.Parser supporta .NET Core e .NET Framework.
### GroupDocs.Parser preserva la formattazione del testo durante l'estrazione?
Sì, GroupDocs.Parser può mantenere la formattazione come stili e caratteri durante l'estrazione del testo.
### Posso estrarre immagini e metadati utilizzando GroupDocs.Parser?
Sì, GroupDocs.Parser consente l'estrazione di immagini, metadati e testo dai documenti.
### Come posso ottenere supporto per GroupDocs.Parser?
 Puoi ottenere supporto da[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).