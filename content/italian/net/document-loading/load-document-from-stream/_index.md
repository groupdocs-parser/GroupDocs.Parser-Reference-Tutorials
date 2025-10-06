---
title: Carica documento dal flusso
linktitle: Carica documento dal flusso
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre testo da vari formati di documenti in .NET utilizzando GroupDocs.Parser. Guida passo passo con esempi di codice.
weight: 12
url: /it/net/document-loading/load-document-from-stream/
type: docs
---
# Carica documento dal flusso

## introduzione
Nell'ambito dell'elaborazione dei documenti nelle applicazioni .NET, l'estrazione del testo da vari formati di file è un requisito comune. GroupDocs.Parser per .NET offre una potente soluzione per analizzare ed estrarre facilmente testo da una vasta gamma di documenti. Questo tutorial ti guiderà passo dopo passo attraverso il processo di utilizzo di GroupDocs.Parser per estrarre testo dai documenti.
## Prerequisiti
Prima di immergerti nell'utilizzo di GroupDocs.Parser per .NET, assicurati di avere la seguente configurazione:
- Ambiente di sviluppo: Visual Studio o qualsiasi altro ambiente di sviluppo .NET.
-  Pacchetto GroupDocs.Parser per .NET: scarica e installa la libreria GroupDocs.Parser per .NET da[Qui](https://releases.groupdocs.com/parser/net/).
- Esempi di documenti: tieni pronti i documenti di esempio per l'estrazione del testo.
## Importazione di spazi dei nomi
Inizia importando gli spazi dei nomi necessari nel tuo progetto .NET per accedere alle funzionalità GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

passaggi seguenti dimostrano come estrarre testo da un documento utilizzando GroupDocs.Parser da un flusso.
## Passaggio 1: caricare il documento dallo stream
```csharp
// Crea il flusso
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Crea un'istanza della classe Parser con lo stream
    using (Parser parser = new Parser(stream))
    {
        // Estrai il testo nel lettore
        using (TextReader reader = parser.GetText())
        {
            // Stampa il testo dal documento
            // Se l'estrazione del testo non è supportata, il lettore sarà nullo
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
In questo esempio:
- Apriamo un flusso di file per il file di documento (`YourSampleFile.docx`).
-  Inizializzare a`Parser` istanza con il flusso.
-  Utilizzo`parser.GetText()` per recuperare a`TextReader` contenente il testo estratto.
- Stampa il testo estratto o un messaggio se l'estrazione del testo non è supportata per il formato del documento.
## Conclusione
GroupDocs.Parser per .NET semplifica l'estrazione del testo da vari formati di documenti, consentendo agli sviluppatori di elaborare e utilizzare in modo efficiente il contenuto testuale all'interno delle loro applicazioni. Seguendo i passaggi descritti in questo tutorial, puoi integrare perfettamente le funzionalità di estrazione del testo dei documenti nei tuoi progetti .NET.

## Domande frequenti
### Quali formati di documenti sono supportati da GroupDocs.Parser per .NET?
GroupDocs.Parser supporta un'ampia gamma di formati di documenti tra cui DOCX, PDF, XLSX, PPTX, EPUB e altri.
### GroupDocs.Parser può estrarre immagini o metadati dai documenti?
Sì, GroupDocs.Parser può estrarre immagini, metadati e testo da vari tipi di documenti.
### GroupDocs.Parser è compatibile con le applicazioni .NET Core?
Sì, GroupDocs.Parser è compatibile con le applicazioni .NET Framework e .NET Core.
### Come posso ottenere una licenza temporanea per GroupDocs.Parser?
 È possibile ottenere una licenza temporanea da[Qui](https://purchase.groupdocs.com/temporary-license/).
### Dove posso trovare ulteriore supporto o documentazione per GroupDocs.Parser?
 Per ulteriore supporto, visitare il[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) o fare riferimento a[documentazione](https://tutorials.groupdocs.com/parser/net/).
