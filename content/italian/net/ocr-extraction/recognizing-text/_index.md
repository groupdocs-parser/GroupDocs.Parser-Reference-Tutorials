---
title: Riconoscimento del testo
linktitle: Riconoscimento del testo
second_title: API GroupDocs.Parser .NET
description: Estrai testo da vari formati di documenti in modo efficiente con GroupDocs.Parser per .NET. Integrazione semplice e potenti funzionalità OCR.
type: docs
weight: 12
url: /it/net/ocr-extraction/recognizing-text/
---
## introduzione
Nell'ambito dello sviluppo .NET, l'estrazione efficiente del testo da vari formati di documenti è fondamentale. GroupDocs.Parser per .NET fornisce una soluzione solida per estrarre il testo senza problemi. In questo tutorial, approfondiremo passo dopo passo l'utilizzo di GroupDocs.Parser per riconoscere ed estrarre testo dai documenti.
## Prerequisiti
Prima di approfondire l'utilizzo di GroupDocs.Parser, assicurati di disporre dei seguenti prerequisiti:
- Conoscenza di base della programmazione C#
- Visual Studio installato sul tuo computer
- Accesso a Internet per download di pacchetti e riferimenti alla documentazione

## Importa spazi dei nomi
Inizia importando gli spazi dei nomi necessari per sfruttare le funzionalità GroupDocs.Parser:
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
## Passaggio 1: installare GroupDocs.Parser
 Innanzitutto, scarica e installa la libreria GroupDocs.Parser. Puoi acquisirlo da[Link per scaricare](https://releases.groupdocs.com/parser/net/).
## Passaggio 2: ottieni una licenza temporanea
 Per utilizzare GroupDocs.Parser, ottenere una licenza temporanea da[Qui](https://purchase.groupdocs.com/temporary-license/).
## Passaggio 3: inizializzazione di ParserSettings
 Crea un'istanza di`ParserSettings`classe per configurare le impostazioni di estrazione del testo, inclusi i connettori OCR, se necessario.
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Passaggio 4: utilizzo del parser per estrarre il testo
 Ora crea un'istanza di`Parser` classe con le impostazioni configurate.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx", settings))
{
    // Configura TextOptions per l'utilizzo dell'OCR
    TextOptions options = new TextOptions(false, true);
    // Estrai il testo utilizzando l'OCR
    using (TextReader reader = parser.GetText(options))
    {
        // Visualizza il testo estratto o un messaggio "non supportato".
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
In questo frammento:
-  Sostituire`"YourSampleFile.docx"` con il percorso del documento di destinazione.
- `TextOptions` è configurato per abilitare l'OCR e ottimizzare l'estrazione del testo.

## Conclusione
 Congratulazioni! Hai imparato come integrare GroupDocs.Parser per .NET nei tuoi progetti per estrarre il testo in modo efficiente. Esplora l'ampio[documentazione](https://reference.groupdocs.com/parser/net/) per funzionalità avanzate e ottimizzazioni.

## Domande frequenti
### GroupDocs.Parser è adatto per estrarre testo da file PDF?
Sì, GroupDocs.Parser supporta l'estrazione di testo da vari formati, incluso PDF.
### Posso integrare GroupDocs.Parser nella mia applicazione ASP.NET?
Assolutamente sì, GroupDocs.Parser può essere perfettamente integrato nelle applicazioni ASP.NET.
### GroupDocs.Parser richiede una licenza per uso commerciale?
Sì, per l'uso commerciale è necessaria una licenza. Ottieni una licenza temporanea[Qui](https://purchase.groupdocs.com/temporary-license/).
### Quali formati di documenti sono supportati da GroupDocs.Parser?
GroupDocs.Parser supporta un'ampia gamma di formati, inclusi DOCX, PDF, XLSX e altri.
### Come posso chiedere supporto o porre domande relative a GroupDocs.Parser?
 Visitare il[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)per supporto e discussioni.