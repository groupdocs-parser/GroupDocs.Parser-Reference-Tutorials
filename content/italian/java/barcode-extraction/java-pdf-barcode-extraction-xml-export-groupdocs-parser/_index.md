---
date: '2026-10-12'
description: Scopri come estrarre QR da PDF in Java usando GroupDocs.Parser ed esportare
  i dati del codice a barre in XML per l'elaborazione successiva.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Scopri come estrarre QR da PDF in Java usando GroupDocs.Parser ed
  esportare i dati del codice a barre in XML per l'elaborazione successiva.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Come estrarre QR da PDF in Java con GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: Come estrarre QR da PDF in Java con GroupDocs.Parser
type: docs
url: /it/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Come estrarre QR da PDF in Java con GroupDocs.Parser

Nei moderni flussi di lavoro aziendali, **estrarre QR da PDF** può trasformare un collo di bottiglia di inserimento dati manuale in una pipeline completamente automatizzata. Che tu stia gestendo manifesti di spedizione, ricevute al dettaglio o cataloghi di prodotti, estrarre rapidamente e in modo affidabile le informazioni QR è essenziale per i sistemi a valle. Questo tutorial ti guida nell'utilizzo di **GroupDocs.Parser for Java** per leggere i codici QR (e altri codici a barre) dai PDF e esportare i risultati in un file XML pulito che il tuo ERP, inventario o piattaforma di analisi può consumare.

## Risposte rapide
- **Che cosa fa GroupDocs.Parser for Java?** Legge i file PDF ed estrae dati strutturati come codici a barre, tabelle e testo.  
- **Come estrarre i codici QR?** Configura `BarcodeOptions` con il tipo QR e chiama `parser.getBarcodes()`.  
- **Posso leggere i codici QR in Java?** Sì—imposta il tipo di codice a barre su `"QR"` nelle opzioni.  
- **Ho bisogno di una licenza?** Una versione di prova funziona per i test; è necessaria una licenza commerciale per la produzione.  
- **Quale versione di Java è richiesta?** Si consiglia Java 8 o superiore.

## Che cosa significa “estrarre QR da PDF” nel contesto dell'elaborazione PDF?
Estrarre QR da PDF significa scansionare ogni pagina alla ricerca di grafiche codificate QR, decodificare i dati incorporati e restituirli in un formato adatto al programma. GroupDocs.Parser astrae l'analisi di immagine a basso livello così puoi concentrarti sulla logica di business anziché sulla manipolazione dei pixel.

## Perché usare GroupDocs.Parser per l'estrazione di QR?
GroupDocs.Parser supporta **oltre 30 formati di input** e può elaborare PDF fino a **500 MB** senza caricare l'intero file in memoria, fornendo risultati ad alta precisione anche su scansioni a bassa risoluzione. Puoi scegliere `QualityMode.Low` per la velocità o `QualityMode.High` per la massima precisione, e la stessa API funziona per PDF, immagini e documenti Office, eliminando la necessità di più librerie.

## Prerequisiti
- **GroupDocs.Parser for Java** (versione 25.5 o successiva).  
- Maven o download manuale del JAR.  
- Ambiente di sviluppo Java 8+ (IntelliJ IDEA, Eclipse o qualsiasi editor).  

## Configurazione di GroupDocs.Parser per Java
### Utilizzo di Maven
Aggiungi il repository GroupDocs e la dipendenza al tuo `pom.xml`:

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

### Download diretto
In alternativa, scarica l'ultimo JAR da [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Passaggi per l'acquisizione della licenza
- **Prova gratuita:** prova di 30 giorni con tutte le funzionalità.  
- **Licenza temporanea:** richiedi una chiave temporanea per una valutazione estesa.  
- **Acquisto:** ottieni una licenza commerciale per le distribuzioni in produzione.

### Inizializzazione e configurazione di base
Crea un'istanza `Parser` che punti al PDF che desideri analizzare:

`Parser` è la classe principale in GroupDocs.Parser che rappresenta un documento e fornisce metodi per estrarre contenuti come testo, tabelle e codici a barre.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Come leggere i codici QR nei PDF Java usando GroupDocs.Parser
Leggere i codici QR nei PDF Java con GroupDocs.Parser comporta la creazione di un'istanza parser, la configurazione delle opzioni barcode per mirare ai tipi QR, l'invocazione del metodo di estrazione barcode e la gestione degli oggetti barcode restituiti. Il processo è semplice, funziona su qualsiasi pagina PDF e restituisce i valori decodificati insieme ai metadati posizionali per ulteriori elaborazioni.

### Passo 1: verifica del supporto barcode
Prima di tentare l'estrazione, conferma che il formato del documento supporti la scansione dei barcode:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Spiegazione:* Questa verifica previene errori di runtime su tipi di file non supportati.

### Passo 2: configura le opzioni barcode (leggi QR in Java)
`BarcodeOptions` è un oggetto di configurazione che ti consente di specificare quali simbologie di barcode rilevare, impostare la modalità di qualità della scansione e regolare finemente parametri come le soglie di rilevamento, garantendo prestazioni ottimali per i QR target.

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Spiegazione:* `QualityMode.Low` velocizza l'elaborazione; passa a `High` se necessiti di maggiore precisione. L'argomento `"QR"` indica al motore di cercare solo barcode di tipo QR.

### Passo 3: estrai i dati QR
`parser.getBarcodes(options)` scansiona il documento usando le `BarcodeOptions` fornite e restituisce una collezione di oggetti `PageBarcodeArea`, ognuno dei quali incapsula il valore QR decodificato, il numero di pagina e le coordinate esatte del barcode nella pagina, consentendo una gestione precisa a valle.

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Spiegazione:* `parser.getBarcodes` restituisce una collezione iterabile di oggetti `PageBarcodeArea`, ognuno contenente il valore QR decodificato e la sua posizione nella pagina.

## Esportazione dei dati estratti in XML
### Passo 4: inizializza l'exporter XML
`XmlExporter` è una classe di utilità che trasforma una collezione di oggetti barcode in un documento XML ben strutturato, generando automaticamente elementi per ogni barcode con attributi per indice di pagina, posizione e valore decodificato, che possono poi essere salvati o trasmessi ad altri sistemi.

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Spiegazione:* `XmlExporter` gestisce la serializzazione degli oggetti barcode in XML standard, pronto per l'integrazione con sistemi ERP o di inventario.

### Passo 5: scrivi il file XML
Salva le informazioni QR estratte su disco:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Spiegazione:* Il `data.xml` risultante contiene un elemento `<Barcode>` per ogni codice QR, con attributi per numero di pagina, coordinate e valore decodificato.

## Applicazioni pratiche
1. **Gestione dell'inventario:** Popola automaticamente i database di stock leggendo i tag QR sui PDF delle spedizioni in arrivo.  
2. **Visibilità della catena di fornitura:** Traccia i pacchi in tempo reale estraendo gli identificatori QR incorporati nei documenti logistici.  
3. **Ricevute al dettaglio:** Recupera informazioni promozionali o di garanzia dai codici QR stampati sulle ricevute digitali.

## Considerazioni sulle prestazioni
- **Gestione della memoria:** Per PDF molto grandi, elabora le pagine in modalità streaming invece di caricare l'intero file in memoria.  
- **Selezione di QualityMode:** Usa `Low` per l'elaborazione di massa; passa a `High` quando lavori con scansioni a bassa risoluzione.  
- **Aggiornamenti della libreria:** Mantieni GroupDocs.Parser aggiornato per beneficiare delle ultime migliorie di prestazioni e correzioni di bug.

## Problemi comuni e risoluzione
| Sintomo | Probabile causa | Risoluzione |
|---------|----------------|-------------|
| Nessun barcode restituito | Tipo di barcode errato specificato | Modifica `"QR"` con il tipo appropriato (es., `"CODE_128"`). |
| Errore Out‑of‑memory su PDF grandi | Intero documento caricato in una volta | Elabora le pagine individualmente o aumenta la dimensione dell'heap JVM (`-Xmx2g`). |
| File XML vuoto | `exportBarcodes` chiamato prima dell'estrazione | Assicurati che `parser.getBarcodes(options)` restituisca dati prima dell'esportazione. |

## Domande frequenti
**Q: Posso estrarre barcode da file immagine usando GroupDocs.Parser?**  
A: Sì, la libreria supporta l'estrazione di barcode da formati immagine comuni (PNG, JPEG, TIFF).

**Q: Quali formati di barcode sono riconosciuti?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 e molti altri. Consulta la documentazione API per l'elenco completo.

**Q: Come devo gestire i PDF protetti da password?**  
A: Passa la password al costruttore `Parser`: `new Parser(filePath, "password")`.

**Q: La versione di prova è sufficiente per i test di produzione?**  
A: La versione di prova fornisce tutte le funzionalità ma aggiunge una filigrana ai dati estratti. Per la produzione, acquista una licenza commerciale.

**Q: Cosa succede se il mio PDF contiene sia QR che barcode lineari?**  
A: Crea più istanze `BarcodeOptions` o passa un array di tipi per scansionare tutti i formati necessari in un unico passaggio.

---

**Ultimo aggiornamento:** 2026-10-12  
**Testato con:** GroupDocs.Parser 25.5  
**Autore:** GroupDocs  

## Risorse
- [Documentazione GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Riferimento API](https://reference.groupdocs.com/parser/java)
- [Download GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Repository GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/parser)
- [Applicazione licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

## Tutorial correlati
- [Estrai Barcode PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Come caricare PDF da URL con GroupDocs.Parser per Java](/parser/java/document-loading/)
- [Estrai dati modulo PDF con GroupDocs.Parser in Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)