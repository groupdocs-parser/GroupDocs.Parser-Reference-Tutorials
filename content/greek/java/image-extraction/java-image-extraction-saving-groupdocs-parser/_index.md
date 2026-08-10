---
date: '2026-08-10'
description: Μάθετε πώς να εξάγετε εικόνες pdf java και να αποθηκεύσετε εικόνες PDF
  png με το GroupDocs.Parser. Οδηγός Java βήμα‑βήμα με αποσπάσματα κώδικα.
keywords:
- extract images pdf java
- convert pdf images png
- save pdf images png
lastmod: '2026-08-10'
og_description: Εξάγετε εικόνες pdf java και αποθηκεύστε εικόνες PDF png με το GroupDocs.Parser.
  Ακολουθήστε αυτόν τον οδηγό Java για γρήγορη, αξιόπιστη εξαγωγή εικόνων.
og_image_alt: 'Java guide: extracting images from PDF and saving as PNG with GroupDocs.Parser'
og_title: Εξαγωγή εικόνων pdf java – αποθήκευση εικόνων PDF ως PNG χρησιμοποιώντας
  το GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract images pdf java and save PDF images png with GroupDocs.Parser.
    Step‑by‑step Java guide with code snippets.
  headline: Extract images pdf java – save PDF images as PNG using GroupDocs
  type: TechArticle
- questions:
  - answer: PDFs, Word (`.docx`), Excel (`.xlsx`), PowerPoint, ZIP archives containing
      supported files, and many more.
    question: What formats does GroupDocs.Parser support for image extraction?
  - answer: Yes. Provide the password when constructing the `Parser` object.
    question: Can I extract images from password‑protected PDFs?
  - answer: Process them page‑by‑page, release resources after each batch, and consider
      increasing the JVM heap size if needed.
    question: How should I handle very large documents?
  - answer: Absolutely. GroupDocs.Parser also extracts text, tables, and metadata.
    question: Is it possible to extract other data types besides images?
  - answer: The API will throw `UnsupportedDocumentFormatException`; you can catch
      this and fallback to an alternative strategy (e.g., convert the file first).
    question: What if image extraction isn’t supported for a specific file?
  type: FAQPage
tags:
- extract images pdf
- GroupDocs.Parser
- Java image extraction
title: Εξαγωγή εικόνων pdf java – αποθήκευση εικόνων PDF ως PNG χρησιμοποιώντας το
  GroupDocs
type: docs
url: /el/java/image-extraction/java-image-extraction-saving-groupdocs-parser/
weight: 1
---

# Εξαγωγή εικόνων pdf java – αποθήκευση εικόνων PDF ως PNG χρησιμοποιώντας το GroupDocs

Στα σύγχρονα ροές εργασίας που εστιάζουν στα έγγραφα, **extract images pdf java** είναι μια κοινή απαίτηση που σας εξοικονομεί το χειροκίνητο άνοιγμα των PDF για αντιγραφή εικόνων. Είτε χρειάζεστε φωτογραφίες προϊόντων από καταλόγους, λογότυπα από συμβάσεις ή στιγμιότυπα οθόνης από αναφορές, η αυτοματοποίηση της εξαγωγής με Java και GroupDocs.Parser σας επιτρέπει να αντλήσετε κάθε ενσωματωμένη ραστική εικόνα σε δευτερόλεπτα. Αυτός ο οδηγός σας καθοδηγεί στη εγκατάσταση της βιβλιοθήκης, την εξαγωγή εικόνων από PDF (και άλλες μορφές), και **αποθήκευση εικόνων ως PNG** αρχεία έτοιμα για επεξεργασία.

## Γρήγορες απαντήσεις
- **Τι σημαίνει “extract images from PDF”;** Αυτή είναι η διαδικασία του προγραμματιστικού ανάγνωσης ενός PDF και εξαγωγής κάθε ενσωματωμένης ραστικής εικόνας.  
- **Ποια βιβλιοθήκη το διαχειρίζεται σε Java;** Το GroupDocs.Parser για Java παρέχει ένα απλό API για εξαγωγή εικόνων σε πολλές τύπους εγγράφων.  
- **Μπορώ να αποθηκεύσω τα εξαγόμενα αρχεία ως PNG;** Ναι – χρησιμοποιήστε `ImageOptions(ImageFormat.Png)` όταν καλείτε `image.save()`.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται εμπορική άδεια για παραγωγή.  
- **Μπορεί να εξαχθούν εικόνες από αρχεία Word, Excel ή ZIP;** Απολύτως – η ίδια κλήση `parser.getImages()` λειτουργεί και για αυτές τις μορφές.

## Τι είναι το extract images pdf java;
Το extract images pdf java αναφέρεται στον προγραμματιστικό εντοπισμό κάθε αντικειμένου ραστικής εικόνας ενσωματωμένου σε έγγραφο PDF και στην ανάκτηση των δυαδικών του δεδομένων ώστε να μπορείτε να επαναχρησιμοποιήσετε, να αναλύσετε ή να αρχειοθετήσετε τις εικόνες χωρίς να ανοίξετε το αρχείο χειροκίνητα. Αυτή η διαδικασία συνήθως περιλαμβάνει την ανάλυση της δομής του PDF, την εξαγωγή των ροών εικόνας και τη γραφή τους σε ξεχωριστά αρχεία εικόνας σε επιλεγμένη μορφή όπως PNG.

## Γιατί να εξάγετε εικόνες από PDF με το GroupDocs.Parser;
Το GroupDocs.Parser μπορεί να επεξεργαστεί **έως 500‑σελίδων PDF σε λιγότερο από 5 δευτερόλεπτα** σε έναν τυπικό διακομιστή 8‑πυρήνων, και υποστηρίζει **πάνω από 50 μορφές εισόδου** συμπεριλαμβανομένων των DOCX, XLSX, PPTX και αρχείων ZIP. Η μηχανή εγγεγραμμένου κώδικα διατηρεί τη χρήση μνήμης χαμηλή, επιτρέποντάς σας να διαχειριστείτε αρχεία πολλαπλών εκατοντάδων σελίδων χωρίς να φορτώνετε ολόκληρο το έγγραφο στη μνήμη. Επιπλέον έχετε πλήρη έλεγχο πάνω στη μορφή εξόδου, την ονομασία αρχείων και την επεξεργασία σε παρτίδες.

## Προαπαιτούμενα
- Java Development Kit (JDK) 8 ή νεότερο.  
- Βασική εξοικείωση με Java I/O και διαχείριση εξαιρέσεων.  
- Maven ή η δυνατότητα προσθήκης εξωτερικών JAR στο πρόγραμμά σας.

### Απαιτούμενες βιβλιοθήκες και εξαρτήσεις
Για να εργαστείτε με το GroupDocs.Parser για Java, συμπεριλάβετε το στο πρόγραμμά σας χρησιμοποιώντας Maven ή κατεβάζοντας τη βιβλιοθήκη απευθείας.

### Απαιτήσεις ρύθμισης περιβάλλοντος
Βεβαιωθείτε ότι το IDE σας (IntelliJ IDEA, Eclipse, VS Code) είναι διαμορφωμένο με το JDK και το Maven (αν επιλέξετε τη διαδρομή Maven).

### Προαπαιτούμενες γνώσεις
Η κατανόηση των ροών αρχείων, του try‑with‑resources και της βασικής αντικειμενοστραφούς Java θα κάνει την υλοποίηση πιο ομαλή.

## Ρύθμιση του GroupDocs.Parser για Java
Για να χρησιμοποιήσετε το GroupDocs.Parser, προσθέστε το στο πρόγραμμά σας χρησιμοποιώντας Maven ή κατεβάστε τη βιβλιοθήκη από τη σελίδα των επίσημων εκδόσεων τους.

### Ρύθμιση Maven
Προσθέστε την παρακάτω διαμόρφωση στο `pom.xml` σας:

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
Εναλλακτικά, κατεβάστε την τελευταία έκδοση από [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

Για ολοκληρωμένους οδηγούς, δείτε την [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/).

### Απόκτηση άδειας
Ξεκινήστε με μια δωρεάν δοκιμή κατεβάζοντας τη βιβλιοθήκη. Για εκτεταμένη χρήση, σκεφτείτε την αγορά άδειας ή την απόκτηση προσωρινής άδειας από [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

#### Βασική αρχικοποίηση και ρύθμιση
Η κλάση `Parser` είναι το σημείο εισόδου για όλες τις λειτουργίες ανάλυσης εγγράφων στο GroupDocs.Parser. Δημιουργείτε ένα αντικείμενο περνώντας τη διαδρομή του αρχείου (και προαιρετικά έναν κωδικό πρόσβασης) στον κατασκευαστή του.

```java
import com.groupdocs.parser.Parser;

public class InitializeParser {
    public static void main(String[] args) {
        // Initialize the Parser object with a document path
        try (Parser parser = new Parser("path/to/your/document")) {
            System.out.println("Parser initialized successfully.");
        } catch (Exception e) {
            System.err.println("Error initializing parser: " + e.getMessage());
        }
    }
}
```

## Πώς να εξάγετε εικόνες από PDF χρησιμοποιώντας το GroupDocs.Parser
Φορτώστε το έγγραφο με `new Parser("yourFile.pdf")` και καλέστε `parser.getImages()` – αυτή η ενιαία κλήση επιστρέφει μια συλλογή όλων των ραστικών εικόνων ενσωματωμένων στο PDF, Word, Excel ή αρχείο ZIP που παρέχετε.

### Οδηγός υλοποίησης
Θα χωρίσουμε την υλοποίηση σε λογικές ενότητες ώστε να μπορείτε να ακολουθήσετε κάθε βήμα ξεκάθαρα.

### Χαρακτηριστικό 1: εξαγωγή εικόνων από ένα έγγραφο
Αυτή η λειτουργία δείχνει πώς να εξάγετε εικόνες χρησιμοποιώντας το GroupDocs.Parser για Java.

#### Επισκόπηση
Θα δημιουργήσετε μια μέθοδο που εξάγει όλες τις εικόνες από ένα συγκεκριμένο έγγραφο και ελέγχει αν η εξαγωγή εικόνων υποστηρίζεται για τη δεδομένη μορφή.

#### Βήματα υλοποίησης

##### Βήμα 1: ρύθμιση του parser
Αρχικοποιήστε το αντικείμενο `Parser` με τη διαδρομή του εγγράφου σας:

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.UnsupportedDocumentFormatException;

public class ExtractImagesFeature {
    public static void extractImages() throws UnsupportedDocumentFormatException, IOException {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.zip";
        
        try (Parser parser = new Parser(documentPath)) {
            Iterable<PageImageArea> images = parser.getImages();
            if (images == null) {
                throw new UnsupportedDocumentFormatException("Page images extraction isn't supported.");
            }
        }
    }
}
```

##### Επεξήγηση
- **`parser.getImages()`** εξάγει κάθε περιοχή εικόνας από το έγγραφο, είτε είναι PDF, Word, Excel ή ακόμη και αρχείο ZIP που περιέχει υποστηριζόμενα αρχεία.  
- **Διαχείριση σφαλμάτων**: Η μέθοδος ρίχνει `UnsupportedDocumentFormatException` εάν η μορφή δεν υποστηρίζει εξαγωγή εικόνων, επιτρέποντάς σας να επανέλθετε με χάρη.

### Χαρακτηριστικό 2: αποθήκευση εξαγόμενων εικόνων σε αρχεία
Αφού έχετε τα αντικείμενα εικόνας, το επόμενο βήμα είναι να τα γράψετε στο δίσκο ως αρχεία PNG.

#### Επισκόπηση
Θα επαναλάβετε πάνω σε κάθε εξαγόμενη εικόνα και θα την αποθηκεύσετε ως αρχείο PNG χρησιμοποιώντας την κλάση `ImageOptions`.

**ImageOptions** καθορίζει τη μορφή εξόδου και τις ρυθμίσεις κωδικοποίησης για τις αποθηκευμένες εικόνες.  
**ImageFormat.Png** είναι μια τιμή enum που επιλέγει τη μορφή εικόνας PNG.

#### Βήματα υλοποίησης

##### Βήμα 1: αποθήκευση κάθε εικόνας
Επαναλάβετε τις εικόνες και αποθηκεύστε τις:

```java
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.options.ImageOptions;
import com.groupdocs.parser.options.ImageFormat;

import java.io.FileOutputStream;
import java.io.IOException;
import java.io.OutputStream;

public class SaveImagesFeature {
    public static void saveExtractedImages(Iterable<PageImageArea> images) throws IOException {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/";
        int imageNumber = 0;
        
        ImageOptions options = new ImageOptions(ImageFormat.Png);

        for (PageImageArea image : images) {
            String outputFilePath = outputPath + String.format("%d.png", imageNumber++);
            
            try (OutputStream outputStream = new FileOutputStream(outputFilePath)) {
                image.save(outputStream, options);
            }
        }
    }
}
```

##### Επεξήγηση
- **`ImageOptions(ImageFormat.Png)`** καθορίζει τη μορφή PNG, η οποία είναι χωρίς απώλειες και ιδανική για στιγμιότυπα οθόνης ή γραφικά που απαιτούν ακριβή πιστότητα.  
- **`image.save()`** γράφει κάθε εικόνα στο σύστημα αρχείων χρησιμοποιώντας το παρεχόμενο ρεύμα εξόδου, επαναχρησιμοποιώντας την ίδια παρουσία `ImageOptions` για απόδοση.

#### Συμβουλές αντιμετώπισης προβλημάτων
- Επαληθεύστε ότι η **διαδρομή εγγράφου** δείχνει σε ένα υπάρχον αρχείο και ότι η εφαρμογή έχει δικαιώματα ανάγνωσης.  
- Βεβαιωθείτε ότι ο **κατάλογος εξόδου** υπάρχει και ότι η διαδικασία έχει δικαιώματα εγγραφής.  
- Για πολύ μεγάλα PDF, σκεφτείτε την επεξεργασία των σελίδων σε παρτίδες για να διατηρήσετε τη χρήση μνήμης χαμηλή.

## Πώς να αποθηκεύσετε εικόνες ως PNG
Φορτώστε το έγγραφο, εξάγετε τις εικόνες και καλέστε `image.save(outputStream, new ImageOptions(ImageFormat.Png))` – αυτή η ενιαία γραμμή γράφει κάθε ραστική εικόνα σε αρχείο PNG διατηρώντας την αρχική ανάλυση και βάθος χρώματος.

## Εξαγωγή εικόνων από αρχεία Word, Excel και ZIP
Το `getImages()` του GroupDocs.Parser λειτουργεί σε πολλές μορφές:

- **Word (`.docx`)** – εξάγει ενσωματωμένες εικόνες και σχέδια.  
- **Excel (`.xlsx`)** – εξάγει διαγράμματα και εισαχθείσες εικόνες.  
- **ZIP** – εάν το αρχείο περιέχει υποστηριζόμενα έγγραφα, ο parser θα επεξεργαστεί κάθε καταχώρηση και θα επιστρέψει τις εικόνες τους.

Απλώς αντικαταστήστε τη μεταβλητή `documentPath` με τη διαδρομή προς το αρχείο `.docx`, `.xlsx` ή `.zip` και επαναχρησιμοποιήστε την ίδια λογική εξαγωγής και αποθήκευσης.

## Πρακτικές εφαρμογές
Το GroupDocs.Parser μπορεί να ενσωματωθεί σε διάφορα συστήματα, ενισχύοντας τη λειτουργικότητα:

1. **Αυτοματοποιημένη επεξεργασία εγγράφων** – εξάγετε εικόνες από τιμολόγια ή συμβάσεις για αυτοματοποιημένη εισαγωγή δεδομένων.  
2. **Συστήματα αρχειοθέτησης** – αποθηκεύστε εικόνες εγγράφων κεντρικά για γρήγορη οπτική ανάκτηση.  
3. **Συστήματα διαχείρισης περιεχομένου (CMS)** – αυτόματη λήψη μέσων από ανεβασμένα έγγραφα.

## Σκέψεις απόδοσης
Για να διατηρήσετε την εφαρμογή Java σας ανταποκρινόμενη όταν διαχειρίζεστε μεγάλες παρτίδες:

- **Κλείστε τα ρεύματα άμεσα** χρησιμοποιώντας try‑with‑resources (όπως φαίνεται).  
- **Επαναχρησιμοποιήστε το `ImageOptions`** αντί να δημιουργείτε νέα παρουσία ανά εικόνα.  
- **Επεξεργαστείτε τα έγγραφα διαδοχικά ή σε ελεγχόμενο pool νήματος** για να αποφύγετε αιχμές μνήμης.  
- Το GroupDocs.Parser μπορεί να εξάγει εικόνες από PDF 300‑σελίδων σε **λιγότερο από 4 δευτερόλεπτα** ενώ χρησιμοποιεί λιγότερο από **200 MB** μνήμης heap.

## Συμπέρασμα
Σε αυτό το σεμινάριο μάθατε πώς να ρυθμίσετε το GroupDocs.Parser για Java, **extract images pdf java**, και **αποθήκευση εικόνων ως PNG** αρχεία. Αυτή η δυνατότητα μπορεί να επιταχύνει δραματικά τις ροές εργασίας που εστιάζουν στα έγγραφα σε οποιαδήποτε λύση βασισμένη σε Java.

### Επόμενα βήματα
Εξερευνήστε την [τεκμηρίωση GroupDocs](https://docs.groupdocs.com/parser/java/) για να ανακαλύψετε πρόσθετες λειτουργίες όπως εξαγωγή κειμένου, ανάλυση πινάκων και υποστήριξη OCR. Για λεπτομερείς υπογραφές μεθόδων, δείτε το [API Reference](https://apireference.groupdocs.com/parser/java).

### Κλήση σε δράση
Ξεκινήστε να εφαρμόζετε αυτά τα αποσπάσματα στο πρόγραμμά σας σήμερα—η αυτοματοποιημένη γραμμή εξαγωγής εικόνων είναι μόνο μερικές γραμμές κώδικα μακριά!

## Συχνές ερωτήσεις

**Q: Ποιες μορφές υποστηρίζει το GroupDocs.Parser για εξαγωγή εικόνων;**  
A: PDFs, Word (`.docx`), Excel (`.xlsx`), PowerPoint, αρχεία ZIP που περιέχουν υποστηριζόμενα αρχεία, και πολλά άλλα.

**Q: Μπορώ να εξάγω εικόνες από PDF με προστασία κωδικού;**  
A: Ναι. Παρέχετε τον κωδικό πρόσβασης κατά τη δημιουργία του αντικειμένου `Parser`.

**Q: Πώς πρέπει να διαχειριστώ πολύ μεγάλα έγγραφα;**  
A: Επεξεργαστείτε τα σελίδα‑με‑σελίδα, ελευθερώστε πόρους μετά από κάθε παρτίδα, και σκεφτείτε την αύξηση του μεγέθους heap της JVM αν χρειαστεί.

**Q: Είναι δυνατόν να εξαχθούν άλλοι τύποι δεδομένων εκτός από εικόνες;**  
A: Απόλυτα. Το GroupDocs.Parser εξάγει επίσης κείμενο, πίνακες και μεταδεδομένα.

**Q: Τι γίνεται αν η εξαγωγή εικόνων δεν υποστηρίζεται για ένα συγκεκριμένο αρχείο;**  
A: Το API θα ρίξει `UnsupportedDocumentFormatException`; μπορείτε να το πιάσετε και να στραφείτε σε εναλλακτική στρατηγική (π.χ., μετατρέψτε πρώτα το αρχείο).

---

**Last Updated:** 2026-08-10  
**Tested With:** GroupDocs.Parser 25.5 for Java  
**Author:** GroupDocs

## Σχετικά Σεμινάρια

- [εξαγωγή εικόνων pdf με GroupDocs.Parser Java – Tutorials](/parser/java/image-extraction/)
- [Εξαγωγή εικόνων PDF από συγκεκριμένες περιοχές χρησιμοποιώντας το GroupDocs.Parser Java API](/parser/java/image-extraction/image-extraction-pdf-areas-groupdocs-parser-java/)
- [Πώς να εξάγετε εικόνες Powerpoint χρησιμοποιώντας το GroupDocs.Parser Java (Οδηγός βήμα‑βήμα)](/parser/java/image-extraction/extract-images-powerpoint-groupdocs-parser-java/)