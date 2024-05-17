---
title: Αναζήτηση κειμένου με επισημάνσεις
linktitle: Αναζήτηση κειμένου με επισημάνσεις
second_title: GroupDocs.Parser .NET API
description: Μάθετε πώς να αναζητάτε και να επισημαίνετε κείμενο σε έγγραφα χρησιμοποιώντας το GroupDocs.Parser για .NET. Εξάγετε πολύτιμες γνώσεις αποτελεσματικά.
type: docs
weight: 24
url: /el/net/text-extraction/search-text-with-highlights/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να χρησιμοποιήσετε το GroupDocs.Parser για .NET για να αναζητήσετε κείμενο μέσα σε ένα έγγραφο και να επισημάνετε τα αποτελέσματα αναζήτησης. Το GroupDocs.Parser είναι μια ισχυρή βιβλιοθήκη που σας επιτρέπει να εργάζεστε με διάφορες μορφές εγγράφων και να εξάγετε κείμενο, μεταδεδομένα και πολλά άλλα.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1.  GroupDocs.Parser για .NET: Λήψη και εγκατάσταση της βιβλιοθήκης από[εδώ](https://releases.groupdocs.com/parser/net/).
2. IDE: Χρησιμοποιήστε το Visual Studio ή οποιοδήποτε προτιμώμενο IDE για την ανάπτυξη .NET.
3. Δείγμα αρχείου: Προετοιμάστε ένα δείγμα εγγράφου (π.χ. PDF, DOCX) για αναζήτηση κειμένου.

## Εισαγωγή χώρων ονομάτων
Αρχικά, ξεκινήστε εισάγοντας τους απαραίτητους χώρους ονομάτων στο έργο σας .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Βήμα 1: Δημιουργία παρουσίας Parser
 Ξεκινήστε στιγμιαία του`Parser` κλάση με τη διαδρομή προς το δείγμα αρχείου σας:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ο κωδικός σας εδώ
}
```
## Βήμα 2: Καθορισμός Επιλογών Επισήμανσης
 Προσδιορίστε το`HighlightOptions` για να διαμορφώσετε τον τρόπο με τον οποίο θα επισημαίνονται τα αποτελέσματα αναζήτησης. Για παράδειγμα, ορίζοντας ένα παράθυρο περιβάλλοντος 15 χαρακτήρων:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Βήμα 3: Αναζήτηση κειμένου
Τώρα, εκτελέστε μια αναζήτηση κειμένου μέσα στο έγγραφο. Καταχωρίστε τη λέξη-κλειδί που θέλετε να αναζητήσετε (π.χ. "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Βήμα 4: Επεξεργαστείτε τα αποτελέσματα αναζήτησης
Επαναλάβετε τα αποτελέσματα αναζήτησης και εμφανίστε το κείμενο που βρέθηκε μαζί με τις καλύτερες στιγμές:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## συμπέρασμα
Σε αυτό το σεμινάριο, μάθατε πώς να χρησιμοποιείτε το GroupDocs.Parser για .NET για την αναζήτηση κειμένου μέσα στα έγγραφα και την επισήμανση των αποτελεσμάτων αναζήτησης. Αυτή η λειτουργία μπορεί να είναι εξαιρετικά χρήσιμη για εξαγωγή και ανάλυση κειμένου στις εφαρμογές σας .NET.

## Συχνές ερωτήσεις
### Είναι το GroupDocs.Parser κατάλληλο για την επεξεργασία διαφόρων μορφών εγγράφων;
Ναι, το GroupDocs.Parser υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των PDF, DOCX, XLSX, PPTX και άλλων.
### Μπορώ να χρησιμοποιήσω το GroupDocs.Parser για εξαγωγή μεταδεδομένων από έγγραφα;
Απολύτως! Το GroupDocs.Parser σάς επιτρέπει να εξάγετε μεταδεδομένα, κείμενο και δομημένα δεδομένα από έγγραφα.
### Πού μπορώ να βρω υποστήριξη ή να κάνω ερωτήσεις σχετικά με το GroupDocs.Parser;
 Μπορείτε να επισκεφθείτε το[GroupDocs.Parser φόρουμ](https://forum.groupdocs.com/c/parser/17) για τυχόν ερωτήματα που σχετίζονται με την υποστήριξη.
### Υπάρχει διαθέσιμη δωρεάν δοκιμή για το GroupDocs.Parser;
 Ναι, μπορείτε να έχετε πρόσβαση σε ένα[δωρεάν δοκιμή](https://releases.groupdocs.com/) του GroupDocs.Parser για να αξιολογήσει τις δυνατότητές του.
### Πώς μπορώ να αγοράσω άδεια χρήσης για το GroupDocs.Parser;
 Μπορείτε να αγοράσετε άδεια από[εδώ](https://purchase.groupdocs.com/buy) και επίσης να αποκτήσουν προσωρινές άδειες[εδώ](https://purchase.groupdocs.com/temporary-license/).