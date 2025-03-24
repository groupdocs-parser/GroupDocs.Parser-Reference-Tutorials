---
title: Estrai testo da aree specifiche con opzioni
linktitle: Estrai testo da aree specifiche con opzioni
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre testo da aree specifiche nei documenti utilizzando GroupDocs.Parser per .NET. Esplora le opzioni avanzate di estrazione del testo con questo tutorial.
weight: 14
url: /it/net/text-extraction/extract-text-from-specific-areas-with-options/
---
## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per estrarre testo da aree specifiche all'interno di un documento utilizzando opzioni personalizzabili. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di analizzare ed estrarre testo da vari formati di documenti senza sforzo.
## Prerequisiti
Prima di immergerci nella codifica, assicurati di avere quanto segue:
1. Ambiente di sviluppo: installa Visual Studio o qualsiasi altro IDE di sviluppo .NET.
2.  Libreria GroupDocs.Parser: scarica e installa GroupDocs.Parser per .NET da[Qui](https://releases.groupdocs.com/parser/net/).
3. File di esempio: prepara un documento di esempio (ad esempio PDF, DOCX, ecc.) da cui estrarre il testo.

## Importa spazi dei nomi
Innanzitutto, dovrai importare gli spazi dei nomi necessari per accedere alle classi e ai metodi GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: creare un'istanza della classe parser
 Inizializza un'istanza di`Parser` class fornendo il percorso del file di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il codice per l'estrazione dell'area di testo andrà qui
}
```
## Passaggio 2: definire le opzioni di estrazione dell'area di testo
 Creare`PageTextAreaOptions` per specificare i criteri per l'estrazione del testo.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
In questo esempio:
- `"\\s[a-z]{2}\\s"` è un modello di espressione regolare per trovare aree di testo contenenti solo lettere minuscole.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` definisce il rettangolo (posizione e dimensione) sulla pagina da cui estrarre il testo.
## Passaggio 3: estrazione delle aree di testo
Utilizza le opzioni definite per estrarre aree di testo che soddisfano i criteri specificati.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Passaggio 4: verifica e ripetizione sulle aree di testo estratte
Controlla se l'estrazione dell'area di testo è supportata e quindi esegui l'iterazione sulle aree estratte.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Conclusione
In questo tutorial abbiamo spiegato come estrarre testo da aree specifiche all'interno di un documento utilizzando GroupDocs.Parser per .NET. Questa libreria offre ampie funzionalità per l'analisi di vari formati di documenti, rendendola uno strumento prezioso per le attività di estrazione del testo.

## Domande frequenti
### GroupDocs.Parser può estrarre testo da documenti scansionati?
Sì, GroupDocs.Parser supporta l'estrazione di testo basata su OCR per i documenti scansionati.
### GroupDocs.Parser è compatibile con più formati di documenti?
Sì, può analizzare ed estrarre testo da PDF, DOCX, XLSX, PPTX e altri formati popolari.
### GroupDocs.Parser fornisce supporto per .NET Core?
Sì, GroupDocs.Parser è compatibile con .NET Core e .NET Framework.
### Posso estrarre metadati insieme al testo utilizzando GroupDocs.Parser?
Sì, puoi estrarre sia contenuto testuale che metadati dai documenti.
### È disponibile una versione di prova per GroupDocs.Parser?
 Sì, puoi ottenere una prova gratuita da[Qui](https://releases.groupdocs.com/).