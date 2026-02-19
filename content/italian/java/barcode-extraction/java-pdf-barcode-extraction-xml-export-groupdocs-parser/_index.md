---
date: '2026-02-19'
description: Scopri come leggere i codici QR nei PDF Java usando GroupDocs.Parser
  e esportare i dati del codice a barre in XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Come leggere i codici QR nei PDF Java con GroupDocs.Parser
type: docs
url: /it/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Come leggere i codici QR nei PDF Java con GroupDocs.Parser

In moderni flussi di lavoro aziendali, **come leggere QR** codici dai documenti PDF può fare la differenza tra un collo di bottiglia di inserimento dati manuale e una pipeline completamente automatizzata. Che tu stia gestendo manifesti di spedizione, ricevute al dettaglio o cataloghi di prodotto, estrarre le informazioni QR in modo rapido e affidabile è essenziale. Questo tutorial ti guida nell'uso di **GroupDocs.Parser for Java** per leggere i codici QR (e altri barcode) dai PDF e esportare i risultati in un file XML pulito che i sistemi a valle possono consumare.

## Risposte rapide
- **Cosa fa GroupDocs.Parser for Java?** Legge file PDF ed estrae dati strutturati come i barcode.  
- **Come estrarre i codici QR?** Configurando `BarcodeOptions` con il tipo QR e chiamando `parser.getBarcodes()`.  
- **Posso leggere i codici QR in Java?** Sì—imposta il tipo di barcode su `"QR"` nelle opzioni.  
- **È necessaria una licenza?** Una versione di prova funziona per i test; è richiesta una licenza commerciale per la produzione.  
- **Quale versione di Java è richiesta?** Si consiglia Java 8 o superiore.

## Cos’è “come leggere QR” nel contesto dell’elaborazione PDF?
Leggere i codici QR dai PDF significa scansionare ogni pagina alla ricerca di grafiche codificate QR, decodificare i dati incorporati e restituirli in un formato adatto al programma. GroupDocs.Parser astrae l'analisi a basso livello dell'immagine così puoi concentrarti sulla logica di business anziché sulla manipolazione dei pixel.

## Perché usare GroupDocs.Parser per l’estrazione di QR?
- **Alta precisione:** Gli algoritmi di elaborazione immagine integrati gestiscono scansioni a bassa risoluzione.  
- **Opzioni di performance:** Scegli `QualityMode.Low` per la velocità o `QualityMode.High` per la massima precisione.  
- **Supporto cross‑formato:** Funziona con PDF, immagini e persino documenti Office, così puoi riutilizzare lo stesso codice per diversi tipi di file.

## Prerequisiti
- **GroupDocs.Parser for Java** (versione 25.5 o successiva).  
- Maven o download manuale del JAR.  
- Ambiente di sviluppo Java 8+ (IntelliJ IDEA, Eclipse o qualsiasi editor).  

## Configurare GroupDocs.Parser for Java
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

### Download diretto
In alternativa, scarica l'ultimo JAR da [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Passaggi per l’acquisizione della licenza
- **Prova gratuita:** prova di 30 giorni con set completo di funzionalità.  
- **Licenza temporanea:** richiedi una chiave temporanea per una valutazione estesa.  
- **Acquisto:** ottieni una licenza commerciale per le distribuzioni in produzione.

### Inizializzazione e configurazione di base
Crea un'istanza `Parser` che punti al PDF da analizzare:

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
### Passo 1: Verifica del supporto ai barcode
Prima di tentare l'estrazione, conferma che il formato del documento supporti la scansione dei barcode:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Spiegazione:* questa guardia previene errori di runtime su tipi di file non supportati.

### Passo 2: Configura le opzioni del barcode (Read QR codes Java)
Imposta la qualità della scansione e specifica che ti interessano i codici QR:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Spiegazione:* `QualityMode.Low` velocizza l'elaborazione; passa a `High` se ti serve maggiore accuratezza. L'argomento `"QR"` indica al motore di cercare solo barcode di tipo QR.

### Passo 3: Estrai i dati QR
Recupera le informazioni del barcode da ogni pagina del PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Spiegazione:* `parser.getBarcodes` restituisce una collezione iterabile di oggetti `PageBarcodeArea`, ognuno contenente il valore QR decodificato e la sua posizione nella pagina.

## Esportare i dati estratti in XML
### Passo 4: Inizializzare l’exporter XML
Crea un exporter che trasformerà la collezione di barcode in un file XML ben strutturato:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Spiegazione:* `XmlExporter` gestisce la serializzazione degli oggetti barcode in XML standard, pronto per l’integrazione con sistemi ERP o di inventario.

### Passo 5: Scrivi il file XML
Salva le informazioni QR estratte su disco:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Spiegazione:* il file `data.xml` risultante contiene un elemento `<Barcode>` per ogni codice QR, con attributi per numero di pagina, coordinate e valore decodificato.

## Applicazioni pratiche
1. **Gestione inventario:** Popola automaticamente i database di stock leggendo i tag QR sui PDF di spedizione in entrata.  
2. **Visibilità della supply‑chain:** Traccia i pacchi in tempo reale estraendo gli identificatori QR incorporati nei documenti logistici.  
3. **Ricevute al dettaglio:** Recupera informazioni promozionali o di garanzia dai codici QR stampati sulle ricevute digitali.

## Considerazioni sulle performance
- **Gestione della memoria:** Per PDF molto grandi, elabora le pagine in streaming anziché caricare l’intero file in memoria.  
- **Selezione di QualityMode:** Usa `Low` per elaborazioni di massa; passa a `High` quando lavori con scansioni a bassa risoluzione.  
- **Aggiornamenti della libreria:** Mantieni GroupDocs.Parser aggiornato per beneficiare delle ultime migliorie di performance e correzioni di bug.

## Problemi comuni e risoluzione
| Sintomo | Causa probabile | Soluzione |
|---------|-----------------|-----------|
| Nessun barcode restituito | Tipo di barcode errato specificato | Cambia `"QR"` con il tipo appropriato (es. `"CODE_128"`). |
| Errore out‑of‑memory su PDF grandi | Documento caricato interamente | Elabora le pagine singolarmente o aumenta la dimensione dell'heap JVM (`-Xmx2g`). |
| File XML vuoto | `exportBarcodes` chiamato prima dell'estrazione | Assicurati che `parser.getBarcodes(options)` restituisca dati prima di esportare. |

## Domande frequenti
**D: Posso estrarre barcode da file immagine usando GroupDocs.Parser?**  
R: Sì, la libreria supporta l'estrazione di barcode da formati immagine comuni (PNG, JPEG, TIFF).

**D: Quali formati di barcode sono riconosciuti?**  
R: QR, Code 39, Code 128, DataMatrix, PDF417 e molti altri. Consulta la documentazione API per l'elenco completo.

**D: Come gestire PDF protetti da password?**  
R: Passa la password al costruttore `Parser`: `new Parser(filePath, "password")`.

**D: La versione di prova è sufficiente per i test di produzione?**  
R: La versione di prova fornisce tutte le funzionalità ma aggiunge un watermark ai dati estratti. Per la produzione, acquista una licenza commerciale.

**D: Cosa succede se il mio PDF contiene sia QR sia barcode lineari?**  
R: Crea più istanze `BarcodeOptions` oppure passa un array di tipi per scansionare tutti i formati necessari in un unico passaggio.

---

**Ultimo aggiornamento:** 2026-02-19  
**Testato con:** GroupDocs.Parser 25.5  
**Autore:** GroupDocs  

## Risorse
- [GroupDocs.Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- [API Reference](https://reference.groupdocs.com/parser/java)
- [Download GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub Repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/parser)
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)