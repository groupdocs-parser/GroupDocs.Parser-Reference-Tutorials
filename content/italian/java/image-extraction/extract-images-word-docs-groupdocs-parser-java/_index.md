---
date: '2026-01-19'
description: Scopri come estrarre le immagini dai documenti Word utilizzando GroupDocs.Parser
  per Java e salvare le immagini Word in formato PNG in modo efficiente.
keywords:
- extract images from Word documents
- GroupDocs.Parser for Java
- automate image extraction
title: Estrai immagini da Word usando GroupDocs.Parser per Java
type: docs
url: /it/java/image-extraction/extract-images-word-docs-groupdocs-parser-java/
weight: 1
---

# Estrai immagini da Word usando GroupDocs.Parser per Java

Estrarre immagini dai file Word manualmente richiede tempo e può generare errori. In questo tutorial scoprirai **come estrarre immagini da Word** documenti automaticamente con GroupDocs.Parser per Java, e poi **salvare immagini Word in PNG** per l'el potrai integrare l' Java.

## Risposte rapide
- **Cosa fa la libreria?** Analizza Word, PDF e molti altri formati per esporre testo, tabelle e immagini.  
- **Quante righe di codice?** Circa 30 righe di Java, più qualche riga di configurazione.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per lo sviluppo; è richiesta una licenza completa per la produzione.  
- **Posso estrarre immagini incorporate?** Sì – il metodo `getImages()` restituisce tutte le immagini incorporate.  
- **Formato di output supportato?** PNG è il formato predefinito, ma sono disponibili altri formati tramite `ImageFormat`.

## Cos'è “estrarre immagini da Word”?
GroupDocs.Parser legge la struttura binaria di un file DOCX o DOC e rende ogni immagine disponibile come oggetto `PageImageArea`. Questo ti consente di estrarre programmaticamente ogni immagine senza aprire il documento in Microsoft Word.

## Perché usare GroupDocs.Parser per Java?
- **Velisi in puro Java evita l'overhead di COM o dell'automazione di Office.  
- **Affidabilità:** Funziona su qualsiasi piattaforma (Windows, Linux, macOS) e gestisce i file corrotti in modo elegante.  
- **Flessibilità:** Supporta un'ampia gamma di formati, così puoi riutilizzare lo stesso codice per PDF, PPTX, ecc.

## Prerequisiti
- **GroupDocs.Parser per Java** (versione 25.5 o successiva)  
- **JDK 8+**  
- Un IDE come IntelliJ IDEA, Eclipse o NetBeans  

## Configurazione di GroupDocs.Parser per Java

Aggiungi la libreria al tuo progetto Maven:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/parser/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-parser</artifactId>
      <version>25.5</version>
   </dependency>
</dependencies>
```

In alternativa, scarica l'ultima versione direttamente da [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Passaggi per l'ottenimento della licenza
- **Prova gratuita:** Inizia con una prova gratuita per esplorare le funzionalità.  
- Ottieni una licenza temporanea per testi e le salva come file PNG.

### Passo 1: Inizializzare il Parser

```java
// Initialize the Parser with the document path.
try (Parser parser = new Parser(documentPath)) {
    // Proceed with image extraction...
}
```

### Passo 2: Estrarre le immagini

```java
// Extract images from the document.
Iterable<PageImageArea> images = parser.getImages();
```

### Passo 3: Configurare le opzioni immagine

```java
// Set options to save images in PNG format.
ImageOptions options = new ImageOptions(ImageFormat.Png);
```

### Passo 4: Salvare ogni immagine

```java
int imageNumber = 0;
for (PageImageArea image : images) {
    String outputPath = YOUR_OUTPUT_DIRECTORY + "/" + imageNumber + ".png";
    image.save(outputPath, options);
    imageNumber++;
}
```

### Passo 5: Definire i metodi di supporto per i percorsi

```java
public static String getDocumentDirectory() {
    return YOUR_DOCUMENT_DIRECTORY;
}

public static String getOutputDirectory() {
    return YOUR_OUTPUT_DIRECTORY;
}
```

Sostituisci `YOUR_DOCUMENT_DIRECTORY` e `YOUR_OUTPUT_DIRECTORY` con i percorsi effettivi del file system che intendi utilizzare.

## Come estrarre immagini incorporate da DOCX?
La chiamata `getImages()` restituisce automaticamente **immagini incorporate** da un file DOCX, sia che siano inline, flottanti o parte di una forma. Non sono necessarie chiamate API aggiuntive.

## Come estrarre immagini da DOCX e salvarle come PNG?
L'oggetto `ImageOptions` mostrato nel **Passo 3** viene soddisfacendo il requisito **salvare immagini Word in PNG**.

##olla manuale.  
3. **Archiviazione dei documenti:** Conservare le immagini separatamente per ridurre le dimensioni dell'archivio e migliorare la ricercabilità.  
4. **Pubblicazione automatizzata:** Inviare i PNG estratti direttamente ai generatori di pagine web o ai modelli di email.

## Considerazioni sulle prestazioni
- **Memoria:** Assegna un heap sufficiente (`-Xmx2g` o superiore) quando elabori documenti di grandi dimensioni.  
- **Elaborazione batch:** Scorri una cartella di file e riutilizza una singola istanza `Parser` per documento per mantenere basso l'uso della memoria.  
- **Handle dei file:** Il blocco try‑with‑resources garantisce che il parser venga chiuso tempestivamente, evitando perdite.

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| **OutOfMemoryError** su file DOCX di grandi dimensioni | Aumentare l'heap JVM o elaborare il documento in batch più piccoli. |
| **No images returned** | Verificare che il documento contenga effettivamente immagini incorporate; alcune “immagini” sono disegni VML non esposti come immagini. |
| **Incorrect image orientation** | Alcune immagini DOCX memorizzano la rotazione EXIF; eseguire un post‑processo con una libreria di immagini se necessario. |

## Domande frequenti

**D: Quali formati di file supporta GroupDocs.Parser per l'estrazione di immagini?**  
R: Gestisce DOC, DOCX, PDF, PPT, PPTX e molti altri formati, esponendo le immagini tramite lo stesso metodo `getImages()`.

**D: Posso estrarre immagini da file Word protetti da password?**  
R: Sì—passa la password al costruttore `Parser` e la libreria decritterà il documento prima dell'estrazione.

**D: Esiste un modo per estrarre solo tipi specifici di immagini (ad esempio solo JPEG)?**  
R: Dopo aver recuperato gli oggetti `PageImageArea`, ispeziona `image.getFormat()` e filtra di conseguenza prima di salvare.

**D: La libreria supporta l'elaborazione asincrona?**  
R: Sebbene l'API principale sia sincrona, puoi racchiudere la logica di estrazione in un thread separato o utilizzare `CompletableFuture` di Java per l'elaborazione È necessaria una licenza commerciale per l'uso in produzione?**  
R: Una prova gratuita è sufficiente per la valutazione, ma è richiesta una licenza a pagamento per le distribuzioni commerciali.

## Conclusione
Ora disponi di una soluzione completa, pronta per la produzione, per **come estrarre immagini da Word** documenti usando GroupDocs.Parser per Java e **salvare immagini Word in PNG**. Integra questo codice nei tuoi flussi di lavoro esistenti, automatizza l'estrazione batch e sblocca le risorse visive nascoste nei tuoi file Word.

---

**Ultimo aggiornamento:** 2026-01-19  
**Testato con:** GroupDocs.Parser 25.5  
**Autore:** GroupDocs  

**Risorse**
- **Documentazione:** [GroupDocs Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- **Riferimento API:** [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)
- **Download:** [Latest Release](https://releases.groupdocs.com/parser/java/)
- **GitHub:** [Source Code on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- **Supporto gratuito:** [GroupDocs Forum](https://forum.groupdocs.com/c/parser)
- **Licenza temporanea:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)