---
title: Estrai codici a barre dal documento con le opzioni
linktitle: Estrai codici a barre dal documento con le opzioni
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre i codici a barre dai documenti utilizzando GroupDocs.Parser per .NET. Tutorial completo con esempi di codice e domande frequenti.
weight: 14
url: /it/net/barcode-extraction/extract-barcodes-from-document-with-options/
type: docs
---
# Estrai codici a barre dal documento con le opzioni

## introduzione
In questo tutorial, esamineremo il processo di estrazione dei codici a barre da un documento utilizzando GroupDocs.Parser per .NET. GroupDocs.Parser è una potente libreria che ti consente di estrarre testo, metadati e codici a barre da vari formati di documenti come PDF, Microsoft Word, Excel e altri.
## Prerequisiti
Prima di iniziare, assicurati di disporre dei seguenti prerequisiti:
1. Ambiente di sviluppo: assicurati di avere Visual Studio installato sul tuo computer.
2.  Libreria GroupDocs.Parser: scarica e installa la libreria GroupDocs.Parser per .NET da[Qui](https://releases.groupdocs.com/parser/net/).
3. Documento campione: preparare un documento campione (ad esempio, PDF, DOCX) contenente codici a barre per l'estrazione.

## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo progetto C# per utilizzare le funzionalità GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Passaggio 1: creare un'istanza della classe parser
 Per iniziare, crea un'istanza di`Parser` class passando il percorso al documento di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Codice da aggiungere nei passaggi successivi
}
```
## Passaggio 2: verificare il supporto per l'estrazione dei codici a barre
 Successivamente, controlla se il documento supporta l'estrazione del codice a barre utilizzando il file`Features` proprietà del`Parser` esempio.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Passaggio 3: definire le opzioni di estrazione del codice a barre
 Ora, specifica le opzioni per l'estrazione del codice a barre utilizzando`BarcodeOptions`. È possibile impostare parametri quali modalità di qualità e tipi di codici a barre.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Passaggio 4: estrarre i codici a barre dal documento
 Usa il`GetBarcodes` metodo del`Parser` classe per estrarre i codici a barre in base alle opzioni definite.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Passaggio 5: ripetere e visualizzare i codici a barre estratti
Infine, scorri i codici a barre estratti e visualizza l'indice e i valori della pagina.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Conclusione
 In questo tutorial, abbiamo imparato come estrarre i codici a barre da un documento utilizzando GroupDocs.Parser per .NET. Questo processo prevede la creazione di un file`Parser` esempio, definendo le opzioni di estrazione e scorrendo i codici a barre estratti. GroupDocs.Parser semplifica l'attività di estrazione dei codici a barre da vari formati di documenti, consentendo un'elaborazione efficiente dei documenti all'interno delle applicazioni .NET.

## Domande frequenti
### GroupDocs.Parser può estrarre codici a barre da documenti PDF?
Sì, GroupDocs.Parser supporta l'estrazione di codici a barre da documenti PDF insieme ad altri formati come DOCX, XLSX, ecc.
### Quali tipi di codici a barre supporta GroupDocs.Parser?
GroupDocs.Parser supporta vari tipi di codici a barre inclusi i codici QR, Code 39, Code 128 e altri.
### GroupDocs.Parser richiede una licenza per uso commerciale?
 Sì, per l'uso commerciale è necessaria una licenza valida. È possibile ottenere una licenza da[Qui](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser è adatto per l'elaborazione batch di documenti?
Sì, GroupDocs.Parser può gestire in modo efficiente l'elaborazione batch di documenti per l'estrazione di testo, il recupero di metadati e l'estrazione di codici a barre.
### Dove posso trovare supporto tecnico per GroupDocs.Parser?
 È possibile ottenere supporto tecnico o porre domande su[Forum di GroupDocs](https://forum.groupdocs.com/c/parser/17).