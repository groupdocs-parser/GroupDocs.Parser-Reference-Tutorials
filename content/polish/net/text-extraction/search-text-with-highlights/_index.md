---
title: Wyszukaj tekst z wyróżnieniami
linktitle: Wyszukaj tekst z wyróżnieniami
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyszukiwać i wyróżniać tekst w dokumentach za pomocą GroupDocs.Parser dla .NET. Efektywnie wydobywaj cenne informacje.
type: docs
weight: 24
url: /pl/net/text-extraction/search-text-with-highlights/
---
## Wstęp
tym samouczku omówimy, jak używać programu GroupDocs.Parser dla platformy .NET do wyszukiwania tekstu w dokumencie i wyróżniania wyników wyszukiwania. GroupDocs.Parser to potężna biblioteka, która umożliwia pracę z różnymi formatami dokumentów oraz wyodrębnianie tekstu, metadanych i nie tylko.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1.  GroupDocs.Parser dla .NET: Pobierz i zainstaluj bibliotekę z[Tutaj](https://releases.groupdocs.com/parser/net/).
2. IDE: Użyj Visual Studio lub dowolnego preferowanego IDE do programowania .NET.
3. Przykładowy plik: Przygotuj przykładowy dokument (np. PDF, DOCX) do wyszukiwania tekstu.

## Importuj przestrzenie nazw
Najpierw zacznij od zaimportowania niezbędnych przestrzeni nazw do projektu .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję analizatora składni
 Rozpocznij od utworzenia instancji`Parser` class ze ścieżką do przykładowego pliku:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Twój kod tutaj
}
```
## Krok 2: Zdefiniuj opcje podświetlenia
 Określić`HighlightOptions` aby skonfigurować sposób podświetlania wyników wyszukiwania. Na przykład ustawienie okna kontekstowego o długości 15 znaków:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Krok 3: Wyszukaj tekst
Teraz przeprowadź wyszukiwanie tekstowe w dokumencie. Podaj słowo kluczowe, które chcesz wyszukać (np. „lorem”):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Krok 4: Przetwórz wyniki wyszukiwania
Iteruj po wynikach wyszukiwania i wyświetl znaleziony tekst wraz z wyróżnieniami:
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

## Wniosek
tym samouczku nauczyłeś się używać narzędzia GroupDocs.Parser dla platformy .NET do wyszukiwania tekstu w dokumentach i wyróżniania wyników wyszukiwania. Ta funkcja może być niezwykle przydatna do wyodrębniania i analizy tekstu w aplikacjach .NET.

## Często zadawane pytania
### Czy GroupDocs.Parser nadaje się do przetwarzania różnych formatów dokumentów?
Tak, GroupDocs.Parser obsługuje szeroką gamę formatów dokumentów, w tym PDF, DOCX, XLSX, PPTX i inne.
### Czy mogę używać GroupDocs.Parser do wyodrębniania metadanych z dokumentów?
Absolutnie! GroupDocs.Parser umożliwia wyodrębnianie metadanych, tekstu i danych strukturalnych z dokumentów.
### Gdzie mogę znaleźć pomoc lub zadać pytania dotyczące GroupDocs.Parser?
 Możesz odwiedzić[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) w przypadku jakichkolwiek pytań związanych ze wsparciem.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Parser?
 Tak, możesz uzyskać dostęp do[bezpłatna wersja próbna](https://releases.groupdocs.com/) z GroupDocs.Parser, aby ocenić jego funkcje.
### Jak mogę kupić licencję na GroupDocs.Parser?
 Możesz kupić licencję od[Tutaj](https://purchase.groupdocs.com/buy) a także uzyskać tymczasowe licencje[Tutaj](https://purchase.groupdocs.com/temporary-license/).