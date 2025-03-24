---
title: Wyodrębnij sformatowany tekst z dokumentu
linktitle: Wyodrębnij sformatowany tekst z dokumentu
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić sformatowany tekst z dokumentów za pomocą GroupDocs.Parser dla .NET. Prosta i wydajna ekstrakcja tekstu dla Twoich aplikacji.
weight: 10
url: /pl/net/formatted-text-extraction/extract-formatted-text-from-document/
---

# Wyodrębnij sformatowany tekst z dokumentu

## Wstęp
W tym samouczku omówimy, jak używać programu GroupDocs.Parser dla platformy .NET do wyodrębniania sformatowanego tekstu z różnych typów dokumentów. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom pracę z dokumentami w uproszczony i wydajny sposób. Po przeczytaniu tego przewodnika będziesz w stanie bezproblemowo zintegrować funkcje wyodrębniania tekstu z aplikacjami .NET.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
- Visual Studio: Upewnij się, że masz zainstalowany program Visual Studio w swoim systemie.
-  GroupDocs.Parser dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Parser z[Tutaj](https://releases.groupdocs.com/parser/net/).
- Próbki dokumentów: Przygotuj przykładowe dokumenty (np. PDF, DOCX) do wyodrębnienia tekstu.
## Importuj przestrzenie nazw
Najpierw uwzględnij niezbędne przestrzenie nazw w kodzie C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Rozpocznij od inicjalizacji a`Parser` obiekt ścieżką do przykładowego dokumentu.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Tutaj znajduje się kod wyodrębniania tekstu
}
```
 Zastępować`"YourSampleFile.pdf"` ze ścieżką do pliku dokumentu.

## Krok 2: Wyodrębnij sformatowany tekst
 W ramach`using` blokuj, użyj`GetFormattedText` metoda wyodrębniania sformatowanego tekstu z dokumentu. Określ żądany format wyjściowy (np. HTML) za pomocą`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Wyodrębnij sformatowany tekst do czytnika
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Sprawdź, czy ekstrakcja jest obsługiwana
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Przeczytaj i wyświetl wyodrębniony tekst
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Wniosek
Gratulacje! Nauczyłeś się, jak wyodrębniać sformatowany tekst z dokumentów za pomocą GroupDocs.Parser dla .NET. Ta wszechstronna biblioteka otwiera możliwości przetwarzania i analizy tekstu w aplikacjach.

## Często zadawane pytania
### P: Czy GroupDocs.Parser może wyodrębnić tekst z dokumentów chronionych hasłem?
O: Tak, GroupDocs.Parser obsługuje wyodrębnianie tekstu z dokumentów chronionych hasłem.
### P: Jakie formaty dokumentów są obsługiwane przez GroupDocs.Parser?
Odp.: GroupDocs.Parser obsługuje szeroką gamę formatów, w tym PDF, DOCX, XLSX, PPTX i inne.
### P: Jak mogę uzyskać tymczasową licencję na GroupDocs.Parser?
 Odpowiedź: Możesz uzyskać tymczasową licencję od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### P: Czy GroupDocs.Parser zapewnia obsługę wyodrębniania obrazów z dokumentów?
O: Tak, GroupDocs.Parser obsługuje wyodrębnianie obrazów wraz z wyodrębnianiem tekstu.
### P: Gdzie mogę znaleźć dodatkową pomoc lub zadać pytania dotyczące GroupDocs.Parser?
 O: Odwiedź[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)za wsparcie i dyskusje.