---
title: Estrai testo formattato dal documento
linktitle: Estrai testo formattato dal documento
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre testo formattato dai documenti utilizzando GroupDocs.Parser per .NET. Estrazione del testo semplice ed efficiente per le tue applicazioni.
weight: 10
url: /it/net/formatted-text-extraction/extract-formatted-text-from-document/
type: docs
---
# Estrai testo formattato dal documento

## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per estrarre testo formattato da vari tipi di documenti. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di lavorare con i documenti in modo semplificato ed efficiente. Al termine di questa guida sarai in grado di integrare perfettamente le funzionalità di estrazione del testo nelle tue applicazioni .NET.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Visual Studio: assicurati di avere Visual Studio installato sul tuo sistema.
-  GroupDocs.Parser per .NET: scarica e installa la libreria GroupDocs.Parser da[Qui](https://releases.groupdocs.com/parser/net/).
- Esempi di documenti: prepara documenti di esempio (ad esempio PDF, DOCX) per l'estrazione del testo.
## Importa spazi dei nomi
Innanzitutto, includi gli spazi dei nomi necessari nel codice C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Passaggio 1: creare un'istanza della classe parser
 Inizia inizializzando a`Parser` oggetto con il percorso del documento di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il codice di estrazione del testo va qui
}
```
 Sostituire`"YourSampleFile.pdf"` con il percorso del file del documento.

## Passaggio 2: estrai il testo formattato
 All'interno del`using` bloccare, utilizzare il`GetFormattedText` metodo per estrarre il testo formattato dal documento. Specificare il formato di output desiderato (ad esempio, HTML) utilizzando`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Estrai il testo formattato nel lettore
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Controlla se l'estrazione è supportata
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Leggere e visualizzare il testo estratto
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Conclusione
Congratulazioni! Hai imparato come estrarre testo formattato dai documenti utilizzando GroupDocs.Parser per .NET. Questa libreria versatile apre possibilità per l'elaborazione e l'analisi del testo all'interno delle tue applicazioni.

## Domande frequenti
### D: GroupDocs.Parser può estrarre testo da documenti protetti da password?
R: Sì, GroupDocs.Parser supporta l'estrazione di testo da documenti protetti da password.
### D: Quali formati di documento sono supportati da GroupDocs.Parser?
R: GroupDocs.Parser supporta un'ampia gamma di formati tra cui PDF, DOCX, XLSX, PPTX e altri.
### D: Come posso ottenere una licenza temporanea per GroupDocs.Parser?
 R: Puoi ottenere una licenza temporanea da[Qui](https://purchase.groupdocs.com/temporary-license/).
### D: GroupDocs.Parser fornisce supporto per l'estrazione di immagini dai documenti?
R: Sì, GroupDocs.Parser supporta l'estrazione di immagini insieme all'estrazione di testo.
### D: Dove posso trovare ulteriore supporto o porre domande su GroupDocs.Parser?
 R: Visita il[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)per supporto e discussioni.