---
date: '2026-02-06'
description: Scopri come visualizzare in anteprima i file Excel e convertire xlsx
  in png usando GroupDocs.Parser per Java. Questo tutorial copre l'installazione,
  l'implementazione e le applicazioni pratiche.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Come visualizzare in anteprima i file Excel con GroupDocs.Parser in Java
type: docs
url: /it/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Come visualizzare i file Excel con GroupDocs.Parser in Java

Se stai cercando **come visualizzare Excel** programmaticamente, sei nel posto giusto. In questa guida vedremo come creare anteprime immagine (PNG) da cartelle di lavoro `.xlsx` usando GroupDocs.Parser per Java—perfetto per generare miniature rapide, condividere snapshot o costruire una funzionalità di anteprima documenti nella tua applicazione.

## Risposte rapide
- **Cosa significa “preview Excel”?** Generare file immagine (ad es. PNG) che rappresentano ogni pagina del foglio di lavoro.  
- **Quale formato è consigliato?** PNG offre qualità loss‑less e funziona bene per le miniature web.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per lo sviluppo; è richiesta una licenza commerciale per la produzione.  
- **Posso modificare la risoluzione dell'immagine?** Sì—regola il DPI in `PreviewOptions`.  
- **È possibile visualizzare altri formati?** GroupDocs.Parser supporta anche PDF, Word e molti tipi di immagine.

## Cos'è “come visualizzare Excel” con GroupDocs.Parser?
GroupDocs.Parser legge le cartelle di lavoro Excel, rende ogni foglio come una pagina visiva e consente di trasmettere queste pagine in file immagine. Questo elimina la necessità di interop con Office o convertitori di terze parti.

## Perché usare GroupDocs.Parser per le anteprime Excel?
- **Nessuna installazione di Office richiesta** – funziona su qualsiasi ambiente Java lato server.  
- **Supporta file di grandi dimensioni** – trasmette le pagine una alla volta, mantenendo basso l'uso della memoria.  
- **Output ad alta qualità** – controllo su DPI, formato e opzioni di rendering.  
- **Flessibilità cross‑format** – la stessa API funziona per PDF, documenti Word e altro.

## Prerequisiti
- **Java Development Kit** (8 +).  
- **IDE** come IntelliJ IDEA o Eclipse.  
- **GroupDocs.Parser for Java SDK** – scarica da [here](https://releases.groupdocs.com/parser/java/).  
- **File Excel di esempio** (`.xlsx`) che desideri visualizzare.  
- **Maven o Gradle** (opzionale) per la gestione delle dipendenze.

## Importa Pacchetti
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

## Guida passo‑passo per generare anteprime delle pagine del foglio di calcolo

### Passo 1: Inizializza l'istanza del Parser
Crea un oggetto `Parser` che punta al tuo workbook Excel. Il blocco *try‑with‑resources* garantisce che il parser venga chiuso automaticamente.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Consiglio:** Usa un percorso assoluto o configura una cartella di risorse per evitare `FileNotFoundException`.

### Passo 2: Prepara le tue opzioni di anteprima
Definisci come verrà salvata ogni pagina. L'implementazione `ICreatePageStream` restituisce un nuovo `FileOutputStream` per ogni pagina del foglio di lavoro.

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

> Questo passo è dove **converti xlsx in png**—il flusso scrive i dati PNG su disco.

### Passo 3: Allega un delegato per catturare le informazioni di rendering
Se hai bisogno di dettagli su ogni foglio renderizzato (ad es. dimensioni, nome del foglio), registra un callback.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Passo 4: Specifica il formato di output e il DPI
Seleziona PNG come formato immagine e imposta un DPI che bilanci qualità e dimensione del file.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Regola il DPI se ti servono miniature più piccole (ad es. 96) o stampe ad alta risoluzione (ad es. 300).

### Passo 5: Genera le anteprime
Con tutto configurato, chiama `generatePreview`. L'SDK itererà su ogni foglio di lavoro e invocherà lo stream fornito.

```java
parser.generatePreview(previewOptions);
```

### Passo 6: Definisci l'helper `getOutputPath()`
Questo metodo costruisce un nome file basato sul numero di pagina (foglio). Sentiti libero di personalizzare la struttura delle cartelle.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Errore comune:** Dimenticare di creare la directory `output` in anticipo provocherà un `IOException`. Creala programmaticamente o assicurati che esista.

## Esempio completo funzionante (semplificato)

Di seguito una versione compatta che unisce tutti i componenti. Dimostra il flusso di lavoro **create excel page preview** dall'inizio alla fine.

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
| **Errore out‑of‑memory su file enormi** | Caricamento dell'intero workbook in una volta | Usa l'approccio di streaming (come mostrato) e processa le pagine una alla volta |
| **DPI errato** | `setDpi` non chiamato o impostato al valore predefinito (96) | Chiama `previewOptions.setDpi(yourDesiredValue);` prima di `generatePreview` |
| **Formato non supportato** | Tentativo di visualizzare un `.xlsx` corrotto | Convalida il file con Excel o usa `Parser.isSupported` prima di processare |

## Domande frequenti

**Q: Posso generare anteprime per PDF e immagini usando GroupDocs.Parser?**  
A: Sì, la stessa API funziona per PDF, documenti Word e molti formati immagine.

**Q: Come cambio il formato immagine di output?**  
A: Chiama `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (o `Gif`, `Bmp`, ecc.).

**Q: Le prestazioni sono un problema con workbook molto grandi?**  
A: L'SDK trasmette le pagine, mantenendo basso l'uso della memoria. Per file massivi, considera l'elaborazione in batch paralleli.

**Q: Come gestire gli errori durante la generazione delle anteprime?**  
A: Avvolgi il codice in blocchi try‑catch (come mostrato) e registra i dettagli dell'eccezione. Assicurati che gli stream siano chiusi nel blocco `finally` se non usi try‑with‑resources.

**Q: La libreria richiede l'installazione di Microsoft Office?**  
A: No. GroupDocs.Parser è una soluzione Java pura e funziona su qualsiasi piattaforma che supporta Java 8+.

## Conclusione
Ora disponi di un metodo completo e pronto per la produzione per **come visualizzare Excel** i workbook e **convertire xlsx in png** usando GroupDocs.Parser. Regola DPI, cartella di output o formato immagine per soddisfare le esigenze del tuo progetto e integra questo snippet in flussi di lavoro di gestione documenti più ampi.

Pronto per il passo successivo? Esplora la [documentazione](https://docs.groupdocs.com/parser/java/) ufficiale per opzioni di rendering avanzate, file protetti da password e tecniche di elaborazione batch.

---

**Ultimo aggiornamento:** 2026-02-06  
**Testato con:** GroupDocs.Parser 23.11 (ultima versione al momento della scrittura)  
**Autore:** GroupDocs