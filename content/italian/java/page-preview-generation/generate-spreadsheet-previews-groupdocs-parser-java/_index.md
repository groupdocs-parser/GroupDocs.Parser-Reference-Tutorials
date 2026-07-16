---
date: '2026-07-16'
description: Scopri come creare thumbnail di spreadsheet Java con GroupDocs.Parser,
  preview Excel senza Office e render Excel sheets as images. Questa guida copre setup,
  implementation e pratici use cases.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: Crea thumbnail di spreadsheet Java con GroupDocs.Parser—preview Excel
  senza Office e render Excel sheets as images. Segui questa step‑by‑step guide per
  generare PNG previews efficientemente.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: Crea thumbnail di spreadsheet Java con GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: Crea thumbnail di spreadsheet Java con GroupDocs.Parser
type: docs
url: /it/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Crea miniatura di foglio di calcolo Java usando GroupDocs.Parser

Se stai cercando di **creare miniatura di foglio di calcolo Java** programmi, sei nel posto giusto. In questa guida vedremo come generare anteprime PNG ad alta qualità da cartelle di lavoro `.xlsx` usando GroupDocs.Parser per Java—perfetto per miniature rapide, condividere snapshot o costruire una funzionalità di anteprima dei documenti nella tua applicazione. La soluzione funziona senza l'installazione di Microsoft Office e si adatta a cartelle di lavoro di grandi dimensioni mantenendo basso l'uso della memoria.

## Risposte rapide
- **Cosa significa “preview Excel”?** Generazione di file immagine (ad es., PNG) che rappresentano ogni pagina del foglio di lavoro.  
- **Quale formato è consigliato?** PNG offre qualità loss‑less e funziona bene per le miniature web.  
- **È necessaria una licenza?** Una prova gratuita funziona per lo sviluppo; è necessaria una licenza commerciale per la produzione.  
- **Posso cambiare la risoluzione dell'immagine?** Sì—regola il DPI in `PreviewOptions`.  
- **È possibile visualizzare in anteprima altri formati?** GroupDocs.Parser supporta anche PDF, Word e molti tipi di immagine.

## Cos'è la “preview di Excel” con GroupDocs.Parser?
Carica la tua cartella di lavoro Excel e rendi ogni foglio come immagine PNG senza necessità di Microsoft Office. GroupDocs.Parser trasmette le pagine una alla volta, producendo miniature lossless che possono essere salvate su disco o restituite via HTTP, rendendolo ideale per servizi di anteprima basati sul web.

GroupDocs.Parser legge le cartelle di lavoro Excel, rende ogni foglio come una pagina visiva e consente di trasmettere quelle pagine in file immagine. Questo elimina la necessità di interop con Office o convertitori di terze parti.

## Perché usare GroupDocs.Parser per le anteprime di Excel?
Dovresti usare GroupDocs.Parser perché funziona su qualsiasi server Java, non richiede installazione di Office, gestisce cartelle di lavoro di grandi dimensioni con poca memoria e produce immagini PNG lossless con DPI configurabili. L'SDK supporta **100+ formati di input e output**, può elaborare una cartella di lavoro di 200 pagine in meno di 3 secondi e mantiene l'uso della memoria sotto i 50 MB per foglio.

- **Nessuna installazione di Office richiesta** – funziona su qualsiasi ambiente Java lato server.  
- **Supporta file di grandi dimensioni** – trasmette le pagine una alla volta, mantenendo basso l'uso della memoria.  
- **Output di alta qualità** – controllo su DPI, formato e opzioni di rendering.  
- **Flessibilità cross‑format** – la stessa API funziona per PDF, documenti Word e altro.

## Prerequisiti
- **Java Development Kit** (8 +).  
- **IDE** come IntelliJ IDEA o Eclipse.  
- **GroupDocs.Parser for Java SDK** – scarica da [here](https://releases.groupdocs.com/parser/java/).  
- **Documentazione** – vedi la [documentation](https://docs.groupdocs.com/parser/java/).  
- **File Excel di esempio** (`.xlsx`) che desideri visualizzare in anteprima.  
- **Maven o Gradle** (opzionale) per la gestione delle dipendenze.

## Importa pacchetti
Queste importazioni ti danno accesso al parser, alle opzioni di anteprima e alle utility di gestione dei flussi.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## Guida passo‑paso per generare anteprime delle pagine del foglio di calcolo

### Passo 1: Inizializza l'istanza del Parser
`Parser` è la classe core di GroupDocs.Parser che fornisce accesso in lettura ai file di foglio di calcolo e abilita il rendering pagina per pagina.  
Crea un oggetto `Parser` che punta al tuo workbook Excel. Il blocco *try‑with‑resources* garantisce che il parser venga chiuso automaticamente.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Consiglio:** Usa un percorso assoluto o configura una cartella di risorse per evitare `FileNotFoundException`.

### Passo 2: Prepara le tue opzioni di anteprima
`PreviewOptions` configura i parametri di rendering come formato di output e DPI.  
`ICreatePageStream` è un'interfaccia di callback che fornisce uno stream di output per ogni pagina generata. Definisci come ogni pagina sarà salvata. L'implementazione di `ICreatePageStream` restituisce un nuovo `FileOutputStream` per ogni pagina del foglio di lavoro.

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> Questo passo è dove **converti xlsx in png**—lo stream scrive i dati PNG su disco.

### Passo 3: Allegare un delegato per catturare le informazioni di rendering
Se hai bisogno di dettagli su ogni foglio renderizzato (ad es., dimensioni, nome del foglio), registra una callback.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Passo 4: Specifica formato di output e DPI
Seleziona PNG come formato immagine e imposta un DPI che bilanci qualità e dimensione del file.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Regola il DPI se ti servono miniature più piccole (ad es., 96) o stampe ad alta risoluzione (ad es., 300).

### Passo 5: Genera le anteprime
Con tutto configurato, chiama `generatePreview`. L'SDK itererà su ogni foglio di lavoro e invocherà lo stream fornito.

```java
parser.generatePreview(previewOptions);
```

### Passo 6: Definisci l'helper `getOutputPath()`
`getOutputPath()` costruisce un nome file basato sul numero di pagina (foglio) e restituisce il percorso completo per l'immagine di output. Sentiti libero di personalizzare la struttura delle cartelle.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Errore comune:** Dimenticare di creare la directory `output` in anticipo causerà un `IOException`. Creala programmaticamente o assicurati che esista.

## Esempio completo funzionante (semplificato)

Di seguito una versione compatta che unisce tutti i componenti. Dimostra il flusso di lavoro **create spreadsheet thumbnail Java** dall'inizio alla fine.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

Esegui questo snippet e troverai una serie di file `preview_page_1.png`, `preview_page_2.png`, … nella cartella `output`—ognuno rappresentante un foglio del workbook Excel originale.

## Problemi comuni e soluzioni

| Problema | Causa | Soluzione |
|----------|-------|-----------|
| **Nessuna immagine generata** | `getOutputPath` restituisce una directory non valida | Assicurati che la cartella di destinazione esista o creala con `new File("output").mkdirs();` |
| **Errore out‑of‑memory su file enormi** | Caricamento dell'intero workbook in una volta | Usa l'approccio streaming (come mostrato) e processa le pagine una alla volta |
| **DPI errato** | `setDpi` non chiamato o impostato al valore predefinito (96) | Chiama `previewOptions.setDpi(yourDesiredValue);` prima di `generatePreview` |
| **Formato non supportato** | Tentativo di anteprima di un `.xlsx` corrotto | Convalida il file con Excel o usa `Parser.isSupported` prima di processare |

## Domande frequenti

**D: Posso generare anteprime per PDF e immagini usando GroupDocs.Parser?**  
R: Sì, la stessa API funziona per PDF, documenti Word e molti formati immagine.

**D: Come cambio il formato immagine di output?**  
R: Chiama `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (o `Gif`, `Bmp`, ecc.).

**D: Le prestazioni sono un problema con workbook molto grandi?**  
R: L'SDK trasmette le pagine, mantenendo basso l'uso della memoria. Per file massivi, considera l'elaborazione in batch paralleli.

**D: Come gestire gli errori durante la generazione dell'anteprima?**  
R: Avvolgi il codice in blocchi try‑catch (come mostrato) e registra i dettagli dell'eccezione. Assicurati che gli stream siano chiusi nel blocco `finally` se non usi try‑with‑resources.

**D: La libreria richiede l'installazione di Microsoft Office?**  
R: No. GroupDocs.Parser è una soluzione Java pura e funziona su qualsiasi piattaforma che supporta Java 8+.

---

**Ultimo aggiornamento:** 2026-07-16  
**Testato con:** GroupDocs.Parser 23.11 (ultima versione al momento della stesura)  
**Autore:** GroupDocs

## Tutorial correlati

- [Come generare anteprima – Tutorial di generazione di anteprima di pagina documento per GroupDocs.Parser Java](/parser/java/page-preview-generation/)
- [Analizza Excel Java con GroupDocs.Parser: Guida completa](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [Come estrarre testo grezzo da fogli Excel usando GroupDocs.Parser per Java: Guida passo‑passo](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)