---
title: Estrai immagini da PDF
linktitle: Estrai immagini da PDF
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre immagini da documenti PDF utilizzando GroupDocs.Parser per .NET. Guida passo passo con esempi di codice.
weight: 12
url: /it/net/pdf-processing/extract-images-from-pdf/
---
## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per estrarre immagini da documenti PDF. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di lavorare con vari formati di documenti, inclusi PDF, DOCX, PPTX e altri, in un ambiente .NET. Seguendo questi passaggi, sarai in grado di estrarre immagini dai file PDF senza sforzo.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
- Visual Studio installato nel sistema
- Conoscenza base della programmazione C#
-  GroupDocs.Parser per la libreria .NET (Scarica[Qui](https://releases.groupdocs.com/parser/net/))

## Importa spazi dei nomi
Per iniziare, includi gli spazi dei nomi necessari nel file di codice C#.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: creare un'istanza della classe parser
 Innanzitutto, crea un'istanza di`Parser`class fornendo il percorso del file PDF di esempio.
```csharp
// Crea un'istanza della classe Parser
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il codice per estrarre le immagini andrà qui
}
```
## Passaggio 2: estrai le immagini dal PDF
 All'interno del`using` bloccare, utilizzare il file`GetImages` metodo del`Parser` istanza per recuperare una raccolta di immagini dal documento PDF.
```csharp
// Estrai immagini dal PDF
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Passaggio 3: configura le opzioni di salvataggio delle immagini
Definire le opzioni per specificare come salvare le immagini estratte. Qui salveremo le immagini in formato PNG.
```csharp
// Crea opzioni per salvare le immagini in formato PNG
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Passaggio 4: ripetere le immagini estratte e salvare
 Scorri ogni immagine nel file`images` raccolta e salvarli in file PNG in sequenza.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Salva l'immagine in un file PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```

## Conclusione
In questo tutorial, abbiamo dimostrato come estrarre immagini da documenti PDF utilizzando GroupDocs.Parser per .NET. Seguendo questi passaggi è possibile integrare perfettamente la funzionalità di estrazione delle immagini nelle applicazioni .NET.

## Domande frequenti
### GroupDocs.Parser è compatibile con altri formati di documenti?
Sì, GroupDocs.Parser supporta un'ampia gamma di formati di documenti, inclusi PDF, DOCX, XLSX, PPTX e altri.
### Posso modificare le opzioni di estrazione delle immagini?
Assolutamente! GroupDocs.Parser fornisce varie opzioni per personalizzare l'estrazione delle immagini, come il formato dell'immagine e le impostazioni di qualità.
### GroupDocs.Parser richiede una licenza per uso commerciale?
 Sì, è necessaria una licenza commerciale per utilizzare GroupDocs.Parser in ambienti di produzione. Saperne di più[Qui](https://purchase.groupdocs.com/buy).
### Dove posso trovare ulteriore supporto o assistenza?
 Visita GroupDocs.Parser[Forum](https://forum.groupdocs.com/c/parser/17) per il supporto e l’orientamento della comunità.
### È disponibile una prova gratuita per GroupDocs.Parser?
 Sì, puoi ottenere una prova gratuita da[Qui](https://releases.groupdocs.com/) per esplorare le funzionalità di GroupDocs.Parser.