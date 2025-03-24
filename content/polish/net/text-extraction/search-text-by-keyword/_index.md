---
title: Wyszukaj tekst według słowa kluczowego
linktitle: Wyszukaj tekst według słowa kluczowego
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyszukiwać tekst według słów kluczowych w dokumentach przy użyciu programu GroupDocs.Parser dla platformy .NET. Wydajnie i z łatwością wyodrębniaj istotne treści.
weight: 21
url: /pl/net/text-extraction/search-text-by-keyword/
---

# Wyszukaj tekst według słowa kluczowego

## Wstęp
W tym samouczku omówimy wykorzystanie GroupDocs.Parser dla .NET do wyszukiwania tekstu według słów kluczowych w dokumentach. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom wyodrębnianie tekstu, metadanych i innych informacji z różnych formatów plików, takich jak pliki PDF, dokumenty Microsoft Office i inne. Wyszukiwanie określonych słów kluczowych w tych dokumentach może być niezbędne w przypadku aplikacji obsługujących duże ilości danych tekstowych.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następującą konfigurację:
1. Środowisko programistyczne: Visual Studio lub dowolne preferowane .NET IDE.
2.  GroupDocs.Parser dla .NET: Pobierz bibliotekę z[Tutaj](https://releases.groupdocs.com/parser/net/).
3. Dostęp do przykładowych plików: Przygotuj przykładowy plik (np. PDF, DOCX), aby przetestować funkcję wyszukiwania słów kluczowych.

## Importuj przestrzenie nazw
Najpierw musisz uwzględnić w projekcie niezbędne przestrzenie nazw.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Rozpocznij od utworzenia instancji`Parser` class i podaj ścieżkę do przykładowego pliku.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Wyszukaj słowo kluczowe
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Iteruj po wynikach wyszukiwania
    foreach (SearchResult result in searchResults)
    {
        //Wydrukuj indeks i znaleziony tekst
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Krok 2: Wyszukaj słowo kluczowe
 W ramach`using` zablokuj, zadzwoń`Search` metoda na`parser` obiekt, przekazując żądane słowo kluczowe jako argument.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Zastępować`"test"` ze słowem kluczowym, które chcesz wyszukać w dokumencie.
## Krok 3: Iteruj po wynikach wyszukiwania
 Następnie iteruj po wynikach wyszukiwania uzyskanych z`Search` metoda wykorzystująca A`foreach` pętla.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Dla każdego`SearchResult` obiekt`result` , możesz uzyskać do niego dostęp`Position` (indeks) i`Text` (znaleziony tekst).

## Wniosek
 W tym samouczku omówiliśmy, jak używać programu GroupDocs.Parser dla platformy .NET do łatwego wyszukiwania tekstu według słów kluczowych w dokumentach. Wykorzystując`Search` metoda`Parser` class pozwala na efektywne wyszukiwanie odpowiednich fragmentów tekstu na podstawie określonych wyszukiwanych haseł.

## Często zadawane pytania
### Czy GroupDocs.Parser jest kompatybilny z różnymi formatami dokumentów?
Tak, GroupDocs.Parser obsługuje szeroką gamę formatów plików, w tym PDF, DOCX, XLSX, PPTX i inne.
### Czy mogę wykonywać zaawansowane operacje wyodrębniania tekstu przy użyciu GroupDocs.Parser?
Absolutnie! Oprócz wyszukiwania tekstu GroupDocs.Parser umożliwia wyodrębnianie metadanych, wyodrębnianie tekstu strukturalnego i nie tylko.
### Gdzie mogę znaleźć szczegółową dokumentację GroupDocs.Parser?
Zapoznaj się z pełną dokumentacją[Tutaj](https://tutorials.groupdocs.com/parser/net/).
### Jak mogę uzyskać pomoc dotyczącą zapytań związanych z GroupDocs.Parser?
 Odwiedź forum GroupDocs, aby uzyskać pomoc i dyskusje[Tutaj](https://forum.groupdocs.com/c/parser/17).
### Czy dostępna jest wersja próbna umożliwiająca przetestowanie programu GroupDocs.Parser przed zakupem?
 Tak, możesz uzyskać dostęp do bezpłatnego okresu próbnego[Tutaj](https://releases.groupdocs.com/).