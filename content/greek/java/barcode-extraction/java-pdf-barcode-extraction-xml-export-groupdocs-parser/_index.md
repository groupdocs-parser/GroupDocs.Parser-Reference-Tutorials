---
date: '2026-02-19'
description: Μάθετε πώς να διαβάζετε κώδικες QR σε PDF με Java χρησιμοποιώντας το
  GroupDocs.Parser και να εξάγετε τα δεδομένα του barcode σε XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Πώς να διαβάσετε QR κώδικες σε PDF Java με το GroupDocs.Parser
type: docs
url: /el/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Πώς να Διαβάσετε Κώδικες QR σε PDF Java με το GroupDocs.Parser

Στα σύγχρονα επιχειρηματικά ροές εργασίας, **πώς να διαβάσετε QR** κώδικες από έγγραφα PDF μπορεί να κάνει τη διαφορά μεταξύ ενός στενού σημείου χειροκίνητης εισαγωγής δεδομένων και μιας πλήρως αυτοματοποιημένης γραμμής παραγωγής. Είτε διαχειρίζεστε καταλόγους αποστολών, αποδείξεις λιανικής ή καταλόγους προϊόντων, η γρήγορη και αξιόπιστη εξαγωγή πληροφοριών QR είναι απαραίτητη. Αυτό το εκπαιδευτικό υλικό σας οδηγεί στη χρήση του **GroupDocs.Parser for Java** για την ανάγνωση κωδίκων QR (και άλλων barcode) από PDF και την εξαγωγή των αποτελεσμάτων σε ένα καθαρό αρχείο XML που μπορούν να καταναλώσουν τα επόμενα συστήματα.

## Γρήγορες Απαντήσεις
- **Τι κάνει το GroupDocs.Parser for Java;** Διαβάζει αρχεία PDF και εξάγει δομημένα δεδομένα όπως barcode.  
- **Πώς να εξάγετε κώδικες QR;** Ρυθμίζοντας το `BarcodeOptions` με τον τύπο QR και καλώντας το `parser.getBarcodes()`.  
- **Μπορώ να διαβάσω κώδικες QR σε Java;** Ναι—ορίστε τον τύπο barcode σε `"QR"` στις επιλογές.  
- **Χρειάζομαι άδεια;** Η δοκιμαστική έκδοση λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.  
- **Ποια έκδοση Java απαιτείται;** Συνιστάται Java 8 ή νεότερη.

## Τι σημαίνει “πώς να διαβάσετε QR” στο πλαίσιο της επεξεργασίας PDF;
Η ανάγνωση κωδίκων QR από PDF σημαίνει σάρωση κάθε σελίδας για γραφικά κωδικοποιημένα σε QR, αποκωδικοποίηση των ενσωματωμένων δεδομένων και επιστροφή τους σε μορφή φιλική προς το πρόγραμμα. Το GroupDocs.Parser αφαιρεί την ανάλυση εικόνας χαμηλού επιπέδου ώστε να μπορείτε να εστιάσετε στη λογική της επιχείρησης αντί για τη διαχείριση εικονοστοιχείων.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Parser για εξαγωγή QR;
- **Υψηλή ακρίβεια:** Οι ενσωματωμένοι αλγόριθμοι επεξεργασίας εικόνας διαχειρίζονται σαρώσεις χαμηλής ανάλυσης.  
- **Επιλογές απόδοσης:** Επιλέξτε `QualityMode.Low` για ταχύτητα ή `QualityMode.High` για μέγιστη ακρίβεια.  
- **Υποστήριξη πολλαπλών μορφών:** Λειτουργεί με PDF, εικόνες και ακόμη και έγγραφα Office, ώστε να μπορείτε να επαναχρησιμοποιήσετε την ίδια βάση κώδικα για διαφορετικούς τύπους αρχείων.

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

### Άμεση Λήψη
Εναλλακτικά, κατεβάστε το πιο πρόσφατο JAR από [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Βήματα Απόκτησης Άδειας
- **Δωρεάν Δοκιμή:** Δοκιμή 30 ημερών με πλήρες σύνολο λειτουργιών.  
- **Προσωρινή Άδεια:** Ζητήστε ένα προσωρινό κλειδί για εκτεταμένη αξιολόγηση.  
- **Αγορά:** Αποκτήστε εμπορική άδεια για παραγωγικές εγκαταστάσεις.

### Βασική Αρχικοποίηση και Ρύθμιση
Δημιουργήστε ένα αντικείμενο `Parser` που δείχνει στο PDF που θέλετε να αναλύσετε:

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

## Πώς να διαβάσετε κώδικες QR σε PDF Java χρησιμοποιώντας το GroupDocs.Parser
### Βήμα 1: Επαλήθευση Υποστήριξης Barcode
Πριν προσπαθήσετε την εξαγωγή, επιβεβαιώστε ότι η μορφή του εγγράφου υποστηρίζει σάρωση barcode:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Εξήγηση:* Αυτό το μέτρο αποτρέπει σφάλματα χρόνου εκτέλεσης σε μη υποστηριζόμενους τύπους αρχείων.

### Βήμα 2: Ρύθμιση Επιλογών Barcode (Read QR codes Java)
Ορίστε την ποιότητα σάρωσης και καθορίστε ότι ενδιαφέρεστε για κώδικες QR:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Εξήγηση:* Το `QualityMode.Low` επιταχύνει την επεξεργασία· αλλάξτε σε `High` αν χρειάζεστε επιπλέον ακρίβεια. Το όρισμα `"QR"` λέει στη μηχανή να ψάχνει μόνο για barcode τύπου QR.

### Βήμα 3: Εξαγωγή Δεδομένων QR
Ανακτήστε τις πληροφορίες barcode από κάθε σελίδα του PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Εξήγηση:* Το `parser.getBarcodes` επιστρέφει μια επαναλαμβανόμενη συλλογή αντικειμένων `PageBarcodeArea`, το καθένα περιέχει την αποκωδικοποιημένη τιμή QR και τη θέση της στη σελίδα.

## Εξαγωγή Εξαγόμενων Δεδομένων σε XML
### Βήμα 4: Αρχικοποίηση του Εξαγωγέα XML
Δημιουργήστε έναν εξαγωγέα που θα μετατρέπει τη συλλογή barcode σε ένα καλά δομημένο αρχείο XML:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Εξήγηση:* Το `XmlExporter` διαχειρίζεται τη σειριοποίηση των αντικειμένων barcode σε τυπικό XML, έτοιμο για ενσωμάτωση με συστήματα ERP ή αποθεμάτων.

### Βήμα 5: Γράψτε το Αρχείο XML
Αποθηκεύστε τις εξαγόμενες πληροφορίες QR στο δίσκο:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Εξήγηση:* Το αποτέλεσμα `data.xml` περιέχει ένα στοιχείο `<Barcode>` ανά κώδικα QR, με χαρακτηριστικά για αριθμό σελίδας, συντεταγμένες και αποκωδικοποιημένη τιμή.

## Πρακτικές Εφαρμογές
1. **Διαχείριση Αποθεμάτων:** Αυτόματη συμπλήρωση βάσεων δεδομένων αποθέματος διαβάζοντας ετικέτες QR σε PDF εισερχόμενων αποστολών.  
2. **Ορατότητα Εφοδιαστικής Αλυσίδας:** Παρακολούθηση πακέτων σε πραγματικό χρόνο εξάγοντας τα αναγνωριστικά QR ενσωματωμένα σε έγγραφα logistics.  
3. **Αποδείξεις Λιανικής:** Ανάκτηση προωθητικών ή εγγυητικών πληροφοριών από κώδικες QR που τυπώνονται σε ψηφιακές αποδείξεις.

## Σκέψεις Απόδοσης
- **Διαχείριση Μνήμης:** Για πολύ μεγάλα PDF, επεξεργαστείτε τις σελίδες με ροή αντί να φορτώνετε ολόκληρο το αρχείο στη μνήμη.  
- **Επιλογή QualityMode:** Χρησιμοποιήστε `Low` για μαζική επεξεργασία· αλλάξτε σε `High` όταν αντιμετωπίζετε σαρώσεις χαμηλής ανάλυσης.  
- **Ενημερώσεις Βιβλιοθήκης:** Διατηρήστε το GroupDocs.Parser ενημερωμένο για να επωφεληθείτε από τις τελευταίες βελτιώσεις απόδοσης και διορθώσεις σφαλμάτων.

## Συχνά Προβλήματα & Επίλυση
| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|----------|--------------|----------|
| Δεν επιστράφηκαν barcode | Καθορίστηκε λανθασμένος τύπος barcode | Αλλάξτε το `"QR"` στον κατάλληλο τύπο (π.χ., `"CODE_128"`). |
| Σφάλμα έλλειψης μνήμης σε μεγάλα PDF | Ολόκληρο το έγγραφο φορτώνεται ταυτόχρονα | Επεξεργαστείτε τις σελίδες ξεχωριστά ή αυξήστε το μέγεθος heap της JVM (`-Xmx2g`). |
| Κενό αρχείο XML | `exportBarcodes` κλήθηκε πριν την εξαγωγή | Βεβαιωθείτε ότι το `parser.getBarcodes(options)` επιστρέφει δεδομένα πριν την εξαγωγή. |

## Συχνές Ερωτήσεις
**Q:** Μπορώ να εξάγω barcode από αρχεία εικόνας χρησιμοποιώντας το GroupDocs.Parser;  
**A:** Ναι, η βιβλιοθήκη υποστηρίζει εξαγωγή barcode από κοινές μορφές εικόνας (PNG, JPEG, TIFF).

**Q:** Ποιοι τύποι barcode αναγνωρίζονται;  
**A:** QR, Code 39, Code 128, DataMatrix, PDF417 και πολλούς άλλους. Ανατρέξτε στην τεκμηρίωση API για την πλήρη λίστα.

**Q:** Πώς πρέπει να διαχειριστώ PDF με κωδικό πρόσβασης;  
**A:** Περνάτε τον κωδικό στον κατασκευαστή `Parser`: `new Parser(filePath, "password")`.

**Q:** Είναι η δοκιμαστική έκδοση επαρκής για δοκιμές παραγωγής;  
**A:** Η δοκιμαστική έκδοση παρέχει πλήρη λειτουργικότητα αλλά προσθέτει υδατογράφημα στα εξαγόμενα δεδομένα. Για παραγωγή, αποκτήστε εμπορική άδεια.

**Q:** Τι γίνεται αν το PDF μου περιέχει τόσο QR όσο και γραμμικούς barcode;  
**A:** Δημιουργήστε πολλαπλές εμφανίσεις `BarcodeOptions` ή περάστε έναν πίνακα τύπων για σάρωση όλων των απαιτούμενων μορφών σε μία διεργασία.

---

**Τελευταία Ενημέρωση:** 2026-02-19  
**Δοκιμάστηκε Με:** GroupDocs.Parser 25.5  
**Συγγραφέας:** GroupDocs  

## Πόροι
- [Τεκμηρίωση GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Αναφορά API](https://reference.groupdocs.com/parser/java)
- [Λήψη GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Αποθετήριο GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Δωρεάν Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/parser)
- [Αίτηση για Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)

---