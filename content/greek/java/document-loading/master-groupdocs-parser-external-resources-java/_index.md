---
date: '2026-06-22'
description: Κατακτήστε την ανάλυση εγγράφων Java εξάγοντας εικόνες και μειώνοντας
  τη χρήση μνήμης με το GroupDocs.Parser. Μάθετε custom handlers, resource filtering,
  και performance tips.
keywords:
- java document parsing
- reduce memory usage
- load external resources
- skip unwanted images
- extract pictures docx
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Master java document parsing by extracting images and reducing memory
    usage with GroupDocs.Parser. Learn custom handlers, resource filtering, and performance
    tips.
  headline: 'Java Document Parsing: Extract Images from Documents with GroupDocs.Parser'
  type: TechArticle
- description: Master java document parsing by extracting images and reducing memory
    usage with GroupDocs.Parser. Learn custom handlers, resource filtering, and performance
    tips.
  name: 'Java Document Parsing: Extract Images from Documents with GroupDocs.Parser'
  steps:
  - name: Create a custom handler
    text: '`ExternalResourceHandler` is an interface that lets you decide whether
      a specific external resource—such as an image—should be loaded. Implement the
      `onLoading` method and return `true` for resources you want to keep, `false`
      to skip them. The `onLoading` method receives the resource metadata and sh'
  - name: Configure `ParserSettings` with the handler
    text: '`ParserSettings` is a configuration class that holds options like custom
      handlers, detection settings, and performance tweaks for the parser. Pass your
      handler instance to `ParserSettings` before opening a document.'
  - name: Fine‑tune the filtering logic
    text: If you need more sophisticated rules—such as filtering by image size, format,
      or URI pattern—extend the `onLoading` method accordingly. For example, you can
      skip any image larger than 2 MB or ignore all PNG files.
  type: HowTo
- questions:
  - answer: It lets you control which external resources are loaded, enhancing security
      and performance by filtering out unnecessary files.
    question: What is the primary purpose of using a custom `ExternalResourceHandler`?
  - answer: Yes, a free trial is available, but advanced features and large‑scale
      deployments require a valid license.
    question: Can I use GroupDocs.Parser for Java without a license?
  - answer: Wrap parsing calls in try‑catch blocks for `IOException` and other specific
      exceptions to gracefully handle errors.
    question: How do I handle exceptions during parsing with GroupDocs.Parser?
  - answer: Incorrect URI checks can skip needed files; use logging or breakpoints
      to verify your conditions.
    question: What are common pitfalls when filtering resources?
  - answer: Absolutely—GroupDocs.Parser supports PDFs, Word, Excel, PowerPoint, and
      many other formats.
    question: Is it possible to parse non‑HTML documents using GroupDocs.Parser for
      Java?
  type: FAQPage
title: 'Ανάλυση Εγγράφων Java: Εξαγωγή Εικόνων από Έγγραφα με GroupDocs.Parser'
type: docs
url: /el/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Ανάλυση Εγγράφων Java: Εξαγωγή Εικόνων από Έγγραφα με το GroupDocs.Parser

Σε αυτόν τον ολοκληρωμένο οδηγό θα μάθετε **java document parsing** τεχνικές για την εξαγωγή εικόνων από μια ποικιλία τύπων αρχείων χρησιμοποιώντας το GroupDocs.Parser για Java. Θα περάσουμε από τη ρύθμιση της βιβλιοθήκης, τη δημιουργία ενός προσαρμοσμένου `ExternalResourceHandler`, και την εφαρμογή έξυπνου φιλτραρίσματος ώστε να φορτώνετε μόνο τους πόρους που πραγματικά χρειάζεστε—σας βοηθά να **μειώσετε τη χρήση μνήμης** και να επιταχύνετε την επεξεργασία.

## Γρήγορες Απαντήσεις
- **Τι κάνει το GroupDocs.Parser;** Αναλύει πάνω από 50 μορφές αρχείων, εκθέτοντας κείμενο, εικόνες και άλλους ενσωματωμένους πόρους για προγραμματιστική χρήση.  
- **Μπορώ να παραλείψω ανεπιθύμητες εικόνες;** Ναι—εφαρμόστε ένα προσαρμοσμένο `ExternalResourceHandler` για φιλτράρισμα των πόρων σε πραγματικό χρόνο.  
- **Ποια έκδοση Maven απαιτείται;** Χρησιμοποιήστε το GroupDocs.Parser Java 25.5 ή νεότερο.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται μόνιμη άδεια για παραγωγή.  
- **Είναι αυτή η προσέγγιση thread‑safe;** Δημιουργήστε ένα ξεχωριστό αντικείμενο `Parser` ανά νήμα· τα αντικείμενα δεν μοιράζονται.

## Τι σημαίνει “εξαγωγή εικόνων από έγγραφα”;
Η εξαγωγή εικόνων από έγγραφα σημαίνει την προγραμματιστική ανάκτηση ενσωματωμένων αρχείων εικόνας ώστε να μπορείτε να τα αποθηκεύσετε, να τα εμφανίσετε ή να τα επεξεργαστείτε περαιτέρω εκτός του αρχικού αρχείου. Αυτή η λειτουργία είναι απαραίτητη όταν χρειάζεστε μικρογραφίες, οπτικοποίηση δεδομένων ή να επαναχρησιμοποιήσετε μέσα πολυμέσων χωρίς να διατηρείτε ολόκληρο το πηγαίο έγγραφο.

## Γιατί να φιλτράρετε τους πόρους κατά την εξαγωγή εικόνων;
Το φιλτράρισμα των πόρων κατά την εξαγωγή εικόνων σας επιτρέπει να **μειώσετε τη χρήση μνήμης έως και 70 %** κατά την επεξεργασία μεγάλων αρχείων, επειδή τα ανεπιθύμητα δυαδικά δεδομένα δεν εισέρχονται ποτέ στη μνήμη heap της JVM. Επίσης βελτιώνει την ασφάλεια αποτρέποντας τη φόρτωση πιθανώς μη ασφαλούς περιεχομένου, και επιταχύνει τη διαδικασία—μεγάλα συμβόλαια με εκατοντάδες διακοσμητικά γραφικά μπορούν να αναλυθούν σε ένα κλάσμα του αρχικού χρόνου.

## Προαπαιτούμενα

- **Java Development Kit (JDK)** – έκδοση 8 ή νεότερη.  
- **Maven** – για διαχείριση εξαρτήσεων.  
- Βασική εξοικείωση με Java I/O και διαχείριση εξαιρέσεων.

## Ρύθμιση του GroupDocs.Parser για Java

Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση parser στο `pom.xml`:

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

Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Απόκτηση Άδειας
- **Free Trial** – εξερευνήστε τις βασικές λειτουργίες χωρίς κόστος.  
- **Temporary License** – ξεκλειδώστε τη πλήρη λειτουργικότητα κατά την αξιολόγηση.  
- **Purchased License** – απαιτείται για εμπορική ανάπτυξη.

## Πώς να φιλτράρετε τους πόρους κατά την εξαγωγή εικόνων
Για να φιλτράρετε τους πόρους, υλοποιήστε ένα `ExternalResourceHandler` που αποφασίζει ποια ενσωματωμένα αρχεία θα φορτωθούν. Καταχωρήστε αυτόν τον χειριστή στο `ParserSettings` πριν ανοίξετε το έγγραφο, στη συνέχεια καλέστε τον parser. Ο χειριστής λαμβάνει τα μεταδεδομένα κάθε πόρου, επιτρέποντάς σας να το αποδεχτείτε ή να το απορρίψετε βάσει κριτηρίων όπως τύπος, μέγεθος ή όνομα, διασφαλίζοντας ότι επεξεργάζονται μόνο οι απαραίτητες εικόνες.

### Βήμα 1: Δημιουργία προσαρμοσμένου χειριστή
`ExternalResourceHandler` είναι μια διεπαφή που σας επιτρέπει να αποφασίσετε αν ένας συγκεκριμένος εξωτερικός πόρος—όπως μια εικόνα—πρέπει να φορτωθεί. Υλοποιήστε τη μέθοδο `onLoading` και επιστρέψτε `true` για πόρους που θέλετε να διατηρήσετε, `false` για να τους παραλείψετε. Η μέθοδος `onLoading` λαμβάνει τα μεταδεδομένα του πόρου και πρέπει να επιστρέφει `true` για φόρτωση ή `false` για παράλειψη.

```java
import com.groupdocs.parser.options.ExternalResourceHandler;
import com.groupdocs.parser.data.ExternalResourceLoadingArgs;

class Handler extends ExternalResourceHandler {
    @Override
    public void onLoading(ExternalResourceLoadingArgs args) {
        if (!args.getUri().endsWith("installation.png")) {
            args.setSkipped(true);
        }
        super.onLoading(args);
    }
}
```

### Βήμα 2: Διαμόρφωση του `ParserSettings` με τον χειριστή
`ParserSettings` είναι μια κλάση διαμόρφωσης που περιέχει επιλογές όπως προσαρμοσμένοι χειριστές, ρυθμίσεις ανίχνευσης και βελτιώσεις απόδοσης για τον parser. Περάστε το στιγμιότυπο του χειριστή σας στο `ParserSettings` πριν ανοίξετε ένα έγγραφο.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.IOException;
import com.groupdocs.parser.options.ParserSettings;

public class LoadExternalResources {
    public static void run() throws IOException {
        ParserSettings settings = new ParserSettings(new Handler());
        
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
            Iterable<PageImageArea> images = parser.getImages();
            
            for (PageImageArea image : images) {
                System.out.println(image.getFileType());
            }
        }
    }
}
```

### Βήμα 3: Λεπτομερής ρύθμιση της λογικής φιλτραρίσματος
Αν χρειάζεστε πιο σύνθετους κανόνες—όπως φιλτράρισμα κατά μέγεθος εικόνας, μορφή ή μοτίβο URI—επεκτείνετε τη μέθοδο `onLoading` αναλόγως. Για παράδειγμα, μπορείτε να παραλείψετε οποιαδήποτε εικόνα μεγαλύτερη από 2 MB ή να αγνοήσετε όλα τα αρχεία PNG.

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Πρακτικές Εφαρμογές

1. **Document Management Systems** – Ανάκτηση μόνο των απαραίτητων εικόνων από σαρωμένα συμβόλαια για δημιουργία μικρογραφιών.  
2. **Data Extraction Services** – Παράλειψη διακοσμητικών γραφικών και εστίαση σε διαγράμματα που περιέχουν πολύτιμα δεδομένα.  
3. **Web Scraping Tools** – Φιλτράρισμα των tracking pixels κατά την ανάκτηση σημαντικών μέσων από έγγραφα βασισμένα σε HTML.

## Σκέψεις Απόδοσης
Ο Parser είναι η βασική κλάση που ανοίγει ένα έγγραφο και παρέχει πρόσβαση στο περιεχόμενό του.  
- **Φιλτράρισμα νωρίς**: Εφαρμόστε τον προσαρμοσμένο χειριστή σας πριν την επανάληψη στους πόρους για να αποφύγετε τη φόρτωση ανεπιθύμητων δεδομένων στη μνήμη.  
- **Άμεση απελευθέρωση**: Χρησιμοποιήστε try‑with‑resources (`try (Parser parser = …)`) για να ελευθερώσετε τους εγγενείς πόρους.  
- **Ασύγχρονη επεξεργασία**: Για μεγάλες παρτίδες, επεξεργαστείτε έγγραφα σε parallel streams διατηρώντας κάθε αντικείμενο `Parser` περιορισμένο σε ένα νήμα.

## Κοινά Προβλήματα & Λύσεις
| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|-------|----------------|-----|
| Δεν επιστράφηκαν εικόνες | Ο χειριστής παραλείπει όλους τους πόρους κατά λάθος | Επαληθεύστε τη συνθήκη `if` και βεβαιωθείτε ότι το `args.setSkipped(true)` καλείται μόνο για ανεπιθύμητα URIs. |
| `IOException` σε μεγάλα αρχεία | Ανεπαρκής μνήμη heap | Αυξήστε τη μνήμη heap της JVM (`-Xmx2g`) ή επεξεργαστείτε τις σελίδες σε μικρότερα τμήματα. |
| Η άδεια δεν αναγνωρίζεται | Χρήση δοκιμαστικού DLL σε κώδικα παραγωγής | Εφαρμόστε τη σωστή διαδρομή αρχείου άδειας μέσω `License.setLicense("path/to/license")`. |

## Συχνές Ερωτήσεις

**Q: Ποιος είναι ο κύριος σκοπός της χρήσης ενός προσαρμοσμένου `ExternalResourceHandler`;**  
A: Σας επιτρέπει να ελέγχετε ποιοι εξωτερικοί πόροι φορτώνονται, ενισχύοντας την ασφάλεια και την απόδοση φιλτράροντας τα περιττά αρχεία.

**Q: Μπορώ να χρησιμοποιήσω το GroupDocs.Parser για Java χωρίς άδεια;**  
A: Ναι, υπάρχει δωρεάν δοκιμή, αλλά οι προηγμένες λειτουργίες και οι μεγάλες αναπτύξεις απαιτούν έγκυρη άδεια.

**Q: Πώς να διαχειριστώ εξαιρέσεις κατά την ανάλυση με το GroupDocs.Parser;**  
A: Τυλίξτε τις κλήσεις ανάλυσης σε μπλοκ try‑catch για `IOException` και άλλες συγκεκριμένες εξαιρέσεις ώστε να διαχειρίζεστε τα σφάλματα με χάρη.

**Q: Ποια είναι τα κοινά προβλήματα κατά το φιλτράρισμα των πόρων;**  
A: Λανθασμένοι έλεγχοι URI μπορεί να παραλείψουν απαραίτητα αρχεία· χρησιμοποιήστε logging ή breakpoints για να επαληθεύσετε τις συνθήκες σας.

**Q: Είναι δυνατόν να αναλύσετε μη‑HTML έγγραφα χρησιμοποιώντας το GroupDocs.Parser για Java;**  
A: Απόλυτα—το GroupDocs.Parser υποστηρίζει PDFs, Word, Excel, PowerPoint και πολλές άλλες μορφές.

## Επόμενα Βήματα
Εξερευνήστε την πλήρη [API Reference](https://reference.groupdocs.com/parser/java) για πρόσθετες ρυθμίσεις όπως `ParserSettings.setDetectTables(true)` για εξαγωγή πινάκων, ή πειραματιστείτε με `ParserSettings.setExtractEmbeddedFonts(true)` για εξαγωγή γραμματοσειρών.

---

**Τελευταία Ενημέρωση:** 2026-06-22  
**Δοκιμάστηκε Με:** GroupDocs.Parser 25.5 for Java  
**Συγγραφέας:** GroupDocs  

**Πόροι**  
- **Documentation:** [Τεκμηρίωση GroupDocs.Parser](https://docs.groupdocs.com/parser/java/)  
- **API Reference:** [Λεπτομέρειες API](https://reference.groupdocs.com/parser/java)  
- **Downloads:** [Τελευταίες Εκδόσεις](https://releases.groupdocs.com/parser/java/)

## Σχετικά Μαθήματα

- [Μαθήματα Φόρτωσης Εγγράφων για GroupDocs.Parser Java](/parser/java/document-loading/)
- [εξαγωγή εικόνων pdf με GroupDocs.Parser Java – Μαθήματα](/parser/java/image-extraction/)
- [Πώς να εξάγετε εικόνες από pdf χρησιμοποιώντας το GroupDocs.Parser σε Java: Οδηγός βήμα‑βήμα](/parser/java/image-extraction/extract-images-pdf-groupdocs-parser-java/)