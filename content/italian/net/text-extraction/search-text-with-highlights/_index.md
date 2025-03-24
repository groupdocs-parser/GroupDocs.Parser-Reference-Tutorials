---
title: Cerca testo con evidenziazioni
linktitle: Cerca testo con evidenziazioni
second_title: API GroupDocs.Parser .NET
description: Scopri come cercare ed evidenziare testo nei documenti utilizzando GroupDocs.Parser per .NET. Estrai informazioni preziose in modo efficiente.
weight: 24
url: /it/net/text-extraction/search-text-with-highlights/
---
## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Parser per .NET per cercare testo all'interno di un documento ed evidenziare i risultati della ricerca. GroupDocs.Parser è una potente libreria che ti consente di lavorare con vari formati di documenti ed estrarre testo, metadati e altro.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1.  GroupDocs.Parser per .NET: scarica e installa la libreria da[Qui](https://releases.groupdocs.com/parser/net/).
2. IDE: utilizza Visual Studio o qualsiasi IDE preferito per lo sviluppo .NET.
3. File di esempio: preparare un documento di esempio (ad esempio, PDF, DOCX) per la ricerca di testo.

## Importa spazi dei nomi
Innanzitutto, inizia importando gli spazi dei nomi necessari nel tuo progetto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Passaggio 1: crea un'istanza del parser
 Inizia istanziando il file`Parser` class con il percorso del file di esempio:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Il tuo codice qui
}
```
## Passaggio 2: definire le opzioni di evidenziazione
 Specificare la`HighlightOptions` per configurare il modo in cui i risultati della ricerca dovrebbero essere evidenziati. Ad esempio, impostando una finestra di contesto di 15 caratteri:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Passaggio 3: ricerca nel testo
Ora esegui una ricerca di testo all'interno del documento. Fornisci la parola chiave che desideri cercare (ad esempio "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Passaggio 4: elaborazione dei risultati della ricerca
Scorri i risultati della ricerca e visualizza il testo trovato insieme ai punti salienti:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Conclusione
In questo tutorial hai imparato come utilizzare GroupDocs.Parser per .NET per cercare testo all'interno dei documenti ed evidenziare i risultati della ricerca. Questa funzionalità può essere estremamente utile per l'estrazione e l'analisi del testo nelle applicazioni .NET.

## Domande frequenti
### GroupDocs.Parser è adatto per l'elaborazione di vari formati di documenti?
Sì, GroupDocs.Parser supporta un'ampia gamma di formati di documenti tra cui PDF, DOCX, XLSX, PPTX e altri.
### Posso utilizzare GroupDocs.Parser per estrarre metadati dai documenti?
Assolutamente! GroupDocs.Parser ti consente di estrarre metadati, testo e dati strutturati dai documenti.
### Dove posso trovare supporto o porre domande su GroupDocs.Parser?
 Puoi visitare il[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) per qualsiasi domanda relativa al supporto.
### È disponibile una prova gratuita per GroupDocs.Parser?
 Sì, puoi accedere a[prova gratuita](https://releases.groupdocs.com/) di GroupDocs.Parser per valutarne le caratteristiche.
### Come posso acquistare una licenza per GroupDocs.Parser?
 È possibile acquistare una licenza da[Qui](https://purchase.groupdocs.com/buy) e ottenere anche licenze temporanee[Qui](https://purchase.groupdocs.com/temporary-license/).