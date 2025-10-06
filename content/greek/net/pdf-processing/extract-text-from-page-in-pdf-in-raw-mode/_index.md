---
title: Εξαγωγή κειμένου από τη σελίδα σε PDF σε Raw Mode
linktitle: Εξαγωγή κειμένου από τη σελίδα σε PDF σε Raw Mode
second_title: GroupDocs.Parser .NET API
description: Εξαγωγή κειμένου από αρχεία PDF χρησιμοποιώντας GroupDocs.Parser σε C#. Μάθετε αποτελεσματική εξαγωγή κειμένου PDF με αυτήν την ισχυρή βιβλιοθήκη .NET.
weight: 16
url: /el/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
type: docs
---
# Εξαγωγή κειμένου από τη σελίδα σε PDF σε Raw Mode

## Εισαγωγή
Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να χρησιμοποιήσετε το GroupDocs.Parser για .NET για να εξαγάγετε κείμενο από σελίδες σε έγγραφα PDF χρησιμοποιώντας τη λειτουργία raw. Το GroupDocs.Parser είναι ένα ισχυρό εργαλείο που επιτρέπει στους προγραμματιστές να εργάζονται με διάφορες μορφές εγγράφων μέσω προγραμματισμού.
## Προαπαιτούμενα
Πριν ξεκινήσετε αυτό το σεμινάριο, βεβαιωθείτε ότι έχετε τα εξής:
- Το Visual Studio είναι εγκατεστημένο στον υπολογιστή σας.
- Βασικές γνώσεις προγραμματισμού C#.
- GroupDocs.Parser για τη βιβλιοθήκη .NET, το οποίο μπορείτε[κατέβασε εδώ](https://releases.groupdocs.com/parser/net/).
- Ένα δείγμα αρχείου PDF για δοκιμαστικούς σκοπούς.

## Εισαγωγή χώρων ονομάτων
Πρώτα, φροντίστε να εισαγάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Βήμα 1: Δημιουργήστε μια παρουσία κλάσης Parser
 Για να ξεκινήσετε, δημιουργήστε το`Parser`τάξη παρέχοντας τη διαδρομή προς το δείγμα αρχείου PDF σας.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ο κωδικός σας πηγαίνει εδώ
}
```
## Βήμα 2: Λάβετε πληροφορίες εγγράφου και επαναλάβετε τις σελίδες
Στη συνέχεια, ανακτήστε τις πληροφορίες του εγγράφου και επαναλάβετε σε κάθε σελίδα για να εξαγάγετε κείμενο.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Ο κωδικός σας για εξαγωγή κειμένου πηγαίνει εδώ
}
```
## Βήμα 3: Εξαγωγή κειμένου από κάθε σελίδα
 Εντός του βρόχου, χρησιμοποιήστε το`GetText` μέθοδος εξαγωγής κειμένου από κάθε σελίδα και εκτύπωσης.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## συμπέρασμα
 Σε αυτό το σεμινάριο, μάθαμε πώς να εξάγουμε κείμενο από σελίδες PDF σε μη επεξεργασμένη λειτουργία χρησιμοποιώντας το GroupDocs.Parser για .NET. Αυτή η διαδικασία περιλαμβάνει τη δημιουργία ενός`Parser` για παράδειγμα, λήψη πληροφοριών εγγράφου, επανάληψη σε κάθε σελίδα και εξαγωγή κειμένου χρησιμοποιώντας το`GetText` μέθοδος.

## Συχνές ερωτήσεις
### Τι είναι το GroupDocs.Parser για .NET;
Το GroupDocs.Parser για .NET είναι ένα API ανάλυσης εγγράφων που επιτρέπει στους προγραμματιστές να εξάγουν κείμενο, μεταδεδομένα και άλλες πληροφορίες από διάφορες μορφές αρχείων μέσω προγραμματισμού.
### Πώς μπορώ να κατεβάσω το GroupDocs.Parser για .NET;
 Μπορείτε να κατεβάσετε τη βιβλιοθήκη από το[Ιστότοπος GroupDocs](https://releases.groupdocs.com/parser/net/).
### Υπάρχει δωρεάν δοκιμή διαθέσιμη;
 Ναι, μπορείτε να αποκτήσετε πρόσβαση σε μια δωρεάν δοκιμή του GroupDocs.Parser για .NET από[εδώ](https://releases.groupdocs.com/).
### Πού μπορώ να βρω υποστήριξη για το GroupDocs.Parser για .NET;
 Για τεχνική βοήθεια και κοινοτική υποστήριξη, επισκεφθείτε τη διεύθυνση[Φόρουμ GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Πώς μπορώ να αγοράσω άδεια χρήσης για το GroupDocs.Parser για .NET;
 Μπορείτε να αγοράσετε άδεια από το[σελίδα αγοράς](https://purchase.groupdocs.com/buy) ή να αποκτήσουν προσωρινή άδεια[εδώ](https://purchase.groupdocs.com/temporary-license/).