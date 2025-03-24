---
title: Carica documento dal disco locale
linktitle: Carica documento dal disco locale
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre testo da vari formati di documenti utilizzando GroupDocs.Parser per .NET. Estrazione del testo semplice ed efficiente con C#.
weight: 11
url: /it/net/document-loading/load-document-from-local-disk/
---

# Carica documento dal disco locale

## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per estrarre testo dai documenti. GroupDocs.Parser è una potente libreria che consente agli sviluppatori di analizzare vari formati di documenti ed estrarre il contenuto di testo a livello di codice. Tratteremo i passaggi necessari per iniziare con l'estrazione del testo utilizzando questa libreria.
## Prerequisiti
Prima di iniziare, assicurati di avere installati i seguenti prerequisiti:
- Visual Studio installato nel sistema.
- Conoscenza base del linguaggio di programmazione C#.
-  Libreria GroupDocs.Parser per .NET installata (download[Qui](https://releases.groupdocs.com/parser/net/)).

## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Passaggio 1: caricare il documento dal disco locale
 Inizia caricando un documento dal tuo disco locale. Sostituire`"Your Sample File"` con il percorso del documento di destinazione.
```csharp
// Imposta il percorso del file
string filePath = "Your Sample File";
// Crea un'istanza della classe Parser con filePath
using (Parser parser = new Parser(filePath))
{
    // Estrai il testo nel lettore
    using (TextReader reader = parser.GetText())
    {
        //Stampa il testo estratto dal documento
        // Se l'estrazione del testo non è supportata, il lettore sarà nullo
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Spiegazione dei passaggi
1. Impostazione del percorso file: inizia specificando il percorso del documento da cui desideri estrarre il testo (`filePath` variabile).
2.  Creazione dell'istanza del parser: istanziare il file`Parser` classe superando il`filePath`.
3.  Estrazione del testo: utilizzare il file`GetText()` metodo del`Parser` istanza per ottenere a`TextReader` oggetto contenente il testo estratto dal documento.
4.  Lettura del testo estratto: utilizzare il file`ReadToEnd()` metodo del`TextReader` per recuperare l'intero contenuto testuale estratto dal documento.
5.  Gestione dei formati non supportati: se il formato del documento non supporta l'estrazione del testo, il file`reader` l'oggetto sarà`null`e puoi gestire questo scenario di conseguenza.

## Conclusione
In questo tutorial abbiamo illustrato i passaggi iniziali per estrarre testo da un documento utilizzando GroupDocs.Parser per .NET. Questa libreria offre funzionalità estese per l'analisi dei documenti, consentendo agli sviluppatori di lavorare in modo efficiente con vari formati di file all'interno delle loro applicazioni.

## Domande frequenti
### GroupDocs.Parser è compatibile con tutti i formati di documenti?
GroupDocs.Parser supporta un'ampia gamma di formati tra cui PDF, documenti Microsoft Office (Word, Excel, PowerPoint) e altro ancora.
### Posso estrarre metadati insieme al testo utilizzando GroupDocs.Parser?
Sì, GroupDocs.Parser consente l'estrazione sia del contenuto testuale che dei metadati dai formati di documenti supportati.
### Dove posso trovare ulteriori risorse e supporto per GroupDocs.Parser?
 Visitare il[Documentazione GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) per riferimenti API dettagliati ed esplorare il file[Forum di GroupDocs](https://forum.groupdocs.com/c/parser/17) per il sostegno della comunità.
### Come posso ottenere una licenza temporanea per GroupDocs.Parser?
 Puoi richiedere un[licenza temporanea](https://purchase.groupdocs.com/temporary-license/) a scopo di valutazione e test.
### È disponibile una prova gratuita per GroupDocs.Parser?
 Sì, puoi scaricare un file[prova gratuita](https://releases.groupdocs.com/) versione di GroupDocs.Parser.