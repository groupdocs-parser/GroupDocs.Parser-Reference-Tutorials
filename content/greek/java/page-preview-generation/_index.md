---
date: 2026-09-07
description: Οδηγός βήμα προς βήμα για το πώς να χρησιμοποιήσετε το API προεπισκόπησης
  σελίδων Java για τη δημιουργία προεπισκοπήσεων σελίδων εγγράφων και μικρογραφιών
  με το GroupDocs.Parser, περιλαμβάνοντας παραδείγματα και πόρους.
keywords:
- page preview api java
- document preview generation
- groupdocs.parser java
lastmod: 2026-09-07
og_description: Το API προεπισκόπησης σελίδων Java σας επιτρέπει να δημιουργείτε εικόνες
  προεπισκόπησης για κάθε σελίδα εγγράφου με το GroupDocs.Parser. Αυτό το σεμινάριο
  δείχνει τη ρύθμιση, αποσπάσματα κώδικα και συμβουλές απόδοσης για γρήγορες, αξιόπιστες
  προεπισκοπήσεις.
og_image_alt: Guide showing how to generate page previews using GroupDocs.Parser Java
  API
og_title: Πώς να χρησιμοποιήσετε το API προεπισκόπησης σελίδων Java με το GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-09-07'
  description: Step-by-step guide on how to use the page preview API Java to generate
    document page previews and thumbnails with GroupDocs.Parser, including examples
    and resources.
  headline: How to use the page preview API Java with GroupDocs.Parser
  type: TechArticle
- description: Step-by-step guide on how to use the page preview API Java to generate
    document page previews and thumbnails with GroupDocs.Parser, including examples
    and resources.
  name: How to use the page preview API Java with GroupDocs.Parser
  steps:
  - name: configure preview options
    text: Set the desired image format, width, height, and DPI. These settings control
      the visual quality and file size of the generated preview.
  - name: render each page
    text: Iterate over `document.getPages()` and invoke the preview method. The API
      returns a `java.io.InputStream` that you can write directly to a file or HTTP
      response.
  - name: cache or serve the images
    text: Store the resulting images using a naming convention like `{documentId}_{pageNumber}.png`.
      This enables instant retrieval for subsequent requests without re‑rendering.
  type: HowTo
- questions:
  - answer: Yes. Pass the password to the `loadOptions` when opening the document
      before calling the preview API.
    question: Can I generate previews for password‑protected documents?
  - answer: Store the resulting image files on disk or in a CDN keyed by document
      ID and page number, then reuse them for subsequent requests.
    question: How can I cache generated previews?
  - answer: Absolutely. Wrap the preview call in a background thread or use Java’s
      `CompletableFuture` to avoid blocking the main application thread.
    question: Is it possible to generate previews asynchronously?
  - answer: PNG and JPEG are supported out of the box; you can choose the format in
      the preview options.
    question: What image formats are available for the preview output?
  - answer: No. The API works in read‑only mode and does not modify the source file.
    question: Does preview generation affect the original document?
  type: FAQPage
tags:
- page preview
- groupdocs.parser
- java document processing
- preview generation
- api tutorial
title: Πώς να χρησιμοποιήσετε το API προεπισκόπησης σελίδων Java με το GroupDocs.Parser
type: docs
url: /el/java/page-preview-generation/
weight: 18
---

# Πώς να χρησιμοποιήσετε το API προεπισκόπησης σελίδας Java με το GroupDocs.Parser

Η δημιουργία οπτικών προεπισκοπήσεων των σελίδων εγγράφων είναι απαραίτητη όταν θέλετε να δώσετε στους χρήστες μια γρήγορη ματιά στο περιεχόμενο χωρίς να ανοίξουν ολόκληρο το αρχείο. Με το **page preview API Java**, μπορείτε να μετατρέψετε οποιοδήποτε υποστηριζόμενο έγγραφο σε εικόνες PNG ή JPEG με λίγες μόνο γραμμές κώδικα. Αυτό το tutorial σας καθοδηγεί μέσα από τις βασικές έννοιες, δείχνει πού να βρείτε έτοιμα παραδείγματα και εξηγεί γιατί η δημιουργία προεπισκοπήσεων μπορεί να βελτιώσει δραστικά την εμπειρία χρήστη σε εφαρμογές με πολλά έγγραφα.

## Σύντομες απαντήσεις
- **Τι σημαίνει “δημιουργία προεπισκόπησης”;** Δημιουργία εικόνων (PNG/JPEG) για κάθε σελίδα ενός εγγράφου.  
- **Ποιες μορφές υποστηρίζονται;** PDFs, Word, Excel, PowerPoint, εικόνες και πολλά άλλα μέσω του GroupDocs.Parser.  
- **Χρειάζομαι άδεια;** Μια προσωρινή άδεια λειτουργεί για δοκιμές· απαιτείται πλήρης άδεια για παραγωγή.  
- **Ποιες είναι οι επιδόσεις;** Δημιουργήστε προεπισκοπήσεις κατά απαίτηση ή αποθηκεύστε τις στην cache για να μειώσετε το φορτίο CPU.  
- **Μπορώ να προσαρμόσω το μέγεθος της εικόνας;** Ναι – μπορείτε να καθορίσετε πλάτος, ύψος και DPI στις επιλογές προεπισκόπησης.

## Τι είναι το API προεπισκόπησης σελίδας Java;
Το **page preview API Java** είναι ένα σύνολο μεθόδων στο GroupDocs.Parser που διαβάζει ένα έγγραφο σελίδα‑με‑σελίδα και αποδίδει κάθε σελίδα ως εικόνα. Απομονώνει τις πολυπλοκότητες του χειρισμού PDF, DOCX, XLSX, PPTX και πάνω από 120 άλλων μορφών, παρέχοντας συνεπείς μικρογραφίες για οποιονδήποτε τύπο αρχείου.

## Γιατί να χρησιμοποιήσετε το API προεπισκόπησης σελίδας Java;
Το page preview API Java επιτρέπει στους προγραμματιστές να δημιουργούν γρήγορα μικρογραφίες εικόνας για κάθε σελίδα εγγράφου, βελτιώνοντας την εμπειρία χρήστη, μειώνοντας το εύρος ζώνης και παρέχοντας συνεπή απόδοση σε περισσότερες από 120 μορφές με ελάχιστο κώδικα. Υποστηρίζει επίσης προσαρμοσμένο μέγεθος, ρυθμίσεις DPI και ασύγχρονη επεξεργασία για κλιμακούμενες εφαρμογές.

- **Βελτιωμένη Εμπειρία Χρήστη:** Οι χρήστες βλέπουν μια προεπισκόπηση πριν κατεβάσουν ή ανοίξουν μεγάλα αρχεία, μειώνοντας τον αντιληπτό χρόνο αναμονής έως και 60 %.  
- **Μειωμένο εύρος ζώνης:** Οι μικρογραφίες είναι συνήθως κάτω από 50 KB, σε σύγκριση με αρχεία πηγής πολλαπλών megabytes.  
- **Συνεπής διαμορφώσεων:** Ο ίδιος κώδικας λειτουργεί για πάνω από 120 μορφές εισόδου, εξαλείφοντας την ανάγκη λογικής ειδικής μορφής.  
- **Εύκολη ενσωμάτωση:** Μία κλήση API επιστρέφει ένα `java.awt.image.BufferedImage`, το οποίο μπορείτε να ρέσετε απευθείας σε απάντηση web.

## Προαπαιτούμενα
- Java 8 ή νεότερη εγκατεστημένη.  
- Βιβλιοθήκη GroupDocs.Parser for Java προστέθηκε στο έργο σας (Maven/Gradle).  
- Έγκυρη άδεια GroupDocs.Parser (προσωρινή άδεια για δοκιμές).

## Πώς να δημιουργήσετε προεπισκοπήσεις σελίδων χρησιμοποιώντας το API προεπισκόπησης σελίδας Java;

`Parser.load` είναι μια στατική μέθοδος που ανοίγει ένα αρχείο εγγράφου και επιστρέφει ένα αντικείμενο `Parser` για περαιτέρω λειτουργίες.  
`preview(pageNumber, options)` αποδίδει τη συγκεκριμένη σελίδα ως εικόνα σύμφωνα με τις παρεχόμενες επιλογές προεπισκόπησης.

Φορτώστε το έγγραφό σας με `Parser.load("sample.docx")` και καλέστε `preview(pageNumber, options)` — αυτή η ενιαία κλήση επιστρέφει μια εικόνα για τη ζητούμενη σελίδα. Για επεξεργασία σε παρτίδες, επαναλάβετε τον αριθμό σελίδων και αποθηκεύστε κάθε εικόνα σε cache ή CDN. Η χρήση του API με αυτόν τον τρόπο μειώνει την κατανάλωση μνήμης επειδή κάθε σελίδα αποδίδεται ανεξάρτητα.

### Βήμα 1: διαμόρφωση επιλογών προεπισκόπησης
Ορίστε τη ζητούμενη μορφή εικόνας, πλάτος, ύψος και DPI. Αυτές οι ρυθμίσεις ελέγχουν την οπτική ποιότητα και το μέγεθος αρχείου της παραγόμενης προεπισκόπησης.

### Βήμα 2: απόδοση κάθε σελίδας
Περιηγηθείτε στο `document.getPages()` και καλέστε τη μέθοδο preview. Το API επιστρέφει ένα `java.io.InputStream` που μπορείτε να γράψετε απευθείας σε αρχείο ή σε HTTP response.

### Βήμα 3: αποθήκευση ή παροχή των εικόνων
Αποθηκεύστε τις παραγόμενες εικόνες χρησιμοποιώντας μια σύμβαση ονομασίας όπως `{documentId}_{pageNumber}.png`. Αυτό επιτρέπει άμεση ανάκτηση για επόμενα αιτήματα χωρίς επανασχεδίαση.

## Συχνά προβλήματα και λύσεις
- **Σφάλματα έλλειψης μνήμης σε μεγάλα αρχεία:** Χρησιμοποιήστε λειτουργία streaming ή δημιουργήστε προεπισκοπήσεις για ένα υποσύνολο σελίδων.  
- **Εικόνες χαμηλής ανάλυσης:** Αυξήστε τη ρύθμιση DPI στις επιλογές προεπισκόπησης για να βελτιώσετε την καθαρότητα.  
- **Μη υποστηριζόμενοι τύποι αρχείων:** Επαληθεύστε ότι η μορφή αρχείου αναφέρεται στην τεκμηρίωση των υποστηριζόμενων μορφών του GroupDocs.Parser.

## Συχνές ερωτήσεις

**Q: Μπορώ να δημιουργήσω προεπισκοπήσεις για έγγραφα προστατευμένα με κωδικό;**  
A: Ναι. Περνάτε τον κωδικό στο `loadOptions` όταν ανοίγετε το έγγραφο πριν καλέσετε το API προεπισκόπησης.

**Q: Πώς μπορώ να αποθηκεύσω στην cache τις παραγόμενες προεπισκοπήσεις;**  
A: Αποθηκεύστε τα παραγόμενα αρχεία εικόνας σε δίσκο ή σε CDN με κλειδί το ID του εγγράφου και τον αριθμό σελίδας, και στη συνέχεια επαναχρησιμοποιήστε τα για επόμενα αιτήματα.

**Q: Είναι δυνατόν να δημιουργήσω προεπισκοπήσεις ασύγχρονα;**  
A: Απόλυτα. Τυλίξτε την κλήση preview σε ένα background thread ή χρησιμοποιήστε το `CompletableFuture` της Java για να αποφύγετε το μπλοκάρισμα του κύριου νήματος της εφαρμογής.

**Q: Ποιες μορφές εικόνας είναι διαθέσιμες για την έξοδο προεπισκόπησης;**  
A: Υποστηρίζονται PNG και JPEG από προεπιλογή· μπορείτε να επιλέξετε τη μορφή στις επιλογές προεπισκόπησης.

**Q: Επηρεάζει η δημιουργία προεπισκοπήσεων το αρχικό έγγραφο;**  
A: Όχι. Το API λειτουργεί σε λειτουργία μόνο ανάγνωσης και δεν τροποποιεί το αρχείο προέλευσης.

## Διαθέσιμα μαθήματα

### [Δημιουργία προεπισκοπήσεων σελίδων εγγράφου σε Java χρησιμοποιώντας το GroupDocs.Parser](./generate-document-page-previews-groupdocs-parser-java/)
Μάθετε πώς να δημιουργείτε γρήγορα προεπισκοπήσεις σελίδων εγγράφου με το GroupDocs.Parser για Java, βελτιώνοντας την παραγωγικότητα και την αποδοτικότητα.

### [Δημιουργία προεπισκοπήσεων σελίδων υπολογιστικών φύλλων σε Java με το GroupDocs.Parser](./generate-spreadsheet-previews-groupdocs-parser-java/)
Μάθετε πώς να δημιουργείτε δυναμικές προεπισκοπήσεις σελίδων υπολογιστικών φύλλων χρησιμοποιώντας το GroupDocs.Parser για Java. Αυτό το tutorial καλύπτει τη ρύθμιση, την υλοποίηση και πρακτικές εφαρμογές.

## Πρόσθετοι πόροι

- [Τεκμηρίωση GroupDocs.Parser για Java](https://docs.groupdocs.com/parser/java/)
- [Αναφορά API GroupDocs.Parser για Java](https://reference.groupdocs.com/parser/java/)
- [Λήψη GroupDocs.Parser για Java](https://releases.groupdocs.com/parser/java/)
- [Φόρουμ GroupDocs.Parser](https://forum.groupdocs.com/c/parser)
- [Δωρεάν Υποστήριξη](https://forum.groupdocs.com/)
- [Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)

## Συμπέρασμα
Εκμεταλλευόμενοι το **page preview API Java**, μπορείτε να παρέχετε γρήγορες, υψηλής ποιότητας μικρογραφίες για οποιονδήποτε υποστηριζόμενο τύπο εγγράφου, να βελτιώσετε την ικανοποίηση των χρηστών και να μειώσετε το κόστος του εύρους ζώνης. Ξεκινήστε να ενσωματώνετε το API σήμερα, πειραματιστείτε με τις ρυθμίσεις DPI και μεγέθους, και σκεφτείτε στρατηγικές caching για να κλιμακώσετε αποτελεσματικά την υπηρεσία προεπισκοπήσεων.

---

**Τελευταία ενημέρωση:** 2026-09-07  
**Δοκιμάστηκε με:** GroupDocs.Parser 23.11 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Οδηγός Ανάλυσης Εγγράφων Java Groupdocs Parser](/parser/java/getting-started/document-parsing-java-groupdocs-parser-guide/)
- [Εξαγωγή Κειμένου PDF σε Java με GroupDocs.Parser – Οδηγός βήμα‑βήμα](/parser/java/document-loading/java-groupdocs-parser-load-pdf-document/)
- [Δημιουργία Προεπισκοπήσεων Υπολογιστικών Φύλλων Groupdocs Parser Java](/parser/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/)