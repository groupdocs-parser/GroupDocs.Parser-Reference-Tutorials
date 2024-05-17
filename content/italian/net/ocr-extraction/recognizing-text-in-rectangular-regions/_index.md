---
title: Riconoscimento del testo nelle regioni rettangolari
linktitle: Riconoscimento del testo nelle regioni rettangolari
second_title: API GroupDocs.Parser .NET
description: Scopri come riconoscere il testo in aree specifiche dei documenti utilizzando GroupDocs.Parser per .NET con funzionalità OCR.
type: docs
weight: 14
url: /it/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per riconoscere il testo all'interno di specifiche aree rettangolari di documenti. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di estrarre testo, metadati e altro da vari formati di file, inclusi PDF, Word, Excel e PowerPoint.
## Prerequisiti
Prima di iniziare, assicurati di avere la seguente configurazione:
-  GroupDocs.Parser per .NET: scarica e installa la libreria da[Qui](https://releases.groupdocs.com/parser/net/).
- Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE .NET.
- Documento di esempio: disporre di un file di esempio (ad esempio, PDF, DOCX) che contiene testo da riconoscere.

## Importa spazi dei nomi
Innanzitutto, dovrai importare gli spazi dei nomi necessari nel tuo codice C#:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: inizializzare le impostazioni del parser
 Inizia impostando il file`ParserSettings` con il connettore OCR. Qui utilizzeremo il connettore locale Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Passaggio 2: crea un'istanza del parser
 Successivamente, istanziare il file`Parser` classe con le impostazioni precedentemente definite:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Il codice continua qui
}
```
 Sostituire`"YourSampleFile.pdf"` con il percorso del documento.
## Passaggio 3: Definire il rettangolo OCR
 Definire un rettangolo all'interno del documento in cui verrà eseguito il riconoscimento del testo. Ad esempio, un rettangolo che inizia da`(0, 0)` con larghezza`400` e altezza`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Passaggio 4: configura le opzioni di riconoscimento del testo
 Creare`TextOptions` per specificare l'utilizzo dell'OCR insieme al rettangolo definito:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Passaggio 5: estrai il testo utilizzando l'OCR
 Usa il`GetText` metodo del`Parser` istanza con il configurato`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Leggi il testo estratto o gestisci il caso "non supportato".
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Conclusione
In questo tutorial, abbiamo dimostrato come sfruttare GroupDocs.Parser per .NET per estrarre testo da specifiche aree rettangolari nei documenti utilizzando l'OCR. Questo processo può essere ulteriormente personalizzato e integrato in varie applicazioni per attività di estrazione automatizzata del testo.

## Domande frequenti
### GroupDocs.Parser può estrarre testo da documenti scansionati?
Sì, GroupDocs.Parser supporta l'OCR (riconoscimento ottico dei caratteri) per estrarre il testo dai documenti scansionati.
### Quali formati di file supporta GroupDocs.Parser?
GroupDocs.Parser supporta un'ampia gamma di formati di file, inclusi PDF, DOCX, XLSX, PPTX e altri.
### Come posso gestire i documenti che non sono supportati per l'estrazione del testo?
 Puoi verificare se l'estrazione del testo è supportata utilizzando`TextReader` istanza restituita da`parser.GetText(options)`.
### GroupDocs.Parser è adatto per attività di estrazione di testo su larga scala?
Sì, GroupDocs.Parser è progettato per gestire in modo efficiente attività di estrazione di testo su larga scala.
### Dove posso ottenere supporto per i problemi relativi a GroupDocs.Parser?
 Per supporto e discussioni, visitare il[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).