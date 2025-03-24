---
title: Wyodrębnij tekst z dokumentu Word jako HTML
linktitle: Wyodrębnij tekst z dokumentu Word jako HTML
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak używać GroupDocs.Parser dla .NET do wyodrębniania tekstu z dokumentów programu Word i zapisywania go w formacie HTML. Samouczek krok po kroku z przykładami kodu.
weight: 16
url: /pl/net/word-document-processing/extract-text-from-word-document-as-html/
---

# Wyodrębnij tekst z dokumentu Word jako HTML

## Wstęp
GroupDocs.Parser dla .NET to potężna biblioteka do analizowania dokumentów, która umożliwia programistom bezproblemowe wyodrębnianie tekstu i metadanych z różnych formatów plików. W tym samouczku skupimy się na wykorzystaniu narzędzia GroupDocs.Parser do wyodrębniania tekstu z dokumentów programu Word i zapisywania go w formacie HTML. Proces ten jest niezbędny w przypadku zadań takich jak analiza treści, indeksowanie lub konwertowanie dokumentów do formatów przyjaznych dla Internetu. Pod koniec tego przewodnika będziesz już w pełni świadomy, jak efektywnie używać GroupDocs.Parser w aplikacjach .NET.
## Warunki wstępne
Zanim zagłębisz się w ten samouczek, upewnij się, że spełniasz następujące wymagania wstępne:
- Podstawowa znajomość programowania w języku C#.
- Program Visual Studio zainstalowany na komputerze programistycznym.
-  Biblioteka GroupDocs.Parser dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/parser/net/).
- Dostęp do przykładowego dokumentu Word w celach testowych.
## Importuj przestrzenie nazw
Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Wykonaj poniższe szczegółowe kroki, aby wyodrębnić tekst z dokumentu programu Word i zapisać go w formacie HTML przy użyciu GroupDocs.Parser dla .NET:
## Krok 1: Utwórz instancję klasy analizatora składni
 Najpierw utwórz instancję`Parser` class, podając ścieżkę do przykładowego dokumentu programu Word:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Przejdź do kroku 2...
}
```
 Zastępować`"YourSampleFile.docx"`ze ścieżką do dokumentu programu Word.
## Krok 2: Wyodrębnij sformatowany tekst jako HTML
 Następnie użyj`GetFormattedText` metoda wraz z`FormattedTextOptions`aby wyodrębnić tekst w formacie HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Wyodrębnij sformatowany tekst do czytnika
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Przejdź do kroku 3...
    }
}
```
## Krok 3: Przeczytaj i wyślij wyodrębniony kod HTML
 Na koniec przeczytaj wyodrębnioną treść HTML z pliku`TextReader` i wydrukuj go na konsoli:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Wyodrębnij sformatowany tekst do czytnika
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Wydrukuj sformatowany tekst jako HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Wniosek
W tym samouczku omówiliśmy, jak używać programu GroupDocs.Parser dla platformy .NET do wyodrębniania tekstu z dokumentu programu Word i zapisywania go w formacie HTML. Biblioteka ta oferuje prosty i wydajny sposób analizowania treści dokumentów, co czyni ją nieocenionym narzędziem do zadań związanych z przetwarzaniem dokumentów w aplikacjach .NET.

## Często zadawane pytania
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Parser?
 Możesz poprosić o licencję tymczasową od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę znaleźć więcej dokumentacji dla GroupDocs.Parser?
 Dostępna jest szczegółowa dokumentacja[Tutaj](https://tutorials.groupdocs.com/parser/net/).
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Parser?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej[Tutaj](https://releases.groupdocs.com/).
### Jak uzyskać pomoc dotyczącą GroupDocs.Parser?
 Odwiedź forum pomocy[Tutaj](https://forum.groupdocs.com/c/parser/17).
### Jakie typy dokumentów obsługuje GroupDocs.Parser?
GroupDocs.Parser obsługuje różne formaty dokumentów, w tym Word, PDF, Excel, PowerPoint i inne.