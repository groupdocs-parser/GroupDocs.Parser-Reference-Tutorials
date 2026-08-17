---
date: '2026-07-16'
description: Μάθετε πώς να δημιουργήσετε μικρογραφία λογιστικού φύλλου Java με GroupDocs.Parser,
  να προεπισκοπήσετε Excel χωρίς Office και να αποδώσετε φύλλα Excel ως εικόνες. Αυτός
  ο οδηγός καλύπτει τη ρύθμιση, την υλοποίηση και πρακτικές περιπτώσεις χρήσης.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: Δημιουργήστε μικρογραφία λογιστικού φύλλου Java με GroupDocs.Parser—προεπισκοπήστε
  Excel χωρίς Office και αποδώστε φύλλα Excel ως εικόνες. Ακολουθήστε αυτόν τον βήμα‑βήμα
  οδηγό για να δημιουργήσετε προεπισκοπήσεις PNG αποδοτικά.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: Δημιουργία μικρογραφίας λογιστικού φύλλου Java με χρήση GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: Δημιουργία μικρογραφίας λογιστικού φύλλου Java με χρήση GroupDocs.Parser
type: docs
url: /el/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Δημιουργία μικρογραφίας λογιστικού φύλλου Java χρησιμοποιώντας το GroupDocs.Parser

Αν ψάχνετε να **δημιουργήσετε μικρογραφία λογιστικού φύλλου Java**, βρίσκεστε στο σωστό μέρος. Σε αυτόν τον οδηγό θα σας δείξουμε πώς να δημιουργήσετε προεπισκοπήσεις PNG υψηλής ποιότητας από βιβλία εργασίας `.xlsx` χρησιμοποιώντας το GroupDocs.Parser για Java — ιδανικό για γρήγορες μικρογραφίες, κοινή χρήση στιγμιότυπων ή δημιουργία λειτουργίας προεπισκόπησης εγγράφων στην εφαρμογή σας. Η λύση λειτουργεί χωρίς εγκατάσταση Microsoft Office και κλιμακώνεται σε μεγάλα βιβλία εργασίας διατηρώντας χαμηλή χρήση μνήμης.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “preview Excel”;** Δημιουργία αρχείων εικόνας (π.χ., PNG) που αντιπροσωπεύουν κάθε σελίδα φύλλου εργασίας.  
- **Ποια μορφή συνιστάται;** Το PNG παρέχει ποιότητα χωρίς απώλειες και λειτουργεί καλά για μικρογραφίες στο web.  
- **Χρειάζομαι άδεια;** Η δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται εμπορική άδεια για παραγωγή.  
- **Μπορώ να αλλάξω την ανάλυση της εικόνας;** Ναι — ρυθμίστε το DPI στο `PreviewOptions`.  
- **Είναι δυνατόν να προεπισκοπήσετε άλλες μορφές;** Το GroupDocs.Parser υποστηρίζει επίσης PDF, Word και πολλούς τύπους εικόνων.

## Τι σημαίνει “πώς να προεπισκοπήσετε το Excel” με το GroupDocs.Parser;

Φορτώστε το βιβλίο εργασίας Excel και αποδώστε κάθε φύλλο ως εικόνα PNG χωρίς να χρειάζεται Microsoft Office. Το GroupDocs.Parser μεταδίδει τις σελίδες μία‑μια, παράγοντας μικρογραφίες χωρίς απώλειες που μπορούν να αποθηκευτούν στο δίσκο ή να επιστραφούν μέσω HTTP, καθιστώντας το ιδανικό για υπηρεσίες προεπισκόπησης στο web.

Το GroupDocs.Parser διαβάζει βιβλία εργασίας Excel, αποδίδει κάθε φύλλο ως οπτική σελίδα και σας επιτρέπει να μεταδώσετε αυτές τις σελίδες σε αρχεία εικόνας. Αυτό εξαλείφει την ανάγκη για διασύνδεση με το Office ή τρίτους μετατροπείς.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Parser για προεπισκοπήσεις Excel;

Θα πρέπει να χρησιμοποιήσετε το GroupDocs.Parser επειδή λειτουργεί σε οποιονδήποτε διακομιστή Java, δεν απαιτεί εγκατάσταση Office, διαχειρίζεται μεγάλα βιβλία εργασίας με χαμηλή μνήμη και παράγει εικόνες PNG χωρίς απώλειες με ρυθμιζόμενο DPI. Το SDK υποστηρίζει **100+ input and output formats**, μπορεί να επεξεργαστεί ένα βιβλίο εργασίας 200 σελίδων σε λιγότερο από 3 δευτερόλεπτα και διατηρεί τη χρήση μνήμης κάτω από 50 MB ανά φύλλο.

- **Δεν απαιτείται εγκατάσταση Office** – λειτουργεί σε οποιοδήποτε περιβάλλον Java στο διακομιστή.  
- **Υποστηρίζει μεγάλα αρχεία** – μεταδίδει σελίδες μία‑μία, διατηρώντας τη χρήση μνήμης χαμηλή.  
- **Έξοδος υψηλής ποιότητας** – έλεγχος DPI, μορφής και επιλογών απόδοσης.  
- **Ευελιξία μεταξύ μορφών** – το ίδιο API λειτουργεί για PDF, έγγραφα Word και άλλα.

## Προαπαιτούμενα
- **Java Development Kit** (8 +).  
- **IDE** όπως IntelliJ IDEA ή Eclipse.  
- **GroupDocs.Parser for Java SDK** – κατεβάστε από [here](https://releases.groupdocs.com/parser/java/).  
- **Documentation** – δείτε την επίσημη [documentation](https://docs.groupdocs.com/parser/java/).  
- **Δείγμα αρχείου Excel** (`.xlsx`) που θέλετε να προεπισκοπήσετε.  
- **Maven ή Gradle** (προαιρετικό) για διαχείριση εξαρτήσεων.

## Εισαγωγή Πακέτων
These imports give you access to the parser, preview options, and stream handling utilities.

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

## Οδηγός βήμα‑βήμα για τη δημιουργία προεπισκοπήσεων σελίδων λογιστικού φύλλου

### Βήμα 1: Αρχικοποίηση του αντικειμένου Parser
`Parser` is GroupDocs.Parser's core class that provides read access to spreadsheet files and enables page‑wise rendering.  
Create a `Parser` object pointing at your Excel workbook. The *try‑with‑resources* block ensures the parser is closed automatically.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Pro tip:** Χρησιμοποιήστε απόλυτη διαδρομή ή διαμορφώστε φάκελο πόρων για να αποφύγετε το `FileNotFoundException`.

### Βήμα 2: Προετοιμασία των επιλογών προεπισκόπησης
`PreviewOptions` configures rendering parameters such as output format and DPI.  
`ICreatePageStream` is a callback interface that supplies an output stream for each generated page. Define how each page will be saved. The `ICreatePageStream` implementation returns a fresh `FileOutputStream` for every worksheet page.

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

### Βήμα 3: Προσθήκη αντιπροσώπου για σύλληψη πληροφοριών απόδοσης
If you need details about each rendered sheet (e.g., dimensions, sheet name), register a callback.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Βήμα 4: Καθορισμός μορφής εξόδου και DPI
Select PNG as the image format and set a DPI that balances quality and file size.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Ρυθμίστε το DPI αν χρειάζεστε μικρότερες μικρογραφίες (π.χ., 96) ή εκτυπώσεις υψηλής ανάλυσης (π.χ., 300).

### Βήμα 5: Δημιουργία των προεπισκοπήσεων
With everything configured, call `generatePreview`. The SDK will iterate over each worksheet and invoke the stream you supplied.

```java
parser.generatePreview(previewOptions);
```

### Βήμα 6: Ορισμός της βοηθητικής μεθόδου `getOutputPath()`
`getOutputPath()` builds a file name based on the page (sheet) number and returns the full path for the output image. Feel free to customize the folder structure.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Συνηθισμένο λάθος:** Η παράλειψη δημιουργίας του καταλόγου `output` εκ των προτέρων θα προκαλέσει `IOException`. Δημιουργήστε το προγραμματιστικά ή βεβαιωθείτε ότι υπάρχει.

## Πλήρες λειτουργικό παράδειγμα (απλοποιημένο)

Below is a compact version that ties all the pieces together. It demonstrates the **δημιουργία μικρογραφίας λογιστικού φύλλου Java** workflow from start to finish.

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

Run this snippet, and you’ll find a series of `preview_page_1.png`, `preview_page_2.png`, … files in the `output` folder—each representing a sheet from the original Excel workbook.

## Συχνά Προβλήματα & Λύσεις
| Issue | Cause | Fix |
|-------|-------|-----|
| **No images generated** | `getOutputPath` returns an invalid directory | Ensure the target folder exists or create it with `new File("output").mkdirs();` |
| **Out‑of‑memory error on huge files** | Loading the whole workbook at once | Use the streaming approach (as shown) and process pages one at a time |
| **Incorrect DPI** | `setDpi` not called or set to default (96) | Call `previewOptions.setDpi(yourDesiredValue);` before `generatePreview` |
| **Unsupported format** | Trying to preview a corrupted `.xlsx` | Validate the file with Excel or use `Parser.isSupported` before processing |

## Συχνές Ερωτήσεις

**Q: Μπορώ να δημιουργήσω προεπισκοπήσεις για PDF και εικόνες χρησιμοποιώντας το GroupDocs.Parser;**  
A: Ναι, το ίδιο API λειτουργεί για PDF, έγγραφα Word και πολλά μορφές εικόνων.

**Q: Πώς αλλάζω τη μορφή εξόδου της εικόνας;**  
A: Καλείτε `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (ή `Gif`, `Bmp`, κλπ.).

**Q: Είναι η απόδοση πρόβλημα με πολύ μεγάλα βιβλία εργασίας;**  
A: Το SDK μεταδίδει σελίδες, διατηρώντας τη χρήση μνήμης χαμηλή. Για τεράστια αρχεία, σκεφτείτε επεξεργασία σε παράλληλες παρτίδες.

**Q: Πώς μπορώ να διαχειριστώ σφάλματα κατά τη δημιουργία προεπισκοπήσεων;**  
A: Τυλίξτε τον κώδικα σε μπλοκ try‑catch (όπως φαίνεται) και καταγράψτε τις λεπτομέρειες της εξαίρεσης. Βεβαιωθείτε ότι οι ροές κλείνουν στο block `finally` αν δεν χρησιμοποιείτε try‑with‑resources.

**Q: Η βιβλιοθήκη απαιτεί εγκατάσταση Microsoft Office;**  
A: Όχι. Το GroupDocs.Parser είναι μια καθαρά Java λύση και λειτουργεί σε οποιαδήποτε πλατφόρμα υποστηρίζει Java 8+.

---

**Τελευταία ενημέρωση:** 2026-07-16  
**Δοκιμάστηκε με:** GroupDocs.Parser 23.11 (latest at time of writing)  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πώς να δημιουργήσετε προεπισκόπηση – Μαθήματα δημιουργίας προεπισκόπησης σελίδων εγγράφου για GroupDocs.Parser Java](/parser/java/page-preview-generation/)
- [Ανάλυση Excel Java με GroupDocs.Parser: Πλήρης Οδηγός](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [Πώς να εξάγετε ακατέργαστο κείμενο από φύλλα Excel χρησιμοποιώντας GroupDocs.Parser για Java: Οδηγός βήμα‑βήμα](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)