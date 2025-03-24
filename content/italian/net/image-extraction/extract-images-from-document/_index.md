---
title: Estrai immagini dal documento
linktitle: Estrai immagini dal documento
second_title: API GroupDocs.Parser .NET
description: Estrai immagini dai documenti senza sforzo utilizzando GroupDocs.Parser per .NET. Le tue capacità di elaborazione dei documenti e semplifica le attività di estrazione delle immagini in modo efficiente.
weight: 11
url: /it/net/image-extraction/extract-images-from-document/
---

# Estrai immagini dal documento

## introduzione
In questo tutorial esploreremo come estrarre immagini dai documenti utilizzando GroupDocs.Parser per .NET. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di estrarre testo, metadati, immagini e altro da vari formati di documenti.
## Prerequisiti
Prima di iniziare, assicurati di aver configurato i seguenti prerequisiti:
- Visual Studio: installa Visual Studio sul tuo computer.
-  GroupDocs.Parser per .NET: scarica e installa GroupDocs.Parser dal file[pagina di download](https://releases.groupdocs.com/parser/net/).
- Documento di esempio: prepara un documento di esempio (PDF, DOCX, ecc.) da cui desideri estrarre le immagini.

## Importa spazi dei nomi
Inizia importando gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Passaggio 1: creare un'istanza della classe parser
 Innanzitutto, crea un'istanza di`Parser` class fornendo il percorso del documento di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il tuo codice va qui
}
```
 Sostituire`"YourSampleFile.pdf"` con il percorso del file del documento.
## Passaggio 2: estrai le immagini dal documento
 Successivamente, estrai le immagini dal documento utilizzando il file`GetImages()` metodo.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 IL`GetImages()` Il metodo restituisce una raccolta di`PageImageArea` oggetti che rappresentano le immagini trovate nel documento.
## Passaggio 3: controlla il supporto per l'estrazione delle immagini
Prima di ripetere le immagini, controlla se l'estrazione delle immagini è supportata per il documento.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Questo passaggio garantisce che il documento contenga immagini estraibili.
## Passaggio 4: ripetere le immagini estratte
Ora, esegui l'iterazione sulle immagini estratte per accedere a informazioni dettagliate su ciascuna immagine, come l'indice della pagina, le coordinate del rettangolo e il tipo di immagine.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Questo ciclo stampa le informazioni su ciascuna immagine estratta, inclusa la sua posizione e tipo.

## Conclusione
In questo tutorial abbiamo imparato come utilizzare GroupDocs.Parser per .NET per estrarre immagini dai documenti a livello di codice. Seguendo questi passaggi è possibile integrare perfettamente la funzionalità di estrazione delle immagini dei documenti nelle applicazioni .NET.

## Domande frequenti
### GroupDocs.Parser può estrarre immagini da tutti i formati di documenti?
GroupDocs.Parser supporta l'estrazione di immagini da vari formati, inclusi PDF, DOCX, XLSX e altri.
### È disponibile una prova gratuita per GroupDocs.Parser?
 Sì, puoi accedere a una prova gratuita di GroupDocs.Parser da[sito web](https://releases.groupdocs.com/).
### Dove posso trovare la documentazione per GroupDocs.Parser?
 È possibile trovare la documentazione dettagliata per GroupDocs.Parser[Qui](https://tutorials.groupdocs.com/parser/net/).
### Come posso ottenere una licenza temporanea per GroupDocs.Parser?
 È possibile ottenere una licenza temporanea da[pagina della licenza temporanea](https://purchase.groupdocs.com/temporary-license/).
### Dove posso ottenere supporto per GroupDocs.Parser?
 Per supporto tecnico e assistenza, visitare il[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).