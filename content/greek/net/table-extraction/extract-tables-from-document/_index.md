---
title: Εξαγωγή πινάκων από το έγγραφο
linktitle: Εξαγωγή πινάκων από το έγγραφο
second_title: GroupDocs.Parser .NET API
description: Μάθετε πώς να εξάγετε πίνακες από έγγραφα χρησιμοποιώντας το Groupdocs.Parser για .NET. Ακολουθήστε έναν λεπτομερή οδηγό σχετικά με την ενσωμάτωση αυτής της λειτουργικότητας.
weight: 10
url: /el/net/table-extraction/extract-tables-from-document/
---
## Εισαγωγή
Το Groupdocs.Parser για .NET είναι μια ολοκληρωμένη βιβλιοθήκη που διευκολύνει την ανάλυση εγγράφων, επιτρέποντάς σας να εξάγετε πολύτιμες πληροφορίες όπως πίνακες, κείμενο, μεταδεδομένα και άλλα από έγγραφα. Σε αυτό το σεμινάριο, εστιάζουμε ειδικά στην εξαγωγή πινάκων από έγγραφα χρησιμοποιώντας το Groupdocs.Parser API.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
- Το Visual Studio είναι εγκατεστημένο στο σύστημά σας.
- Εγκατεστημένο .NET Framework ή .NET Core.
- Βασικές γνώσεις προγραμματισμού C#.

## Εισαγωγή χώρων ονομάτων
Αρχικά, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων για πρόσβαση στις κλάσεις και τις μεθόδους Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Βήμα 1: Δημιουργήστε μια παρουσία κλάσης Parser
 Αρχικοποιήστε μια νέα παρουσία του`Parser` τάξη παρέχοντας τη διαδρομή προς το δείγμα εγγράφου σας.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ο κωδικός σας πηγαίνει εδώ
}
```
## Βήμα 2: Ελέγξτε την Υποστήριξη εξαγωγής πίνακα
 Επαληθεύστε εάν το έγγραφο υποστηρίζει την εξαγωγή πίνακα χρησιμοποιώντας το`Features` ιδιοκτησία του`Parser` τάξη.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Βήμα 3: Ορισμός διάταξης πίνακα
Καθορίστε τη διάταξη των πινάκων που θέλετε να εξαγάγετε χρησιμοποιώντας`TemplateTableLayout`. Καθορίστε πλάτη στηλών και ύψη σειρών με βάση τη δομή του εγγράφου σας.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Βήμα 4: Ορισμός επιλογών εξαγωγής πίνακα
 Δημιουργώ`PageTableAreaOptions` με την καθορισμένη διάταξη για να καθορίσετε τον τρόπο εξαγωγής των πινάκων.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Βήμα 5: Εξαγωγή πινάκων
 Χρησιμοποιήστε το`GetTables` μέθοδος του`Parser` κλάση για εξαγωγή πινάκων από το έγγραφο με βάση τις καθορισμένες επιλογές.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Βήμα 6: Επανάληψη και πρόσβαση σε δεδομένα πίνακα
Επαναλάβετε τους πίνακες που έχουν εξαχθεί και τις αντίστοιχες γραμμές και στήλες τους για να αποκτήσετε πρόσβαση στα δεδομένα κελιών.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## συμπέρασμα
Σε αυτό το σεμινάριο, έχουμε καλύψει τον τρόπο χρήσης του Groupdocs.Parser για .NET για την αποτελεσματική εξαγωγή πινάκων από έγγραφα. Αξιοποιώντας τις δυνατότητες αυτής της βιβλιοθήκης, μπορείτε να ενσωματώσετε την εξαγωγή πινάκων στις εφαρμογές σας .NET απρόσκοπτα.

## Συχνές ερωτήσεις
### Μπορεί το Groupdocs.Parser να χειριστεί διαφορετικές μορφές εγγράφων;
Ναι, το Groupdocs.Parser υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των DOCX, PDF, XLSX και άλλων.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το Groupdocs.Parser για .NET;
 Ναι, μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμής από[εδώ](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω υποστήριξη για ερωτήματα που σχετίζονται με το Groupdocs.Parser;
 Μπορείτε να επισκεφθείτε το[Groupdocs.Parser φόρουμ](https://forum.groupdocs.com/c/parser/17) για βοήθεια.
### Πού μπορώ να αγοράσω άδεια χρήσης για το Groupdocs.Parser;
 Μπορείτε να αγοράσετε άδεια από[εδώ](https://purchase.groupdocs.com/buy).
### Πώς μπορώ να αποκτήσω προσωρινή άδεια για λόγους αξιολόγησης;
 Μπορείτε να αποκτήσετε μια προσωρινή άδεια[εδώ](https://purchase.groupdocs.com/temporary-license/).