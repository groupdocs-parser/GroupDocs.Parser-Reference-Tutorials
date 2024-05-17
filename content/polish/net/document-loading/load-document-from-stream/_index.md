---
title: Załaduj dokument ze strumienia
linktitle: Załaduj dokument ze strumienia
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić tekst z różnych formatów dokumentów w .NET przy użyciu GroupDocs.Parser. Przewodnik krok po kroku z przykładami kodu.
type: docs
weight: 12
url: /pl/net/document-loading/load-document-from-stream/
---
## Wstęp
W obszarze przetwarzania dokumentów w aplikacjach .NET powszechnym wymogiem jest wyodrębnianie tekstu z plików o różnych formatach. GroupDocs.Parser dla .NET oferuje zaawansowane rozwiązanie do płynnego analizowania i wyodrębniania tekstu z różnorodnych dokumentów. Ten samouczek poprowadzi Cię krok po kroku przez proces wykorzystania GroupDocs.Parser do wyodrębniania tekstu z dokumentów.
## Warunki wstępne
Zanim zaczniesz korzystać z GroupDocs.Parser dla .NET, upewnij się, że masz następującą konfigurację:
- Środowisko programistyczne: Visual Studio lub dowolne inne środowisko programistyczne .NET.
-  Pakiet GroupDocs.Parser dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Parser dla .NET ze strony[Tutaj](https://releases.groupdocs.com/parser/net/).
- Próbki dokumentów: Przygotuj przykładowe dokumenty do wyodrębnienia tekstu.
## Importowanie przestrzeni nazw
Rozpocznij od zaimportowania niezbędnych przestrzeni nazw do projektu .NET, aby uzyskać dostęp do funkcjonalności GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Poniższe kroki pokazują, jak wyodrębnić tekst z dokumentu przy użyciu GroupDocs.Parser ze strumienia.
## Krok 1: Załaduj dokument ze strumienia
```csharp
// Utwórz strumień
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Utwórz instancję klasy Parser ze strumieniem
    using (Parser parser = new Parser(stream))
    {
        // Wyodrębnij tekst do czytnika
        using (TextReader reader = parser.GetText())
        {
            // Wydrukuj tekst z dokumentu
            // Jeśli wyodrębnianie tekstu nie jest obsługiwane, czytnik będzie miał wartość null
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
W tym przykładzie:
- Otwieramy strumień pliku dla pliku dokumentu (`YourSampleFile.docx`).
-  Zainicjuj a`Parser` przykład ze strumieniem.
-  Używać`parser.GetText()` odzyskać A`TextReader` zawierający wyodrębniony tekst.
- Wydrukuj wyodrębniony tekst lub wiadomość, jeśli wyodrębnianie tekstu nie jest obsługiwane w danym formacie dokumentu.
## Wniosek
GroupDocs.Parser dla .NET upraszcza wyodrębnianie tekstu z różnych formatów dokumentów, umożliwiając programistom wydajne przetwarzanie i wykorzystywanie treści tekstowych w swoich aplikacjach. Wykonując kroki opisane w tym samouczku, możesz bezproblemowo zintegrować możliwości wyodrębniania tekstu dokumentu z projektami .NET.

## Często zadawane pytania
### Jakie formaty dokumentów są obsługiwane przez GroupDocs.Parser dla .NET?
GroupDocs.Parser obsługuje szeroką gamę formatów dokumentów, w tym DOCX, PDF, XLSX, PPTX, EPUB i inne.
### Czy GroupDocs.Parser może wyodrębniać obrazy lub metadane z dokumentów?
Tak, GroupDocs.Parser może wyodrębniać obrazy, metadane i tekst z różnych typów dokumentów.
### Czy GroupDocs.Parser jest zgodny z aplikacjami .NET Core?
Tak, GroupDocs.Parser jest kompatybilny zarówno z aplikacjami .NET Framework, jak i .NET Core.
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Parser?
 Licencję tymczasową można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę znaleźć dodatkowe wsparcie lub dokumentację dotyczącą GroupDocs.Parser?
 Aby uzyskać dodatkowe wsparcie, odwiedź stronę[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) lub zapoznaj się z[dokumentacja](https://reference.groupdocs.com/parser/net/).
