---
title: Estrai testo dalla pagina in modalità Raw
linktitle: Estrai testo dalla pagina in modalità Raw
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre efficacemente il testo dalle pagine dei documenti utilizzando Groupdocs.Parser per .NET in questo tutorial completo.
type: docs
weight: 17
url: /it/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## introduzione
In questo tutorial imparerai come utilizzare Groupdocs.Parser per .NET per estrarre testo dalle pagine del documento in modalità raw. Questa libreria fornisce strumenti efficienti per analizzare ed estrarre contenuto da vari formati di file, consentendo agli sviluppatori di incorporare l'estrazione del testo dei documenti nelle loro applicazioni .NET.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
- Conoscenza base di programmazione C# e .NET
- Visual Studio installato sul tuo computer
- Accesso alla libreria Groupdocs.Parser per .NET
- File di documento di esempio per il test

## Importa spazi dei nomi
Inizia includendo gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: inizializzare il parser
 Innanzitutto, crea un'istanza di`Parser` class fornendo il percorso del file del documento di esempio.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il tuo codice qui
}
```
## Passaggio 2: recuperare le informazioni sul documento
 Recuperare informazioni sul documento utilizzando`GetDocumentInfo()` metodo.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Passaggio 3: scorrere le pagine ed estrarre il testo
Scorri ogni pagina del documento ed estrai il contenuto del testo.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Estrai il testo dalla pagina
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusione
Ora hai imparato come utilizzare Groupdocs.Parser per .NET per estrarre testo dalle pagine del documento in modalità raw. Questa può essere una funzionalità potente per le applicazioni che necessitano di analizzare o elaborare contenuti di testo da vari formati di file.

## Domande frequenti
### Groupdocs.Parser per .NET è compatibile con tutti i formati di file?
Groupdocs.Parser supporta un'ampia gamma di formati di file tra cui PDF, DOCX, XLSX, PPTX, EPUB e altri.
### Posso estrarre metadati insieme al testo utilizzando questa libreria?
Sì, Groupdocs.Parser ti consente di estrarre sia testo che metadati dai documenti.
### È disponibile una versione di prova per i test?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto tecnico per Groupdocs.Parser?
 Per assistenza tecnica, visitare il[Forum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Dove posso acquistare una licenza per Groupdocs.Parser per .NET?
 È possibile acquistare una licenza[Qui](https://purchase.groupdocs.com/buy).