---
title: Εξαγωγή κειμένου από τη σελίδα σε ακατέργαστη λειτουργία
linktitle: Εξαγωγή κειμένου από τη σελίδα σε ακατέργαστη λειτουργία
second_title: GroupDocs.Parser .NET API
description: Μάθετε αποτελεσματική εξαγωγή κειμένου από σελίδες εγγράφων χρησιμοποιώντας το Groupdocs.Parser για .NET σε αυτό το περιεκτικό σεμινάριο.
weight: 17
url: /el/net/text-extraction/extract-text-from-page-in-raw-mode/
---

# Εξαγωγή κειμένου από τη σελίδα σε ακατέργαστη λειτουργία

## Εισαγωγή
Σε αυτό το σεμινάριο, θα μάθετε πώς να χρησιμοποιείτε το Groupdocs.Parser για .NET για να εξαγάγετε κείμενο από σελίδες εγγράφου σε μη επεξεργασμένη λειτουργία. Αυτή η βιβλιοθήκη παρέχει αποτελεσματικά εργαλεία για την ανάλυση και εξαγωγή περιεχομένου από διάφορες μορφές αρχείων, επιτρέποντας στους προγραμματιστές να ενσωματώσουν την εξαγωγή κειμένου εγγράφων στις εφαρμογές τους .NET.
## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
- Βασικές γνώσεις προγραμματισμού C# και .NET
- Το Visual Studio είναι εγκατεστημένο στον υπολογιστή σας
- Πρόσβαση στο Groupdocs.Parser για τη βιβλιοθήκη .NET
- Δείγμα αρχείου εγγράφου για δοκιμή

## Εισαγωγή χώρων ονομάτων
Ξεκινήστε συμπεριλαμβάνοντας τους απαραίτητους χώρους ονομάτων στο έργο σας C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Βήμα 1: Αρχικοποίηση του Parser
 Πρώτα, δημιουργήστε ένα παράδειγμα του`Parser` τάξη παρέχοντας τη διαδρομή προς το δείγμα αρχείου εγγράφου.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ο κωδικός σας εδώ
}
```
## Βήμα 2: Ανάκτηση πληροφοριών εγγράφου
 Ανάκτηση πληροφοριών σχετικά με το έγγραφο χρησιμοποιώντας`GetDocumentInfo()` μέθοδος.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Βήμα 3: Επανάληψη σε σελίδες και εξαγωγή κειμένου
Επαναλάβετε σε κάθε σελίδα του εγγράφου και εξαγάγετε περιεχόμενο κειμένου.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Εξαγωγή κειμένου από τη σελίδα
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## συμπέρασμα
Τώρα μάθατε πώς να χρησιμοποιείτε το Groupdocs.Parser για .NET για την εξαγωγή κειμένου από σελίδες εγγράφων σε μη επεξεργασμένη λειτουργία. Αυτό μπορεί να είναι ένα ισχυρό χαρακτηριστικό για εφαρμογές που χρειάζονται ανάλυση ή επεξεργασία περιεχομένου κειμένου από διάφορες μορφές αρχείων.

## Συχνές ερωτήσεις
### Είναι το Groupdocs.Parser για .NET συμβατό με όλες τις μορφές αρχείων;
Το Groupdocs.Parser υποστηρίζει ένα ευρύ φάσμα μορφών αρχείων, όπως PDF, DOCX, XLSX, PPTX, EPUB και άλλα.
### Μπορώ να εξαγάγω μεταδεδομένα μαζί με κείμενο χρησιμοποιώντας αυτήν τη βιβλιοθήκη;
Ναι, το Groupdocs.Parser σάς επιτρέπει να εξάγετε κείμενο και μεταδεδομένα από έγγραφα.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για δοκιμή;
 Ναι, μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμαστικής έκδοσης από[εδώ](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω τεχνική υποστήριξη για το Groupdocs.Parser;
 Για τεχνική βοήθεια, επισκεφθείτε το[Groupdocs.Parser φόρουμ](https://forum.groupdocs.com/c/parser/17).
### Πού μπορώ να αγοράσω άδεια χρήσης για το Groupdocs.Parser για .NET;
 Μπορείτε να αγοράσετε μια άδεια[εδώ](https://purchase.groupdocs.com/buy).