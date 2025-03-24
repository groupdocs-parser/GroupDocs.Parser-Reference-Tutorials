---
title: Εξαγωγή μορφοποιημένου κειμένου από τη σελίδα εγγράφου
linktitle: Εξαγωγή μορφοποιημένου κειμένου από τη σελίδα εγγράφου
second_title: GroupDocs.Parser .NET API
description: Εξαγωγή μορφοποιημένου κειμένου από σελίδες εγγράφων χρησιμοποιώντας το GroupDocs.Parser για .NET. Αποτελεσματική και αξιόπιστη λύση εξαγωγής κειμένου.
weight: 11
url: /el/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---

# Εξαγωγή μορφοποιημένου κειμένου από τη σελίδα εγγράφου

## Εισαγωγή
Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία εξαγωγής μορφοποιημένου κειμένου από σελίδες εγγράφων χρησιμοποιώντας το GroupDocs.Parser για .NET. Αυτή η βιβλιοθήκη σάς επιτρέπει να αναλύετε αποτελεσματικά και να εξάγετε κείμενο από διάφορες μορφές εγγράφων όπως PDF, Word, Excel και άλλα.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
- Το Visual Studio είναι εγκατεστημένο στο σύστημά σας.
- Βασικές γνώσεις προγραμματισμού C#.
-  GroupDocs.Parser για τη βιβλιοθήκη .NET. Μπορείτε να το κατεβάσετε[εδώ](https://releases.groupdocs.com/parser/net/).

## Εισαγωγή χώρων ονομάτων
Αρχικά, ξεκινήστε εισάγοντας τους απαραίτητους χώρους ονομάτων στο έργο σας C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Βήμα 1: Δημιουργήστε μια παρουσία κλάσης Parser
 Ξεκινήστε δημιουργώντας ένα παράδειγμα του`Parser` τάξη παρέχοντας τη διαδρομή προς το δείγμα αρχείου σας.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ο κωδικός θα πάει εδώ
}
```
## Βήμα 2: Ελέγξτε εάν υποστηρίζεται η εξαγωγή μορφοποιημένου κειμένου
Πριν προχωρήσετε στην εξαγωγή κειμένου, επαληθεύστε εάν το έγγραφο υποστηρίζει την εξαγωγή μορφοποιημένου κειμένου.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Βήμα 3: Λήψη πληροφοριών εγγράφου
Ανακτήστε πληροφορίες σχετικά με το έγγραφο, όπως τον αριθμό των σελίδων.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Βήμα 4: Επανάληψη σελίδων σε έγγραφο και εξαγωγή μορφοποιημένου κειμένου
Επαναλάβετε σε κάθε σελίδα του εγγράφου και εξαγάγετε μορφοποιημένο κείμενο χρησιμοποιώντας καθορισμένες επιλογές (π.χ. μορφή Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## συμπέρασμα
Τώρα ξέρετε πώς να εξαγάγετε μορφοποιημένο κείμενο από σελίδες εγγράφων χρησιμοποιώντας το GroupDocs.Parser για .NET. Αυτή η βιβλιοθήκη παρέχει μια ισχυρή και εύχρηστη λύση για εξαγωγή κειμένου από διάφορες μορφές αρχείων.

## Συχνές ερωτήσεις
### Μπορεί το GroupDocs.Parser να χειριστεί διαφορετικές μορφές αρχείων;
Ναι, το GroupDocs.Parser υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των PDF, DOCX, XLSX, PPTX και άλλων.
### Είναι το GroupDocs.Parser συμβατό με .NET Core;
Ναι, το GroupDocs.Parser υποστηρίζει .NET Core και .NET Framework.
### Διατηρεί το GroupDocs.Parser τη μορφοποίηση κειμένου κατά την εξαγωγή;
Ναι, το GroupDocs.Parser μπορεί να διατηρήσει τη μορφοποίηση, όπως στυλ και γραμματοσειρές κατά την εξαγωγή κειμένου.
### Μπορώ να εξαγάγω εικόνες και μεταδεδομένα χρησιμοποιώντας το GroupDocs.Parser;
Ναι, το GroupDocs.Parser επιτρέπει την εξαγωγή εικόνων, μεταδεδομένων και κειμένου από έγγραφα.
### Πώς μπορώ να λάβω υποστήριξη για το GroupDocs.Parser;
 Μπορείτε να λάβετε υποστήριξη από το[GroupDocs.Parser φόρουμ](https://forum.groupdocs.com/c/parser/17).