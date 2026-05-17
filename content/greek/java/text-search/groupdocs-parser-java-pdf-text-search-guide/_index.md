---
date: '2026-04-21'
description: Μάθετε πώς να αναζητήσετε πολλαπλές λέξεις‑κλειδιά σε PDF και να αναζητήσετε
  PDF ανά αριθμό σελίδας χρησιμοποιώντας το GroupDocs.Parser για Java. Λάβετε κώδικα
  βήμα‑βήμα, διαχείριση σφαλμάτων και συμβουλές απόδοσης.
keywords:
- search multiple keywords in pdf
- search pdf by page number
- GroupDocs.Parser for Java
title: Αναζήτηση πολλαπλών λέξεων‑κλειδιών σε PDF με το GroupDocs.Parser για Java
  – Ένας ολοκληρωμένος οδηγός
type: docs
url: /el/java/text-search/groupdocs-parser-java-pdf-text-search-guide/
weight: 1
---

# Αναζήτηση πολλαπλών λέξεων-κλειδιών σε PDF χρησιμοποιώντας το GroupDocs.Parser για Java

Η αναζήτηση σε έγγραφα PDF για να βρεθεί συγκεκριμένο κείμενο μπορεί να είναι προκλητική, ειδικά όταν εργάζεστε με μεγάλα αρχεία ή πολλαπλές σελίδες. **Αν χρειάζεστε να αναζητήσετε πολλαπλές λέξεις-κλειδιά σε PDF** αρχεία γρήγορα και αξιόπιστα, η βιβλιοθήκη GroupDocs.Parser για Java παρέχει μια καθαρή, υψηλής απόδοσης λύση. Αυτό το tutorial σας καθοδηγεί στη ρύθμιση της βιβλιοθήκης, την αναζήτηση ανά αριθμό σελίδας και τη διαχείριση μη υποστηριζόμενων μορφών — όλα με παραδείγματα πραγματικού κόσμου που μπορείτε να αντιγράψετε στο έργο σας.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη σας βοηθά να αναζητήσετε πολλαπλές λέξεις-κλειδιά σε PDF;** GroupDocs.Parser for Java.  
- **Μπορείτε να περιορίσετε τα αποτελέσματα σε συγκεκριμένους αριθμούς σελίδων;** Ναι, χρησιμοποιώντας `SearchOptions` μπορείτε να ανακτήσετε το δείκτη σελίδας για κάθε αντιστοίχηση.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται πληρωμένη άδεια για παραγωγή.  
- **Υποστηρίζεται regex;** Απόλυτα – ενεργοποιήστε το στο `SearchOptions`.  
- **Ποια έκδοση της Java απαιτείται;** Java 8 ή νεότερη με εργαλεία κατασκευής Maven ή Gradle.

## Τι είναι η «αναζήτηση πολλαπλών λέξεων-κλειδιών σε pdf»;
Όταν χρειάζεται να εντοπίσετε αρκετούς όρους — όπως «invoice», «due date» ή «total» — σε ένα μεγάλο PDF, μια αναζήτηση σε μία διέλευση που επιστρέφει τους αριθμούς σελίδων για κάθε αντιστοίχηση εξοικονομεί χρόνο και την πολυπλοκότητα του κώδικα. Το GroupDocs.Parser αφαιρεί την χαμηλού επιπέδου ανάλυση PDF, παρέχοντάς σας ένα απλό API για την εκτέλεση αυτών των ερωτημάτων πολλαπλών λέξεων-κλειδιών.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Parser για Java;
- **Ακριβής εξαγωγή κειμένου** ακόμη και από σαρωμένα ή σύνθετα PDFs.  
- **Ενσωματωμένη ευρετηρίαση σελίδων** ώστε να γνωρίζετε ακριβώς πού εμφανίζεται κάθε λέξη-κλειδί.  
- **Διαχείριση εξαιρέσεων** για μη υποστηριζόμενες μορφές, κρυπτογραφημένα αρχεία και έγγραφα με υψηλή κατανάλωση μνήμης.  
- **Ενσωμάτωση Maven χωρίς εξαρτήσεις** για γρήγορη ρύθμιση του έργου.

## Προαπαιτούμενα
- **Java 8+** και ένα IDE συμβατό με Maven (IntelliJ IDEA, Eclipse κ.λπ.).  
- **GroupDocs.Parser for Java** (έκδοση 25.5 ή νεότερη).  
- Βασικές γνώσεις διαχείρισης εξαιρέσεων Java και I/O αρχείων.

## Ρύθμιση του GroupDocs.Parser για Java
Μπορείτε να προσθέσετε τη βιβλιοθήκη μέσω Maven ή να την κατεβάσετε απευθείας.

### Χρήση Maven
Προσθέστε το αποθετήριο και την εξάρτηση στο αρχείο `pom.xml` σας:
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
Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).  
**Απόκτηση Άδειας**: Ξεκινήστε με μια δωρεάν δοκιμή ή ζητήστε προσωρινή άδεια για δοκιμή του GroupDocs.Parser. Για μακροπρόθεσμη χρήση, σκεφτείτε την αγορά άδειας.

#### Βασική Αρχικοποίηση και Ρύθμιση
Μόλις η βιβλιοθήκη είναι διαθέσιμη, η αρχικοποίησή της είναι απλή:
```java
import com.groupdocs.parser.Parser;

String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf";
try (Parser parser = new Parser(filePath)) {
    // Your parsing logic here
} catch (Exception e) {
    System.err.println("An error occurred: " + e.getMessage());
}
```

## Οδηγός Υλοποίησης
Θα χωρίσουμε την υλοποίηση σε δύο πρακτικά χαρακτηριστικά:

1. **Αναζήτηση πολλαπλών λέξεων-κλειδιών σε PDF και ανάκτηση αριθμών σελίδων** – ιδανικό για «search pdf by page number».  
2. **Ευγενική διαχείριση σφαλμάτων για μη υποστηριζόμενες μορφές εγγράφων**.

### Χαρακτηριστικό 1: Αναζήτηση πολλαπλών λέξεων-κλειδιών σε PDF και λήψη δεικτών σελίδων
#### Επισκόπηση
Η μέθοδος `search` του GroupDocs.Parser, σε συνδυασμό με το `SearchOptions`, σας επιτρέπει να εντοπίσετε οποιονδήποτε όρο (ή μοτίβο κανονικής έκφρασης) και επιστρέφει τόσο τη θέση χαρακτήρα όσο και το δείκτη σελίδας.

#### Βήμα‑βήμα
**Βήμα 1 – Εισαγωγή των απαιτούμενων κλάσεων**  
```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.SearchResult;
import com.groupdocs.parser.options.SearchOptions;
import com.groupdocs.parser.exceptions.UnsupportedDocumentFormatException;
```

**Βήμα 2 – Αρχικοποίηση του parser και ρύθμιση του `SearchOptions`**  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // Replace with actual document path

try (Parser parser = new Parser(filePath)) {
    if (!parser.getFeatures().isText()) {
        throw new UnsupportedDocumentFormatException("Text extraction isn't supported.");
    }

    // false = case‑insensitive, false = not whole‑word, false = regex disabled, true = return page index
    SearchOptions options = new SearchOptions(false, false, false, true);
    Iterable<SearchResult> results = parser.search("invoice|due date|total", options);
    
    for (SearchResult result : results) {
        System.out.println(String.format("Found at position %d on page %d: %s", 
                                         result.getPosition(), 
                                         result.getPageIndex() + 1, // pages are zero‑based
                                         result.getText()));
    }
} catch (UnsupportedDocumentFormatException e) {
    System.err.println(e.getMessage());
}
```

**Εξήγηση βασικών παραμέτρων**
- `filePath`: Διαδρομή προς το PDF που θέλετε να αναζητήσετε.  
- `SearchOptions(false, false, false, true)`:  
  * **Case‑sensitive** – `false` κάνει την αναζήτηση χωρίς διάκριση πεζών‑κεφαλαίων.  
  * **Whole‑word** – `false` επιτρέπει μερικές αντιστοιχίες.  
  * **Regex** – `false` απενεργοποιεί την ανάλυση κανονικής έκφρασης· ορίστε σε `true` αν χρειάζεστε regex.  
  * **Return page index** – `true` εξασφαλίζει ότι κάθε `SearchResult` περιέχει τον αριθμό σελίδας.  

**Συμβουλή:** Η συμβολοσειρά αναζήτησης "invoice|due date|total" χρησιμοποιεί τον τελεστή pipe (`|`) για να αναζητήσει *πολλαπλές λέξεις-κλειδιά* σε μία κλήση.

#### Επίλυση Προβλημάτων
- **Κενά αποτελέσματα:** Επαληθεύστε ότι το PDF περιέχει πραγματικό κείμενο που μπορεί να επιλεγεί (όχι μόνο εικόνες).  
- **Λανθασμένοι αριθμοί σελίδων:** Θυμηθείτε ότι το `getPageIndex()` είναι μηδενικής βάσης· προσθέστε `+1` για αριθμό που διαβάζει ο άνθρωπος.

### Χαρακτηριστικό 2: Διαχείριση σφαλμάτων για μη υποστηριζόμενες μορφές εγγράφων
#### Επισκόπηση
Δεν είναι δυνατόν κάθε αρχείο να αναλυθεί για κείμενο (π.χ., κάποια κρυπτογραφημένα ή μόνο εικόνα PDFs). Η σύλληψη του `UnsupportedDocumentFormatException` επιτρέπει στην εφαρμογή σας να αποτύχει με χάρη.

#### Implementation
**Βήμα 1 – Τυλίξτε τη δημιουργία του parser σε μπλοκ try‑catch**  
```java
try (Parser parser = new Parser(filePath)) {
    if (!parser.getFeatures().isText()) {
        throw new UnsupportedDocumentFormatException("Text extraction isn't supported.");
    }
} catch (UnsupportedDocumentFormatException e) {
    System.err.println(e.getMessage());
}
```

**Γιατί είναι σημαντικό**  
Ανιχνεύοντας νωρίς μη υποστηριζόμενες μορφές, μπορείτε να ενημερώσετε τους χρήστες, να καταγράψετε το πρόβλημα ή να μεταβείτε σε λύση OCR αντί να καταρρεύσει όλη η διαδικασία.

## Πρακτικές Εφαρμογές
Ακολουθούν τρία κοινά σενάρια όπου η **αναζήτηση πολλαπλών λέξεων-κλειδιών σε PDF** διαπρέπει:

1. **Legal Document Review** – Εντοπίστε ρήτρες όπως «force majeure», «termination» ή «confidentiality» σε εκατοντάδες σελίδες.  
2. **Invoice Processing** – Εξάγετε «invoice number», «due date» και «total amount» σε μία διέλευση για αυτοματοποιημένη λογιστική.  
3. **Academic Research** – Σαρώστε ερευνητικές εργασίες για πολλαπλές παραλλαγές ορολογίας (π.χ., «machine learning», «deep learning», «neural network»).

## Σκέψεις Απόδοσης
- **Ανάλυση μόνο των απαιτούμενων σελίδων**: Εάν γνωρίζετε τα σχετικά τμήματα, περιορίστε το εύρος αναζήτησης για να μειώσετε τη χρήση μνήμης.  
- **Χρησιμοποιήστε try‑with‑resources** (όπως φαίνεται) για να διασφαλίσετε ότι οι parsers κλείνουν άμεσα, αποτρέποντας διαρροές μνήμης.  
- **Αποφύγετε τη φόρτωση ολόκληρου του PDF στη μνήμη** όταν εργάζεστε με πολύ μεγάλα αρχεία· επεξεργαστείτε σε τμήματα αν είναι δυνατόν.

## Συμπέρασμα
Τώρα έχετε μια πλήρη, έτοιμη για παραγωγή προσέγγιση για **αναζήτηση πολλαπλών λέξεων-κλειδιών σε PDF** έγγραφα, ανάκτηση των ακριβών αριθμών σελίδων και ευγενική διαχείριση μη υποστηριζόμενων μορφών χρησιμοποιώντας το GroupDocs.Parser για Java. Ενσωματώστε αυτά τα αποσπάσματα σε μεγαλύτερες ροές εργασίας — επεξεργασία δέσμης, web services ή επιτραπέζιες εφαρμογές — για αυτοματοποίηση της ανάλυσης εγγράφων σε κλίμακα.

**Επόμενα Βήματα**  
- Δοκιμάστε μοτίβα regex για πιο σύνθετες αναζητήσεις.  
- Συνδυάστε τα αποτελέσματα αναζήτησης με έναν PDF writer (π.χ., GroupDocs.Conversion) για επισήμανση των αντιστοιχιών.  
- Εξερευνήστε την επεξεργασία δέσμης επαναλαμβάνοντας έναν φάκελο PDF και αποθηκεύοντας τα αποτελέσματα σε βάση δεδομένων.

## Συχνές Ερωτήσεις
**Q: Μπορώ να αναζητήσω πολλαπλές λέξεις-κλειδιά ταυτόχρονα;**  
A: Ναι. Χρησιμοποιήστε μια συμβολοσειρά διαχωρισμένη με pipe (π.χ., `"invoice|due date|total"`) ή ενεργοποιήστε regex στο `SearchOptions`.

**Q: Τι γίνεται αν το έγγραφό μου είναι κρυπτογραφημένο;**  
A: Παρέχετε τον κωδικό πρόσβασης κατά τη δημιουργία του `Parser`. Εάν δεν έχετε τον κωδικό, η βιβλιοθήκη θα ρίξει μια εξαίρεση που μπορείτε να συλλάβετε.

**Q: Πώς να διαχειριστώ πολύ μεγάλα αρχεία PDF αποδοτικά;**  
A: Επεξεργαστείτε το αρχείο σελίδα‑με‑σελίδα, ή χρησιμοποιήστε το `SearchOptions` για να περιορίσετε το εύρος σε συγκεκριμένες περιοχές σελίδων.

**Q: Είναι το GroupDocs.Parser συμβατό με όλες τις εκδόσεις PDF;**  
A: Υποστηρίζει την πλειονότητα των προτύπων PDF (1.4‑1.7, PDF/A, PDF/X). Πάντα δοκιμάζετε με τα συγκεκριμένα αρχεία σας.

**Q: Μπορεί αυτό να χρησιμοποιηθεί για επεξεργασία δέσμης εγγράφων;**  
A: Απόλυτα. Επανάληψη σε έναν φάκελο, εφαρμογή της ίδιας λογικής αναζήτησης και αποθήκευση των αποτελεσμάτων για κάθε αρχείο.

## Πόροι
- **Τεκμηρίωση**: [GroupDocs.Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- **Αναφορά API**: [GroupDocs API Reference](https://reference.groupdocs.com/parser/java/)

---

**Τελευταία Ενημέρωση:** 2026-04-21  
**Δοκιμάστηκε Με:** GroupDocs.Parser for Java 25.5  
**Συγγραφέας:** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}