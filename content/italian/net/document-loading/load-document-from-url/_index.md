---
title: Carica documento dall'URL
linktitle: Carica documento dall'URL
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre testo dai documenti utilizzando GroupDocs.Parser per .NET. Questo tutorial illustra il caricamento di un documento da un URL e l'estrazione del testo passo dopo passo.
weight: 13
url: /it/net/document-loading/load-document-from-url/
---

# Carica documento dall'URL

## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per estrarre testo dai documenti. GroupDocs.Parser è un potente strumento per estrarre testo, metadati e altre informazioni da vari formati di documenti, come PDF, Word, Excel e altri. Tratteremo passo dopo passo il processo di caricamento di un documento da un URL e di estrazione del suo contenuto testuale.
## Prerequisiti
Prima di iniziare, assicurati di aver configurato i seguenti prerequisiti:
1. Visual Studio: installa Visual Studio sul tuo sistema.
2.  GroupDocs.Parser per .NET: scaricare e installare GroupDocs.Parser per .NET dal[pagina di download](https://releases.groupdocs.com/parser/net/).
3. Comprensione di base di C#: familiarità con il linguaggio di programmazione C#.

## Importa spazi dei nomi
Inizia includendo gli spazi dei nomi necessari nel codice C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Innanzitutto, dimostreremo come caricare un documento da un URL ed estrarne il contenuto testuale.
## Passaggio 1: specificare l'URL del documento
Specifica l'URL del documento da cui desideri estrarre il testo:
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## Passaggio 2: crea un'istanza del parser
 Istanziare il`Parser` classe con l'URL del documento:
```csharp
using (Parser parser = new Parser(uri))
{
    // Il tuo codice va qui
}
```
## Passaggio 3: estrai il testo dal documento
 Dentro il`using`bloccare, utilizzare`parser.GetText()` per estrarre il testo dal documento:
```csharp
using (TextReader reader = parser.GetText())
{
    // Il tuo codice va qui
}
```
## Passaggio 4: Visualizza il testo estratto
Leggere e stampare il testo estratto dal documento:
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## Conclusione
In questo tutorial abbiamo trattato le nozioni di base sull'estrazione del testo da un documento utilizzando GroupDocs.Parser per .NET. Seguendo questi passaggi, puoi integrare facilmente le funzionalità di estrazione del testo dei documenti nelle tue applicazioni C#.

## Domande frequenti
### GroupDocs.Parser è compatibile con vari formati di documenti?
Sì, GroupDocs.Parser supporta un'ampia gamma di formati di documenti, inclusi PDF, Word, Excel, PowerPoint e altri.
### Posso estrarre metadati insieme al testo utilizzando GroupDocs.Parser?
Sì, GroupDocs.Parser ti consente di estrarre metadati, testo e altre informazioni dai documenti.
### È disponibile una versione di prova per GroupDocs.Parser?
 Sì, puoi ottenere una versione di prova gratuita di GroupDocs.Parser da[Qui](https://releases.groupdocs.com/).
### Dove posso trovare la documentazione per GroupDocs.Parser?
 È disponibile la documentazione dettagliata per GroupDocs.Parser[Qui](https://tutorials.groupdocs.com/parser/net/).
### Come posso ottenere supporto tecnico per GroupDocs.Parser?
È possibile cercare supporto tecnico e porre domande sul forum GroupDocs.Parser[Qui](https://forum.groupdocs.com/c/parser/17).