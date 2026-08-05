---
date: '2026-08-05'
description: Μάθετε πώς να εξάγετε εικόνες από έγγραφα Word χρησιμοποιώντας το GroupDocs.Parser
  for Java και να αποθηκεύετε τις εικόνες Word σε μορφή PNG αποδοτικά.
keywords:
- extract images from word
- how to extract images
- extract images from docx
- extract pictures from word
- convert word images png
lastmod: '2026-08-05'
og_description: Εξαγωγή εικόνων από έγγραφα Word με το GroupDocs.Parser for Java.
  Μάθετε βήμα‑βήμα πώς να τραβήξετε τις εικόνες και να αποθηκεύετε τις εικόνες Word
  σε μορφή PNG αποδοτικά.
og_image_alt: Code example showing image extraction from a Word document using GroupDocs.Parser
  for Java
og_title: Εξαγωγή εικόνων από Word χρησιμοποιώντας το GroupDocs.Parser for Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to extract images from word documents using GroupDocs.Parser
    for Java and save word images png efficiently.
  headline: Extract images from word using GroupDocs.Parser for Java
  type: TechArticle
- description: Learn how to extract images from word documents using GroupDocs.Parser
    for Java and save word images png efficiently.
  name: Extract images from word using GroupDocs.Parser for Java
  steps:
  - name: initialize the parser
    text: The `Parser` class is the entry point for reading a document. It loads the
      file into memory and prepares all content streams for extraction.
  - name: extract images
    text: '`PageImageArea` objects represent each picture found in the document, regardless
      of whether the image is inline, floating, or part of a shape.'
  - name: configure image options
    text: '`ImageOptions` lets you specify the output format, resolution, and other
      rendering settings before saving each picture.'
  - name: save each image
    text: '`ImageFormat` enum defines the output image format such as PNG, JPEG, or
      BMP. The `save` method writes the binary image data to a file on disk. By passing
      `ImageFormat.Png`, you satisfy the **save word images png** requirement.'
  - name: define helper methods for paths
    text: Utility methods simplify path handling and keep the main extraction logic
      clean and maintainable. Replace `YOUR_DOCUMENT_DIRECTORY` and `YOUR_OUTPUT_DIRECTORY`
      with the actual file system locations you intend to use.
  type: HowTo
- questions:
  - answer: It handles DOC, DOCX, PDF, PPT, PPTX, and many other formats, exposing
      images via the same `getImages()` method.
    question: What file formats does GroupDocs.Parser support for image extraction?
  - answer: Yes—pass the password to the `Parser` constructor, and the library will
      decrypt the document before extraction.
    question: Can I extract images from password‑protected Word files?
  - answer: After retrieving `PageImageArea` objects, inspect `image.getFormat()`
      and filter accordingly before saving.
    question: Is there a way to extract only specific image types (e.g., JPEG only)?
  - answer: While the core API is synchronous, you can wrap the extraction logic in
      a separate thread or use Java’s `CompletableFuture` for parallel processing.
    question: Does the library support asynchronous processing?
  - answer: A free trial is fine for evaluation, but a paid license is required for
      commercial deployments.
    question: Do I need a commercial license for production use?
  type: FAQPage
tags:
- extract images
- GroupDocs.Parser
- Java document processing
title: Εξαγωγή εικόνων από Word χρησιμοποιώντας το GroupDocs.Parser for Java
type: docs
url: /el/java/image-extraction/extract-images-word-docs-groupdocs-parser-java/
weight: 1
---

# Εξαγωγή εικόνων από το Word χρησιμοποιώντας το GroupDocs.Parser για Java

Η εξαγωγή εικόνων από αρχεία Word με το χέρι είναι χρονοβόρα και επιρρεπής σε σφάλματα. Σε αυτό το tutorial θα ανακαλύψετε **πώς να εξάγετε εικόνες από το word** έγγραφα αυτόματα με το GroupDocs.Parser για Java, και στη συνέχεια **να αποθηκεύσετε εικόνες word png** για επεξεργασία downstream. Θα έχετε μια σαφή επισκόπηση του γιατί η βιβλιοθήκη είναι γρήγορη, πώς να τη ρυθμίσετε, και συμβουλές βέλτιστων πρακτικών που σας επιτρέπουν να ενσωματώσετε την εξαγωγή εικόνων σε οποιαδήποτε εφαρμογή Java.

## Γρήγορες απαντήσεις
- **Τι κάνει η βιβλιοθήκη;** Αναλύει Word, PDF και πολλές άλλες μορφές για να αποκαλύψει κείμενο, πίνακες και εικόνες.  
- **Πόσες γραμμές κώδικα;** Περίπου 30 γραμμές Java, συν μερικές γραμμές ρυθμίσεων.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται πλήρης άδεια για παραγωγή.  
- **Μπορώ να εξάγω ενσωματωμένες εικόνες;** Ναι – η μέθοδος `getImages()` επιστρέφει κάθε ενσωματωμένη εικόνα.  
- **Υποστηριζόμενη μορφή εξόδου;** Η προεπιλογή είναι PNG, αλλά άλλες μορφές είναι διαθέσιμες μέσω του `ImageFormat`.

## Τι είναι η “εξαγωγή εικόνων από το word”;
Η εξαγωγή εικόνων από το word αναφέρεται στην προγραμματιστική ανάκτηση όλων των αρχείων εικόνας που είναι ενσωματωμένα σε ένα έγγραφο Microsoft Word. Το GroupDocs.Parser διαβάζει τη δυαδική δομή ενός αρχείου DOCX ή DOC και εμφανίζει κάθε εικόνα ως αντικείμενο `PageImageArea`, επιτρέποντάς σας να εξάγετε κάθε εικόνα χωρίς να ανοίξετε το έγγραφο στο Microsoft Word. Αυτή η προσέγγιση εξαλείφει την χειροκίνητη αντιγραφή‑επικόλληση, μειώνει τα ανθρώπινα σφάλματα και κλιμακώνεται σε χιλιάδες αρχεία σε εργασίες δέσμης.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Parser για Java;
Μπορείτε να εξάγετε εικόνες από έγγραφα word με **ταχύτητα**, **αξιοπιστία** και **διαπλατφορμική ευελιξία**. Το GroupDocs.Parser επεξεργάζεται ένα DOCX 200 σελίδων σε κάτω από 2 δευτερόλεπτα σε έναν τυπικό διακομιστή 2 CPU, και λειτουργεί σε Windows, Linux και macOS χωρίς να απαιτεί Microsoft Office. Η βιβλιοθήκη επίσης αντέχει σε κατεστραμμένα αρχεία, επιστρέφοντας τις εικόνες που είναι ακόμη προσβάσιμες, κάτι που την καθιστά ιδανική για μεγάλης κλίμακας έργα μετεγκατάστασης.

## Προαπαιτούμενα
- **GroupDocs.Parser for Java** (version 25.5 ή νεότερη)  
- **JDK 8+** εγκατεστημένο στο μηχάνημά σας ανάπτυξης  
- Ένα IDE όπως IntelliJ IDEA, Eclipse ή NetBeans για επεξεργασία και εκτέλεση του κώδικα  

## Ρύθμιση του GroupDocs.Parser για Java

Προσθέστε τη βιβλιοθήκη στο Maven project σας:

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

Εναλλακτικά, κατεβάστε την τελευταία έκδοση απευθείας από [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Βήματα απόκτησης άδειας
- **Δωρεάν δοκιμή:** Ξεκινήστε με μια δωρεάν δοκιμή για να εξερευνήσετε τις δυνατότητες.  
- **Προσωρινή άδεια:** Αποκτήστε μια προσωρινή άδεια για εκτεταμένη δοκιμή αν χρειάζεται.  
- **Αγορά:** Αποκτήστε πλήρη άδεια για παραγωγικές εγκαταστάσεις.

## Οδηγός υλοποίησης

Παρακάτω βρίσκεται ο πλήρης, έτοιμος για εκτέλεση κώδικας Java που **εξάγει εικόνες από το word** έγγραφα και τις αποθηκεύει ως αρχεία PNG.

### Βήμα 1: αρχικοποίηση του parser

Η κλάση `Parser` είναι το σημείο εισόδου για την ανάγνωση ενός εγγράφου. Φορτώνει το αρχείο στη μνήμη και προετοιμάζει όλα τα ρεύματα περιεχομένου για εξαγωγή.

```java
// Initialize the Parser with the document path.
try (Parser parser = new Parser(documentPath)) {
    // Proceed with image extraction...
}
```

### Βήμα 2: εξαγωγή εικόνων

Τα αντικείμενα `PageImageArea` αντιπροσωπεύουν κάθε εικόνα που βρέθηκε στο έγγραφο, ανεξάρτητα από το αν η εικόνα είναι ενσωματωμένη, αιωρούμενη ή μέρος ενός σχήματος.

```java
// Extract images from the document.
Iterable<PageImageArea> images = parser.getImages();
```

### Βήμα 3: ρύθμιση επιλογών εικόνας

`ImageOptions` σας επιτρέπει να καθορίσετε τη μορφή εξόδου, την ανάλυση και άλλες ρυθμίσεις απόδοσης πριν αποθηκεύσετε κάθε εικόνα.

```java
// Set options to save images in PNG format.
ImageOptions options = new ImageOptions(ImageFormat.Png);
```

### Βήμα 4: αποθήκευση κάθε εικόνας

Το enum `ImageFormat` ορίζει τη μορφή εξόδου της εικόνας όπως PNG, JPEG ή BMP.  
Η μέθοδος `save` γράφει τα δυαδικά δεδομένα της εικόνας σε αρχείο στο δίσκο. Με τη χρήση του `ImageFormat.Png`, ικανοποιείτε την απαίτηση **save word images png**.

```java
int imageNumber = 0;
for (PageImageArea image : images) {
    String outputPath = YOUR_OUTPUT_DIRECTORY + "/" + imageNumber + ".png";
    image.save(outputPath, options);
    imageNumber++;
}
```

### Βήμα 5: ορισμός βοηθητικών μεθόδων για διαδρομές

Οι βοηθητικές μέθοδοι απλοποιούν τη διαχείριση διαδρομών και διατηρούν την κύρια λογική εξαγωγής καθαρή και συντηρήσιμη.

```java
public static String getDocumentDirectory() {
    return YOUR_DOCUMENT_DIRECTORY;
}

public static String getOutputDirectory() {
    return YOUR_OUTPUT_DIRECTORY;
}
```

Αντικαταστήστε το `YOUR_DOCUMENT_DIRECTORY` και το `YOUR_OUTPUT_DIRECTORY` με τις πραγματικές τοποθεσίες του συστήματος αρχείων που σκοπεύετε να χρησιμοποιήσετε.

## Πώς να εξάγετε ενσωματωμένες εικόνες από docx;
Η μέθοδος `getImages()` επιστρέφει μια συλλογή από αντικείμενα `PageImageArea` που αντιπροσωπεύουν κάθε ενσωματωμένη εικόνα.  
Φορτώστε το DOCX με `new Parser("input.docx")` και καλέστε `parser.getImages()` – η μέθοδος επιστρέφει αυτόματα κάθε ενσωματωμένη εικόνα, συμπεριλαμβανομένων των ενσωματωμένων εικόνων, των αιωρούμενων σχημάτων και των σχεδίων VML. Δεν απαιτούνται πρόσθετες κλήσεις API, έτσι μπορείτε να διατρέξετε τη συλλογή που επιστράφηκε και να επεξεργαστείτε απευθείας κάθε `PageImageArea`.

## Πώς να εξάγετε εικόνες από docx και να τις αποθηκεύσετε ως PNG;
Δημιουργήστε μια παρουσία του `ImageOptions`, ορίστε `options.setImageFormat(ImageFormat.Png)`, και περάστε το στη `image.save(outputPath, options)`. Αυτή η ρύθμιση εξασφαλίζει ότι κάθε εξαγόμενη εικόνα γράφεται ως αρχείο PNG, ικανοποιώντας τον στόχο **save word images png** ενώ διατηρεί την αρχική ανάλυση και βάθος χρώματος.

## Πρακτικές εφαρμογές
1. **Διαχείριση περιεχομένου:** Αποσύρετε εικόνες από παλιά αρχεία Word για μια ψηφιακή βιβλιοθήκη περιουσιακών στοιχείων.  
2. **Μεταφορά δεδομένων:** Μετακινήστε ενσωματωμένα γραφικά σε ένα νέο CMS χωρίς χειροκίνητη αντιγραφή‑επικόλληση.  
3. **Αρχειοθέτηση εγγράφων:** Αποθηκεύστε τις εικόνες ξεχωριστά για να μειώσετε το μέγεθος του αρχείου και να βελτιώσετε την αναζητησιμότητα.  
4. **Αυτοματοποιημένη δημοσίευση:** Τροφοδοτήστε τα εξαγόμενα PNG απευθείας σε γεννήτριες ιστοσελίδων ή πρότυπα email.

## Σκέψεις απόδοσης
- **Χρήση μνήμης:** Κατανείμετε τουλάχιστον `-Xmx2g` όταν επεξεργάζεστε μεγάλα έγγραφα· ο parser μεταδίδει δεδομένα για να διατηρήσει το αποτύπωμα της heap χαμηλό.  
- **Επεξεργασία δέσμης:** Επαναχρησιμοποιήστε μια μόνο παρουσία `Parser` ανά έγγραφο μέσα σε βρόχο για να ελαχιστοποιήσετε το κόστος δημιουργίας αντικειμένων.  
- **Διαχειριστές αρχείων:** Το μπλοκ try‑with‑resources εγγυάται ότι ο parser κλείνει άμεσα, αποτρέποντας διαρροές περιγραφέων.

## Συνηθισμένα προβλήματα και λύσεις
| Πρόβλημα | Λύση |
|-------|----------|
| **OutOfMemoryError** on huge DOCX files | Αυξήστε τη μνήμη heap της JVM ή επεξεργαστείτε το έγγραφο σε μικρότερες δέσμες. |
| **No images returned** | Επαληθεύστε ότι το έγγραφο περιέχει πραγματικά ενσωματωμένες εικόνες· ορισμένες “εικόνες” είναι σχέδια VML που δεν εκτίθενται ως εικόνες. |
| **Incorrect image orientation** | Ορισμένες εικόνες DOCX αποθηκεύουν περιστροφή EXIF· επεξεργαστείτε μετά με μια βιβλιοθήκη εικόνας αν χρειάζεται. |

## Συχνές ερωτήσεις

**Q: Ποια μορφότυπα αρχείων υποστηρίζει το GroupDocs.Parser για εξαγωγή εικόνων;**  
A: Διαχειρίζεται DOC, DOCX, PDF, PPT, PPTX και πολλές άλλες μορφές, εκθέτοντας εικόνες μέσω της ίδιας μεθόδου `getImages()`.

**Q: Μπορώ να εξάγω εικόνες από αρχεία Word προστατευμένα με κωδικό;**  
A: Ναι—περάστε τον κωδικό στον κατασκευαστή `Parser`, και η βιβλιοθήκη θα αποκρυπτογραφήσει το έγγραφο πριν την εξαγωγή.

**Q: Υπάρχει τρόπος να εξάγω μόνο συγκεκριμένους τύπους εικόνων (π.χ., μόνο JPEG);**  
A: Αφού ανακτήσετε τα αντικείμενα `PageImageArea`, ελέγξτε το `image.getFormat()` και φιλτράρετε αναλόγως πριν την αποθήκευση.

**Q: Υποστηρίζει η βιβλιοθήκη ασύγχρονη επεξεργασία;**  
A: Αν και το βασικό API είναι συγχρονισμένο, μπορείτε να τυλίξετε τη λογική εξαγωγής σε ξεχωριστό νήμα ή να χρησιμοποιήσετε το `CompletableFuture` της Java για παράλληλη επεξεργασία.

**Q: Χρειάζομαι εμπορική άδεια για χρήση σε παραγωγή;**  
A: Μια δωρεάν δοκιμή είναι επαρκής για αξιολόγηση, αλλά απαιτείται πληρωμένη άδεια για εμπορικές εγκαταστάσεις.

**Τελευταία ενημέρωση:** 2026-08-05  
**Δοκιμάστηκε με:** GroupDocs.Parser 25.5  
**Συγγραφέας:** GroupDocs  

**Πόροι**  
- **Τεκμηρίωση:** [GroupDocs Parser Java Documentation](https://docs.groupdocs.com/parser/java/)  
- **Αναφορά API:** [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)  
- **Λήψη:** [Latest Release](https://releases.groupdocs.com/parser/java/)  
- **GitHub:** [Κώδικας πηγής στο GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- **Δωρεάν υποστήριξη:** [Φόρουμ GroupDocs](https://forum.groupdocs.com/c/parser)  
- **Προσωρινή άδεια:** [Αποκτήστε μια προσωρινή άδεια](https://purchase.groupdocs.com/temporary-license/)

## Σχετικά Μαθήματα

- [Πώς να αποθηκεύσετε εικόνες με το GroupDocs.Parser για Java](/parser/java/image-extraction/extract-images-groupdocs-parser-java/)
- [Πώς να εξάγετε εικόνες από pdf χρησιμοποιώντας το GroupDocs.Parser σε Java: Οδηγός βήμα‑βήμα](/parser/java/image-extraction/extract-images-pdf-groupdocs-parser-java/)
- [Πώς να εξάγετε κείμενο από έγγραφα Word χρησιμοποιώντας το GroupDocs.Parser σε Java](/parser/java/text-extraction/extract-text-word-docs-groupdocs-parser-java/)