---
title: Αναζήτηση κειμένου κατά κανονική έκφραση (Regex)
linktitle: Αναζήτηση κειμένου κατά κανονική έκφραση (Regex)
second_title: GroupDocs.Parser .NET API
description: Μάθετε πώς να αναζητάτε κείμενο χρησιμοποιώντας κανονικές εκφράσεις σε έγγραφα χρησιμοποιώντας το GroupDocs.Parser για .NET. Εξαγωγή συγκεκριμένου περιεχομένου χωρίς κόπο.
weight: 23
url: /el/net/text-extraction/search-text-by-regex/
---

# Αναζήτηση κειμένου κατά κανονική έκφραση (Regex)

## Εισαγωγή
Σε αυτό το σεμινάριο, θα εμβαθύνουμε στη χρήση του GroupDocs.Parser για .NET για αναζήτηση κειμένου με κανονική έκφραση (Regex) μέσα σε έγγραφα. Το GroupDocs.Parser είναι μια ισχυρή βιβλιοθήκη που επιτρέπει στους προγραμματιστές να εξάγουν κείμενο και μεταδεδομένα από διάφορες μορφές αρχείων όπως PDF, DOCX, XLSX και άλλα. Η αναζήτηση κειμένου χρησιμοποιώντας κανονικές εκφράσεις είναι ιδιαίτερα χρήσιμη για την αποτελεσματική εύρεση μοτίβων ή συγκεκριμένου περιεχομένου μέσα στα έγγραφα.
## Προαπαιτούμενα
Πριν προχωρήσετε σε αυτό το σεμινάριο, βεβαιωθείτε ότι έχετε τα εξής:
1. Visual Studio: Εγκαταστήστε το Visual Studio IDE για ανάπτυξη .NET.
2.  GroupDocs.Parser για .NET: Λήψη και εγκατάσταση του GroupDocs.Parser για .NET από[εδώ](https://releases.groupdocs.com/parser/net/).
3. Δείγμα αρχείου: Προετοιμάστε ένα δείγμα εγγράφου (PDF, DOCX, κ.λπ.) για τον έλεγχο της λειτουργικότητας αναζήτησης.

## Εισαγωγή χώρων ονομάτων
Αρχικά, ξεκινήστε συμπεριλαμβάνοντας τους απαραίτητους χώρους ονομάτων στον κώδικα C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Βήμα 1: Δημιουργήστε μια παρουσία κλάσης Parser
 Στιγμιότυπο το`Parser` τάξη παρέχοντας τη διαδρομή προς το δείγμα αρχείου σας:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ο κώδικας πηγαίνει εδώ
}
```
 Αντικαθιστώ`"YourSampleFile.pdf"` με τη διαδρομή προς το πραγματικό σας αρχείο.
## Βήμα 2: Αναζήτηση με χρήση κανονικής έκφρασης
Ορίστε και εκτελέστε την αναζήτηση χρησιμοποιώντας ένα μοτίβο τυπικής έκφρασης. Για παράδειγμα, για να βρείτε αριθμητικές ακολουθίες (π.χ. ακέραιους αριθμούς) μέσα στο έγγραφο:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 Σε αυτό το παράδειγμα,`[0-9]+` είναι ένα τυπικό μοτίβο έκφρασης που ταιριάζει με ένα ή περισσότερα ψηφία.
## Βήμα 3: Ελέγξτε την υποστήριξη αναζήτησης
Επαληθεύστε εάν η λειτουργία αναζήτησης υποστηρίζεται για τον τύπο εγγράφου:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Βήμα 4: Επαναλάβετε τα αποτελέσματα αναζήτησης
Επαναλάβετε τα αποτελέσματα αναζήτησης και επεξεργαστείτε κάθε αντιστοιχία:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Αυτός ο βρόχος θα εκτυπώσει τη θέση και το αντίστοιχο κείμενο που βρίσκεται μέσα στο έγγραφο.

## συμπέρασμα
Συμπερασματικά, η αξιοποίηση του GroupDocs.Parser για .NET επιτρέπει την αποτελεσματική αναζήτηση κειμένου χρησιμοποιώντας κανονικές εκφράσεις σε διάφορες μορφές εγγράφων. Ακολουθώντας αυτόν τον οδηγό, οι προγραμματιστές μπορούν να ενσωματώσουν απρόσκοπτα την ανάλυση εγγράφων και την εξαγωγή κειμένου βάσει regex στις εφαρμογές τους .NET.

## Συχνές ερωτήσεις
### Μπορεί το GroupDocs.Parser να κάνει αναζήτηση σε κρυπτογραφημένα έγγραφα;
Όχι, το GroupDocs.Parser δεν μπορεί να πραγματοποιήσει αναζήτηση σε κρυπτογραφημένα έγγραφα ή έγγραφα που προστατεύονται με κωδικό πρόσβασης.
### Υποστηρίζει το GroupDocs.Parser το OCR (Optical Character Recognition);
Όχι, το GroupDocs.Parser δεν εκτελεί OCR. Βασίζεται στην εξαγωγή κειμένου από την εσωτερική δομή του εγγράφου.
### Μπορώ να αναζητήσω σύνθετα μοτίβα χρησιμοποιώντας κανονικές εκφράσεις;
Ναι, το GroupDocs.Parser υποστηρίζει πλήρεις κανονικές εκφράσεις, επιτρέποντας την αντιστοίχιση σύνθετων προτύπων στα έγγραφα.
### Ποιες μορφές εγγράφων υποστηρίζονται για εξαγωγή κειμένου;
Το GroupDocs.Parser υποστηρίζει ένα ευρύ φάσμα μορφών, συμπεριλαμβανομένων των PDF, DOCX, XLSX, PPTX και άλλων.
### Είναι το GroupDocs.Parser συμβατό με .NET Core;
Ναι, το GroupDocs.Parser είναι συμβατό με το .NET Core για ανάπτυξη πολλαπλών πλατφορμών.