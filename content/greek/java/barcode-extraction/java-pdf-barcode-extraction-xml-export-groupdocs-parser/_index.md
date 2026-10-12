---
date: '2026-10-12'
description: Μάθετε πώς να εξάγετε QR από PDF σε Java χρησιμοποιώντας το GroupDocs.Parser
  και να εξάγετε τα δεδομένα barcode σε XML για downstream processing.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Μάθετε πώς να εξάγετε QR από PDF σε Java χρησιμοποιώντας το GroupDocs.Parser
  και να εξάγετε τα δεδομένα barcode σε XML για downstream processing.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Πώς να εξάγετε QR από PDF σε Java με το GroupDocs.Parser
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
title: Πώς να εξάγετε QR από PDF σε Java με το GroupDocs.Parser
type: docs
url: /el/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Πώς να εξάγετε QR από PDF σε Java με το GroupDocs.Parser

Σε σύγχρονα επιχειρηματικά ροές εργασίας, **η εξαγωγή QR από PDF** μπορεί να μετατρέψει ένα εμπόδιο χειροκίνητης εισαγωγής δεδομένων σε μια πλήρως αυτοματοποιημένη διαδικασία. Είτε διαχειρίζεστε φορτωτικές manifest, αποδείξεις λιανικής ή καταλόγους προϊόντων, η γρήγορη και αξιόπιστη ανάκτηση πληροφοριών QR είναι απαραίτητη για τα συστήματα downstream. Αυτό το tutorial σας οδηγεί στη χρήση του **GroupDocs.Parser for Java** για την ανάγνωση QR κωδίκων (και άλλων barcode) από PDFs και την εξαγωγή των αποτελεσμάτων σε ένα καθαρό αρχείο XML που μπορεί να καταναλώσει το ERP, το σύστημα απογραφής ή η πλατφόρμα ανάλυσης σας.

## Γρήγορες απαντήσεις
- **Τι κάνει το GroupDocs.Parser for Java;** Διαβάζει αρχεία PDF και εξάγει δομημένα δεδομένα όπως γραμμωτούς κώδικες, πίνακες και κείμενο.  
- **Πώς να εξάγετε QR κώδικες;** Διαμορφώστε το `BarcodeOptions` με τον τύπο QR και καλέστε `parser.getBarcodes()`.  
- **Μπορώ να διαβάσω QR κώδικες σε Java;** Ναι—ορίστε τον τύπο γραμμωτού κώδικα σε `"QR"` στις επιλογές.  
- **Χρειάζομαι άδεια;** Η δοκιμαστική έκδοση λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.  
- **Ποια έκδοση Java απαιτείται;** Συνιστάται Java 8 ή νεότερη.

## Τι σημαίνει «εξαγωγή QR από PDF» στο πλαίσιο της επεξεργασίας PDF;
Η εξαγωγή QR από PDF σημαίνει σάρωση κάθε σελίδας για γραφικά κωδικοποιημένα σε QR, αποκωδικοποίηση των ενσωματωμένων δεδομένων και επιστροφή τους σε μορφή φιλική προς το πρόγραμμα. Το GroupDocs.Parser αφαιρεί την ανάγκη για χαμηλού επιπέδου ανάλυση εικόνας, ώστε να εστιάσετε στη λογική της επιχείρησης αντί για τη διαχείριση εικονοστοιχείων.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Parser για εξαγωγή QR;
Το GroupDocs.Parser υποστηρίζει **πάνω από 30 μορφές εισόδου** και μπορεί να επεξεργαστεί PDFs έως **500 MB** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, παρέχοντας υψηλή ακρίβεια ακόμη και σε χαμηλής ανάλυσης σκαναρίσματα. Μπορείτε να επιλέξετε `QualityMode.Low` για ταχύτητα ή `QualityMode.High` για μέγιστη ακρίβεια, και το ίδιο API λειτουργεί για PDFs, εικόνες και έγγραφα Office, εξαλείφοντας την ανάγκη πολλαπλών βιβλιοθηκών.

## Προαπαιτούμενα
- **GroupDocs.Parser for Java** (έκδοση 25.5 ή νεότερη).  
- Maven ή χειροκίνητη λήψη JAR.  
- Περιβάλλον ανάπτυξης Java 8+ (IntelliJ IDEA, Eclipse ή οποιοσδήποτε επεξεργαστής).  

## Ρύθμιση του GroupDocs.Parser για Java
### Χρήση Maven
Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση στο `pom.xml` σας:

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

### Άμεση λήψη
Εναλλακτικά, κατεβάστε το τελευταίο JAR από [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Βήματα απόκτησης άδειας
- **Δωρεάν δοκιμή:** Δοκιμή 30 ημερών με πλήρες σύνολο λειτουργιών.  
- **Προσωρινή άδεια:** Ζητήστε προσωρινό κλειδί για εκτεταμένη αξιολόγηση.  
- **Αγορά:** Αποκτήστε εμπορική άδεια για παραγωγικές εγκαταστάσεις.

### Βασική αρχικοποίηση και ρύθμιση
Δημιουργήστε μια παρουσία `Parser` που δείχνει στο PDF που θέλετε να αναλύσετε:

`Parser` είναι η κύρια κλάση στο GroupDocs.Parser που αντιπροσωπεύει ένα έγγραφο και παρέχει μεθόδους για εξαγωγή περιεχομένου όπως κείμενο, πίνακες και γραμμωτούς κώδικες.  

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

## Πώς να διαβάσετε QR κώδικες σε PDF Java χρησιμοποιώντας το GroupDocs.Parser
Η ανάγνωση QR κωδίκων σε PDF Java με το GroupDocs.Parser περιλαμβάνει τη δημιουργία μιας παρουσίας parser, τη διαμόρφωση επιλογών barcode για στόχευση QR τύπων, την κλήση της μεθόδου εξαγωγής barcode και, στη συνέχεια, τη διαχείριση των αντικειμένων barcode που επιστρέφονται. Η διαδικασία είναι απλή, λειτουργεί σε οποιαδήποτε σελίδα PDF και επιστρέφει τις αποκωδικοποιημένες τιμές μαζί με μεταδεδομένα θέσης για περαιτέρω επεξεργασία.

### Βήμα 1: επαλήθευση υποστήριξης γραμμωτού κώδικα
Πριν επιχειρήσετε την εξαγωγή, βεβαιωθείτε ότι η μορφή του εγγράφου υποστηρίζει σάρωση γραμμωτών κωδίκων:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Εξήγηση:* Αυτό το μέτρο αποτρέπει σφάλματα χρόνου εκτέλεσης σε μη υποστηριζόμενους τύπους αρχείων.

### Βήμα 2: διαμόρφωση επιλογών γραμμωτού κώδικα (ανάγνωση QR κωδίκων Java)
`BarcodeOptions` είναι ένα αντικείμενο διαμόρφωσης που σας επιτρέπει να καθορίσετε ποιες συμβολές barcode θα ανιχνευθούν, να ορίσετε τη λειτουργία ποιότητας σάρωσης και να ρυθμίσετε παραμέτρους όπως τα όρια ανίχνευσης, εξασφαλίζοντας βέλτιστη απόδοση για τους στόχους QR κώδικα.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Εξήγηση:* `QualityMode.Low` επιταχύνει την επεξεργασία· μεταβείτε σε `High` εάν χρειάζεστε επιπλέον ακρίβεια. Το όρισμα `"QR"` λέει στη μηχανή να ψάχνει μόνο για QR‑τύπου barcode.

### Βήμα 3: εξαγωγή των δεδομένων QR
`parser.getBarcodes(options)` σαρώνει το έγγραφο χρησιμοποιώντας τις παρεχόμενες `BarcodeOptions` και επιστρέφει μια συλλογή αντικειμένων `PageBarcodeArea`, το καθένα από τα οποία περιλαμβάνει την αποκωδικοποιημένη τιμή QR, τον αριθμό σελίδας και τις ακριβείς συντεταγμένες του barcode στη σελίδα, επιτρέποντας ακριβή επεξεργασία downstream.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Εξήγηση:* `parser.getBarcodes` επιστρέφει μια επαναλήψιμη συλλογή αντικειμένων `PageBarcodeArea`, το καθένα περιέχει την αποκωδικοποιημένη τιμή QR και τη θέση της στη σελίδα.

## Εξαγωγή των εξαγόμενων δεδομένων σε XML
### Βήμα 4: αρχικοποίηση του XML εξαγωγέα
`XmlExporter` είναι μια βοηθητική κλάση που μετατρέπει μια συλλογή αντικειμένων barcode σε ένα καλά δομημένο έγγραφο XML, δημιουργώντας αυτόματα στοιχεία για κάθε barcode με χαρακτηριστικά για δείκτη σελίδας, θέση και αποκωδικοποιημένη τιμή, τα οποία μπορούν στη συνέχεια να αποθηκευτούν ή να μεταδοθούν σε άλλα συστήματα.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Εξήγηση:* Το `XmlExporter` διαχειρίζεται τη σειριοποίηση των αντικειμένων barcode σε τυπικό XML, έτοιμο για ενσωμάτωση σε ERP ή συστήματα απογραφής.

### Βήμα 5: εγγραφή του αρχείου XML
Αποθηκεύστε τις εξαγόμενες πληροφορίες QR στο δίσκο:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Εξήγηση:* Το παραγόμενο `data.xml` περιέχει ένα στοιχείο `<Barcode>` ανά QR κώδικα, με χαρακτηριστικά για αριθμό σελίδας, συντεταγμένες και αποκωδικοποιημένη τιμή.

## Πρακτικές εφαρμογές
1. **Διαχείριση αποθεμάτων:** Αυτόματη ενημέρωση βάσεων δεδομένων αποθέματος διαβάζοντας QR ετικέτες σε εισερχόμενα PDF αποστολών.  
2. **Ορατότητα αλυσίδας εφοδιασμού:** Παρακολούθηση πακέτων σε πραγματικό χρόνο εξάγοντας QR αναγνωριστικά ενσωματωμένα σε έγγραφα logistics.  
3. **Αποδείξεις λιανικής:** Ανάκτηση προωθητικών ή εγγυητικών πληροφοριών από QR κώδικες που τυπώνονται σε ψηφιακές αποδείξεις.

## Σκέψεις απόδοσης
- **Διαχείριση μνήμης:** Για πολύ μεγάλα PDFs, επεξεργαστείτε τις σελίδες με ροή αντί να φορτώνετε ολόκληρο το αρχείο στη μνήμη.  
- **Επιλογή QualityMode:** Χρησιμοποιήστε `Low` για μαζική επεξεργασία· μεταβείτε σε `High` όταν αντιμετωπίζετε σκαναρίσματα χαμηλής ανάλυσης.  
- **Ενημερώσεις βιβλιοθήκης:** Κρατήστε το GroupDocs.Parser ενημερωμένο για να επωφεληθείτε από τις τελευταίες βελτιώσεις απόδοσης και διορθώσεις σφαλμάτων.

## Συχνά προβλήματα & αντιμετώπιση
| Συμπτωμα | Πιθανή αιτία | Διόρθωση |
|----------|--------------|----------|
| Δεν επιστρέφονται barcode | Λάθος τύπος barcode καθορισμένος | Αλλάξτε το `"QR"` στον κατάλληλο τύπο (π.χ., `"CODE_128"`). |
| Σφάλμα Out‑of‑memory σε μεγάλα PDFs | Φόρτωση ολόκληρου του εγγράφου ταυτόχρονα | Επεξεργαστείτε τις σελίδες ξεχωριστά ή αυξήστε το μέγεθος heap της JVM (`-Xmx2g`). |
| Κενό αρχείο XML | `exportBarcodes` κλήθηκε πριν από την εξαγωγή | Βεβαιωθείτε ότι `parser.getBarcodes(options)` επιστρέφει δεδομένα πριν την εξαγωγή. |

## Συχνές ερωτήσεις
**Ε: Μπορώ να εξάγω γραμμωτούς κώδικες από αρχεία εικόνας χρησιμοποιώντας το GroupDocs.Parser;**  
Α: Ναι, η βιβλιοθήκη υποστηρίζει εξαγωγή barcode από κοινές μορφές εικόνας (PNG, JPEG, TIFF).

**Ε: Ποιες μορφές barcode αναγνωρίζονται;**  
Α: QR, Code 39, Code 128, DataMatrix, PDF417 και πολλές άλλες. Ανατρέξτε στην τεκμηρίωση API για την πλήρη λίστα.

**Ε: Πώς πρέπει να διαχειριστώ PDFs προστατευμένα με κωδικό;**  
Α: Περνάτε τον κωδικό στον κατασκευαστή `Parser`: `new Parser(filePath, "password")`.

**Ε: Είναι η δοκιμαστική έκδοση επαρκής για δοκιμές παραγωγής;**  
Α: Η δοκιμαστική έκδοση παρέχει πλήρη λειτουργικότητα αλλά προσθέτει υδατογράφημα στα εξαγόμενα δεδομένα. Για παραγωγή, αποκτήστε εμπορική άδεια.

**Ε: Τι γίνεται αν το PDF μου περιέχει τόσο QR όσο και γραμμωτούς κώδικες;**  
Α: Δημιουργήστε πολλαπλές εμφανίσεις `BarcodeOptions` ή περάστε έναν πίνακα τύπων για σάρωση όλων των απαιτούμενων μορφών σε μία κλήση.

---

**Τελευταία ενημέρωση:** 2026-10-12  
**Δοκιμή με:** GroupDocs.Parser 25.5  
**Συγγραφέας:** GroupDocs  

## Πόροι
- [Τεκμηρίωση GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Αναφορά API](https://reference.groupdocs.com/parser/java)
- [Λήψη GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Αποθετήριο GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Δωρεάν φόρουμ υποστήριξης](https://forum.groupdocs.com/c/parser)
- [Αίτηση προσωρινής άδειας](https://purchase.groupdocs.com/temporary-license/)

## Σχετικά Μαθήματα

- [Εξαγωγή Barcode PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Πώς να φορτώσετε PDF από URL με GroupDocs.Parser for Java](/parser/java/document-loading/)
- [Εξαγωγή δεδομένων φόρμας PDF με GroupDocs.Parser σε Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)