---
date: '2026-02-06'
description: Μάθετε πώς να προεπισκοπείτε αρχεία Excel και να μετατρέπετε xlsx σε
  png χρησιμοποιώντας το GroupDocs.Parser για Java. Αυτό το σεμινάριο καλύπτει τη
  ρύθμιση, την υλοποίηση και τις πρακτικές εφαρμογές.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Πώς να προεπισκοπήσετε αρχεία Excel με το GroupDocs.Parser σε Java
type: docs
url: /el/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Πώς να Προεπισκοπήσετε Αρχεία Excel με το GroupDocs.Parser σε Java

Αν ψάχνετε για **πώς να προεπισκοπήσετε Excel** υπολογιστικά φύλλα προγραμματιστικά, βρίσκεστε στο σωστό μέρος. Σε αυτόν τον οδηγό θα περάσουμε από τη δημιουργία προεπισκοπήσεων εικόνας (PNG) από βιβλία εργασίας `.xlsx` χρησιμοποιώντας το GroupDocs.Parser για Java — ιδανικό για γρήγορα μικρογραφίες, κοινή χρήση στιγμιοτύπων ή δημιουργία λειτουργίας προεπισκόπησης εγγράφων στην εφαρμογή σας.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “προεπισκόπηση Excel”;** Δημιουργία αρχείων εικόνας (π.χ. PNG) που αντιπροσωπεύουν κάθε σελίδα φύλλου εργασίας.  
- **Ποια μορφή συνιστάται;** Το PNG προσφέρει απώλεια‑απαγόρευση ποιότητας και λειτουργεί καλά για μικρογραφίες στο web.  
- **Χρειάζεται άδεια;** Μια δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται εμπορική άδεια για παραγωγή.  
- **Μπορώ να αλλάξω την ανάλυση της εικόνας;** Ναι — ρυθμίστε το DPI στο `PreviewOptions`.  
- **Είναι δυνατόν να προεπισκοπήσετε και άλλες μορφές;** Το GroupDocs.Parser υποστηρίζει επίσης PDF, Word και πολλούς τύπους εικόνων.

## Τι είναι το “πώς να προεπισκοπήσετε Excel” με το GroupDocs.Parser;
Το GroupDocs.Parser διαβάζει βιβλία εργασίας Excel, αποδίδει κάθε φύλλο ως οπτική σελίδα και σας επιτρέπει να μεταφέρετε αυτές τις σελίδες σε αρχεία εικόνας. Αυτό εξαλείφει την ανάγκη για Office interop ή εξωτερικούς μετατροπείς.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Parser για προεπισκοπήσεις Excel;
- **Δεν απαιτείται εγκατάσταση Office** – λειτουργεί σε οποιοδήποτε περιβάλλον Java διακομιστή.  
- **Υποστηρίζει μεγάλα αρχεία** – μεταδίδει τις σελίδες μία‑μια, διατηρώντας τη χρήση μνήμης χαμηλή.  
- **Αποτέλεσμα υψηλής ποιότητας** – έλεγχος DPI, μορφής και επιλογών απόδοσης.  
- **Ευελιξία μεταξύ μορφών** – το ίδιο API λειτουργεί για PDF, έγγραφα Word και άλλα.

## Προαπαιτούμενα
- **Java Development Kit** (8 +).  
- **IDE** όπως IntelliJ IDEA ή Eclipse.  
- **GroupDocs.Parser for Java SDK** – κατεβάστε το από [εδώ](https://releases.groupdocs.com/parser/java/).  
- **Δείγμα αρχείου Excel** (`.xlsx`) που θέλετε να προεπισκοπήσετε.  
- **Maven ή Gradle** (προαιρετικά) για διαχείριση εξαρτήσεων.

## Εισαγωγή Πακέτων
Αυτές οι εισαγωγές σας δίνουν πρόσβαση στον parser, στις επιλογές προεπισκόπησης και στα βοηθητικά εργαλεία ροής.

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

## Οδηγός Βήμα‑βήμα για Δημιουργία Προεπισκοπήσεων Σελίδων Υπολογιστικού Φύλλου

### Βήμα 1: Αρχικοποίηση του Αντικειμένου Parser
Δημιουργήστε ένα αντικείμενο `Parser` που δείχνει στο βιβλίο εργασίας Excel. Το μπλοκ *try‑with‑resources* εξασφαλίζει ότι ο parser κλείνει αυτόματα.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Συμβουλή:** Χρησιμοποιήστε απόλυτη διαδρομή ή ρυθμίστε φάκελο πόρων για να αποφύγετε το `FileNotFoundException`.

### Βήμα 2: Προετοιμασία των Επιλογών Προεπισκόπησης
Ορίστε πώς θα αποθηκευτεί κάθε σελίδα. Η υλοποίηση `ICreatePageStream` επιστρέφει ένα νέο `FileOutputStream` για κάθε φύλλο εργασίας.

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

> Αυτό το βήμα είναι όπου **μετατρέπετε xlsx σε png** — η ροή γράφει δεδομένα PNG στο δίσκο.

### Βήμα 3: Προσθήκη Delegate για Καταγραφή Πληροφοριών Απόδοσης
Αν χρειάζεστε λεπτομέρειες για κάθε αποδοθέν φύλλο (π.χ. διαστάσεις, όνομα φύλλου), εγγραφείτε σε μια κλήση επιστροφής.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Βήμα 4: Καθορισμός Μορφής Εξόδου και DPI
Επιλέξτε PNG ως μορφή εικόνας και ορίστε DPI που ισορροπεί ποιότητα και μέγεθος αρχείου.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Ρυθμίστε το DPI αν χρειάζεστε μικρότερες μικρογραφίες (π.χ. 96) ή εκτυπώσεις υψηλής ανάλυσης (π.χ. 300).

### Βήμα 5: Δημιουργία των Προεπισκοπήσεων
Με όλα τα στοιχεία διαμορφωμένα, καλέστε `generatePreview`. Το SDK θα επαναλάβει κάθε φύλλο και θα καλέσει τη ροή που παρείχατε.

```java
parser.generatePreview(previewOptions);
```

### Βήμα 6: Ορισμός της Βοηθητικής Μεθόδου `getOutputPath()`
Αυτή η μέθοδος δημιουργεί όνομα αρχείου βάσει του αριθμού σελίδας (φύλλου). Μπορείτε να προσαρμόσετε τη δομή φακέλων όπως θέλετε.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Κοινό λάθος:** Η παράλειψη δημιουργίας του καταλόγου `output` εκ των προτέρων θα προκαλέσει `IOException`. Δημιουργήστε το προγραμματιστικά ή βεβαιωθείτε ότι υπάρχει.

## Πλήρες Παράδειγμα Εργασίας (Απλοποιημένο)

Παρακάτω υπάρχει μια σύντομη έκδοση που ενώνει όλα τα κομμάτια. Δείχνει τη ροή **δημιουργίας προεπισκόπησης σελίδας Excel** από την αρχή μέχρι το τέλος.

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

Εκτελέστε αυτό το απόσπασμα και θα βρείτε μια σειρά αρχείων `preview_page_1.png`, `preview_page_2.png`, … στον φάκελο `output` — το καθένα αντιπροσωπεύει ένα φύλλο από το αρχικό βιβλίο εργασίας Excel.

## Συχνά Προβλήματα & Λύσεις
| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| **Δεν δημιουργούνται εικόνες** | `getOutputPath` επιστρέφει μη έγκυρο φάκελο | Βεβαιωθείτε ότι ο προορισμός υπάρχει ή δημιουργήστε τον με `new File("output").mkdirs();` |
| **Σφάλμα έλλειψης μνήμης σε τεράστια αρχεία** | Φόρτωση ολόκληρου βιβλίου εργασίας ταυτόχρονα | Χρησιμοποιήστε την προσέγγιση ροής (όπως φαίνεται) και επεξεργαστείτε τις σελίδες μία‑μια |
| **Λάθος DPI** | `setDpi` δεν κλήθηκε ή είναι στην προεπιλογή (96) | Καλέστε `previewOptions.setDpi(η_επιθυμητή_τιμή);` πριν από το `generatePreview` |
| **Μη υποστηριζόμενη μορφή** | Προσπάθεια προεπισκόπησης κατεστραμμένου `.xlsx` | Επικυρώστε το αρχείο με το Excel ή χρησιμοποιήστε `Parser.isSupported` πριν την επεξεργασία |

## Συχνές Ερωτήσεις

**Ε: Μπορώ να δημιουργήσω προεπισκοπήσεις για PDF και εικόνες χρησιμοποιώντας το GroupDocs.Parser;**  
Α: Ναι, το ίδιο API λειτουργεί για PDF, έγγραφα Word και πολλές μορφές εικόνας.

**Ε: Πώς αλλάζω τη μορφή εξόδου της εικόνας;**  
Α: Καλέστε `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (ή `Gif`, `Bmp`, κ.λπ.).

**Ε: Η απόδοση αποτελεί πρόβλημα με πολύ μεγάλα βιβλία εργασίας;**  
Α: Το SDK μεταδίδει τις σελίδες, διατηρώντας τη χρήση μνήμης χαμηλή. Για τεράστια αρχεία, σκεφτείτε επεξεργασία σε παράλληλα παρτίδες.

**Ε: Πώς μπορώ να διαχειριστώ σφάλματα κατά τη δημιουργία προεπισκοπήσεων;**  
Α: Τυλίξτε τον κώδικα σε μπλοκ try‑catch (όπως φαίνεται) και καταγράψτε τις λεπτομέρειες της εξαίρεσης. Βεβαιωθείτε ότι οι ροές κλείνουν στο μπλοκ `finally` αν δεν χρησιμοποιείτε try‑with‑resources.

**Ε: Η βιβλιοθήκη απαιτεί εγκατάσταση του Microsoft Office;**  
Α: Όχι. Το GroupDocs.Parser είναι μια καθαρή λύση Java και λειτουργεί σε οποιαδήποτε πλατφόρμα που υποστηρίζει Java 8+.

## Συμπέρασμα
Τώρα έχετε μια πλήρη, έτοιμη για παραγωγή μέθοδο για **πώς να προεπισκοπήσετε Excel** βιβλία εργασίας και **να μετατρέψετε xlsx σε png** χρησιμοποιώντας το GroupDocs.Parser. Ρυθμίστε το DPI, το φάκελο εξόδου ή τη μορφή εικόνας ώστε να ταιριάζει στις ανάγκες του έργου σας και ενσωματώστε αυτό το απόσπασμα σε μεγαλύτερες ροές διαχείρισης εγγράφων.

Έτοιμοι για το επόμενο βήμα; Εξερευνήστε την επίσημη [τεκμηρίωση](https://docs.groupdocs.com/parser/java/) για προχωρημένες επιλογές απόδοσης, αρχεία με προστασία κωδικού και τεχνικές επεξεργασίας παρτίδας.

---

**Τελευταία ενημέρωση:** 2026-02-06  
**Δοκιμασμένο με:** GroupDocs.Parser 23.11 (τελευταία έκδοση τη στιγμή της συγγραφής)  
**Συγγραφέας:** GroupDocs