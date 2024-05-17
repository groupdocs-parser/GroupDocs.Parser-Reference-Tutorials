---
title: Εργασία με πεδία σε σταθερές θέσεις σε πρότυπα
linktitle: Εργασία με πεδία σε σταθερές θέσεις σε πρότυπα
second_title: GroupDocs.Parser .NET API
description: Μάθετε πώς να εξάγετε δεδομένα από έγγραφα χρησιμοποιώντας το GroupDocs.Parser για .NET. Ολοκληρωμένο σεμινάριο με παραδείγματα κώδικα.
type: docs
weight: 11
url: /el/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα εξερευνήσουμε τον τρόπο εργασίας με πεδία σε σταθερές θέσεις μέσα σε πρότυπα χρησιμοποιώντας το GroupDocs.Parser για .NET. Το GroupDocs.Parser είναι μια ισχυρή βιβλιοθήκη ανάλυσης εγγράφων που επιτρέπει στους προγραμματιστές να εξάγουν δεδομένα από διάφορες μορφές εγγράφων όπως PDF, Word, Excel και άλλα. Συγκεκριμένα, θα επικεντρωθούμε στον καθορισμό και τη χρήση πεδίων προτύπων για την εξαγωγή στοχευμένων πληροφοριών με βάση τις σταθερές θέσεις τους.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
- Βασική κατανόηση της ανάπτυξης C# και .NET.
- Το Visual Studio είναι εγκατεστημένο στο σύστημά σας.
- Εγκαταστάθηκε το GroupDocs.Parser για τη βιβλιοθήκη .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/parser/net/).
- Δείγματα αρχείων εγγράφων για δοκιμή.

## Εισαγωγή χώρων ονομάτων
Ξεκινήστε συμπεριλαμβάνοντας τους απαραίτητους χώρους ονομάτων στο έργο σας C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Βήμα 1: Ορίστε ένα πεδίο προτύπου
Αρχικά, ορίστε ένα πεδίο με σταθερή θέση μέσα σε ένα πρότυπο. Αυτό το πεδίο αντιπροσωπεύει την περιοχή από την οποία θα εξαχθούν τα δεδομένα.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Εδώ:
- `Rectangle` καθορίζει τη θέση και το μέγεθος του πεδίου.
- `Point(35, 135)` αντιπροσωπεύει τις συντεταγμένες πάνω-αριστερής γωνίας.
- `Size(100, 10)` ορίζει το πλάτος και το ύψος του πεδίου.
- `"FromCompany"` είναι το όνομα που έχει εκχωρηθεί σε αυτό το πεδίο.
## Βήμα 2: Δημιουργήστε ένα πρότυπο
Κατασκευάστε ένα πρότυπο χρησιμοποιώντας το καθορισμένο πεδίο.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 ο`Template` αντικείμενο περιέχει τα καθορισμένα πεδία.
## Βήμα 3: Ανάλυση εγγράφου χρησιμοποιώντας το πρότυπο
 Στιγμιότυπο το`Parser` κλάση με τη διαδρομή εγγράφου προορισμού και, στη συνέχεια, αναλύστε το έγγραφο χρησιμοποιώντας το πρότυπο που δημιουργήθηκε.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Επανάληψη μέσω εξαγόμενων δεδομένων
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Εδώ:
- `Parser` αρχικοποιείται με τη διαδρομή αρχείου δείγματος εγγράφου.
- `ParseByTemplate` μέθοδος χρησιμοποιείται για την εξαγωγή δεδομένων με βάση το παρεχόμενο πρότυπο.
-  Η πρόσβαση στα εξαγόμενα δεδομένα γίνεται χρησιμοποιώντας`DocumentData`όπου κάθε στοιχείο αντιστοιχεί σε ένα καθορισμένο πεδίο.

## συμπέρασμα
Σε αυτό το σεμινάριο, καλύψαμε τη διαδικασία εργασίας με πεδία σε σταθερές θέσεις σε πρότυπα χρησιμοποιώντας το GroupDocs.Parser για .NET. Ορίζοντας πρότυπα με συγκεκριμένες θέσεις πεδίων, οι προγραμματιστές μπορούν να εξάγουν με ακρίβεια στοχευμένα δεδομένα από διάφορες μορφές εγγράφων.

## Συχνές ερωτήσεις
### Είναι το GroupDocs.Parser συμβατό με όλες τις μορφές εγγράφων;
 Το GroupDocs.Parser υποστηρίζει ένα ευρύ φάσμα μορφών αρχείων, συμπεριλαμβανομένων των PDF, Microsoft Word, Excel, PowerPoint και άλλων. Αναφέρομαι στο[τεκμηρίωση](https://reference.groupdocs.com/parser/net/) για αναλυτική λίστα.
### Πώς μπορώ να αποκτήσω μια προσωρινή άδεια για το GroupDocs.Parser;
 Μπορείτε να λάβετε μια προσωρινή άδεια για σκοπούς δοκιμής από[εδώ](https://purchase.groupdocs.com/temporary-license/).
### Πού μπορώ να βρω υποστήριξη για το GroupDocs.Parser;
 Για τεχνική βοήθεια και συζητήσεις, επισκεφθείτε τη διεύθυνση[GroupDocs.Parser φόρουμ](https://forum.groupdocs.com/c/parser/17).
### Μπορώ να δοκιμάσω το GroupDocs.Parser πριν το αγοράσω;
 Ναι, μπορείτε να εξερευνήσετε τη βιβλιοθήκη με μια δωρεάν δοκιμή διαθέσιμη[εδώ](https://releases.groupdocs.com/).
### Πώς μπορώ να αγοράσω άδεια χρήσης για το GroupDocs.Parser;
 Για να αγοράσετε μια άδεια, επισκεφτείτε το[σελίδα αγοράς](https://purchase.groupdocs.com/buy).