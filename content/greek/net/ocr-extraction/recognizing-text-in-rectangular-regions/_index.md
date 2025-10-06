---
title: Αναγνώριση κειμένου σε ορθογώνιες περιοχές
linktitle: Αναγνώριση κειμένου σε ορθογώνιες περιοχές
second_title: GroupDocs.Parser .NET API
description: Μάθετε πώς να αναγνωρίζετε κείμενο σε συγκεκριμένες περιοχές εγγράφων χρησιμοποιώντας το GroupDocs.Parser για .NET με δυνατότητες OCR.
weight: 14
url: /el/net/ocr-extraction/recognizing-text-in-rectangular-regions/
type: docs
---
# Αναγνώριση κειμένου σε ορθογώνιες περιοχές

## Εισαγωγή
Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να χρησιμοποιήσετε το GroupDocs.Parser για .NET για την αναγνώριση κειμένου σε συγκεκριμένες ορθογώνιες περιοχές εγγράφων. Το GroupDocs.Parser είναι μια ισχυρή βιβλιοθήκη που επιτρέπει στους προγραμματιστές να εξάγουν κείμενο, μεταδεδομένα και άλλα από διάφορες μορφές αρχείων, όπως PDF, Word, Excel και PowerPoint.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε ρυθμίσει τις ακόλουθες ρυθμίσεις:
-  GroupDocs.Parser για .NET: Λήψη και εγκατάσταση της βιβλιοθήκης από[εδώ](https://releases.groupdocs.com/parser/net/).
- Περιβάλλον ανάπτυξης: Visual Studio ή οποιοδήποτε άλλο .NET IDE.
- Δείγμα εγγράφου: Έχετε ένα δείγμα αρχείου (π.χ. PDF, DOCX) που περιέχει κείμενο προς αναγνώριση.

## Εισαγωγή χώρων ονομάτων
Αρχικά, θα χρειαστεί να εισαγάγετε τους απαραίτητους χώρους ονομάτων στον κώδικα C#:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Βήμα 1: Αρχικοποίηση ρυθμίσεων ανάλυσης
 Ξεκινήστε με τη ρύθμιση του`ParserSettings` με την υποδοχή OCR. Εδώ, θα χρησιμοποιήσουμε την εσωτερική σύνδεση Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Βήμα 2: Δημιουργία παρουσίας Parser
 Στη συνέχεια, δημιουργήστε το`Parser` τάξη με τις προηγουμένως καθορισμένες ρυθμίσεις:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Ο κώδικας συνεχίζεται εδώ
}
```
 Αντικαθιστώ`"YourSampleFile.pdf"` με τη διαδρομή προς το έγγραφό σας.
## Βήμα 3: Ορίστε το ορθογώνιο OCR
 Ορίστε ένα ορθογώνιο εντός του εγγράφου όπου θα εκτελεστεί η αναγνώριση κειμένου. Για παράδειγμα, ένα ορθογώνιο που ξεκινά από`(0, 0)` με πλάτος`400` και ύψος`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Βήμα 4: Διαμόρφωση επιλογών αναγνώρισης κειμένου
 Δημιουργώ`TextOptions` για να καθορίσετε τη χρήση OCR μαζί με το καθορισμένο ορθογώνιο:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Βήμα 5: Εξαγωγή κειμένου χρησιμοποιώντας OCR
 Χρησιμοποιήστε το`GetText` μέθοδος του`Parser` παράδειγμα με το ρυθμισμένο`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Διαβάστε το εξαγόμενο κείμενο ή χειριστείτε την περίπτωση "δεν υποστηρίζεται".
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## συμπέρασμα
Σε αυτό το σεμινάριο, δείξαμε πώς να αξιοποιήσετε το GroupDocs.Parser για .NET για την εξαγωγή κειμένου από συγκεκριμένες ορθογώνιες περιοχές σε έγγραφα χρησιμοποιώντας OCR. Αυτή η διαδικασία μπορεί να προσαρμοστεί περαιτέρω και να ενσωματωθεί σε διάφορες εφαρμογές για αυτοματοποιημένες εργασίες εξαγωγής κειμένου.

## Συχνές ερωτήσεις
### Μπορεί το GroupDocs.Parser να εξάγει κείμενο από σαρωμένα έγγραφα;
Ναι, το GroupDocs.Parser υποστηρίζει OCR (Optical Character Recognition) για εξαγωγή κειμένου από σαρωμένα έγγραφα.
### Ποιες μορφές αρχείων υποστηρίζει το GroupDocs.Parser;
Το GroupDocs.Parser υποστηρίζει ένα ευρύ φάσμα μορφών αρχείων, συμπεριλαμβανομένων των PDF, DOCX, XLSX, PPTX και άλλων.
### Πώς μπορώ να χειριστώ έγγραφα που δεν υποστηρίζονται για εξαγωγή κειμένου;
 Μπορείτε να ελέγξετε εάν η εξαγωγή κειμένου υποστηρίζεται χρησιμοποιώντας`TextReader` παράδειγμα που επιστράφηκε από`parser.GetText(options)`.
### Είναι το GroupDocs.Parser κατάλληλο για εργασίες εξαγωγής κειμένου μεγάλης κλίμακας;
Ναι, το GroupDocs.Parser έχει σχεδιαστεί για να χειρίζεται αποτελεσματικά εργασίες εξαγωγής κειμένου μεγάλης κλίμακας.
### Πού μπορώ να λάβω υποστήριξη για ζητήματα που σχετίζονται με το GroupDocs.Parser;
 Για υποστήριξη και συζητήσεις, επισκεφθείτε το[GroupDocs.Parser φόρουμ](https://forum.groupdocs.com/c/parser/17).