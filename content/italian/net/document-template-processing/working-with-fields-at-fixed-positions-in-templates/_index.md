---
title: Lavorare con i campi in posizioni fisse nei modelli
linktitle: Lavorare con i campi in posizioni fisse nei modelli
second_title: API GroupDocs.Parser .NET
description: Scopri come estrarre dati dai documenti utilizzando GroupDocs.Parser per .NET. Tutorial completo con esempi di codice.
weight: 11
url: /it/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---

# Lavorare con i campi in posizioni fisse nei modelli

## introduzione
In questo tutorial esploreremo come lavorare con i campi in posizioni fisse all'interno dei modelli utilizzando GroupDocs.Parser per .NET. GroupDocs.Parser è una potente libreria di analisi dei documenti che consente agli sviluppatori di estrarre dati da vari formati di documenti come PDF, Word, Excel e altri. Nello specifico, ci concentreremo sulla definizione e sull'utilizzo dei campi del modello per estrarre informazioni mirate in base alle loro posizioni fisse.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Conoscenza di base dello sviluppo C# e .NET.
- Visual Studio installato nel sistema.
- GroupDocs.Parser per la libreria .NET installata. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/parser/net/).
- File di documenti di esempio per i test.

## Importa spazi dei nomi
Inizia includendo gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Passaggio 1: definire un campo modello
Innanzitutto, definisci un campo con una posizione fissa all'interno di un modello. Questo campo rappresenta l'area da cui verranno estratti i dati.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Qui:
- `Rectangle` specifica la posizione e la dimensione del campo.
- `Point(35, 135)` rappresenta le coordinate dell'angolo in alto a sinistra.
- `Size(100, 10)` definisce la larghezza e l'altezza del campo.
- `"FromCompany"` è il nome assegnato a questo campo.
## Passaggio 2: crea un modello
Costruisci un modello utilizzando il campo definito.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 IL`Template` l'oggetto contiene i campi definiti.
## Passaggio 3: analizzare il documento utilizzando il modello
 Istanziare il`Parser` class con il percorso del documento di destinazione e quindi analizzare il documento utilizzando il modello creato.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Scorrere i dati estratti
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Qui:
- `Parser` viene inizializzato con il percorso del file del documento di esempio.
- `ParseByTemplate` Il metodo viene utilizzato per estrarre i dati in base al modello fornito.
-  È possibile accedere ai dati estratti utilizzando`DocumentData`dove ogni elemento corrisponde a un campo definito.

## Conclusione
In questo tutorial abbiamo illustrato il processo di utilizzo dei campi in posizioni fisse nei modelli utilizzando GroupDocs.Parser per .NET. Definendo modelli con posizioni di campo specifiche, gli sviluppatori possono estrarre con precisione dati mirati da vari formati di documenti.

## Domande frequenti
### GroupDocs.Parser è compatibile con tutti i formati di documenti?
 GroupDocs.Parser supporta un'ampia gamma di formati di file, inclusi PDF, Microsoft Word, Excel, PowerPoint e altri. Fare riferimento al[documentazione](https://tutorials.groupdocs.com/parser/net/) per un elenco dettagliato.
### Come posso ottenere una licenza temporanea per GroupDocs.Parser?
 È possibile ottenere una licenza temporanea a scopo di test da[Qui](https://purchase.groupdocs.com/temporary-license/).
### Dove posso trovare supporto per GroupDocs.Parser?
 Per assistenza tecnica e discussioni, visitare il[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Posso provare GroupDocs.Parser prima dell'acquisto?
 Sì, puoi esplorare la libreria con una prova gratuita disponibile[Qui](https://releases.groupdocs.com/).
### Come posso acquistare una licenza per GroupDocs.Parser?
 Per acquistare una licenza, visitare il[pagina di acquisto](https://purchase.groupdocs.com/buy).