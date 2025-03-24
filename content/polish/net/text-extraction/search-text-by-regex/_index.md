---
title: Wyszukaj tekst według wyrażenia regularnego (Regex)
linktitle: Wyszukaj tekst według wyrażenia regularnego (Regex)
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyszukiwać tekst przy użyciu wyrażeń regularnych w dokumentach przy użyciu GroupDocs.Parser dla .NET. Wyodrębnij konkretną treść bez wysiłku.
weight: 23
url: /pl/net/text-extraction/search-text-by-regex/
---
## Wstęp
W tym samouczku omówimy użycie narzędzia GroupDocs.Parser dla platformy .NET do wyszukiwania tekstu za pomocą wyrażeń regularnych (Regex) w dokumentach. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom wyodrębnianie tekstu i metadanych z różnych formatów plików, takich jak PDF, DOCX, XLSX i innych. Wyszukiwanie tekstu za pomocą wyrażeń regularnych jest szczególnie przydatne do skutecznego wyszukiwania wzorców lub określonej treści w dokumentach.
## Warunki wstępne
Zanim zagłębisz się w ten samouczek, upewnij się, że posiadasz następujące elementy:
1. Visual Studio: Zainstaluj Visual Studio IDE do programowania .NET.
2.  GroupDocs.Parser dla .NET: Pobierz i zainstaluj GroupDocs.Parser dla .NET z[Tutaj](https://releases.groupdocs.com/parser/net/).
3. Przykładowy plik: Przygotuj przykładowy dokument (PDF, DOCX itp.) w celu przetestowania funkcji wyszukiwania.

## Importuj przestrzenie nazw
Najpierw zacznij od dołączenia niezbędnych przestrzeni nazw do kodu C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Utwórz instancję`Parser` class, podając ścieżkę do przykładowego pliku:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kod trafia tutaj
}
```
 Zastępować`"YourSampleFile.pdf"` ze ścieżką do rzeczywistego pliku.
## Krok 2: Wyszukaj przy użyciu wyrażeń regularnych
Zdefiniuj i wykonaj wyszukiwanie przy użyciu wzorca wyrażenia regularnego. Na przykład, aby znaleźć ciągi liczbowe (np. liczby całkowite) w dokumencie:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 W tym przykładzie`[0-9]+` to wzorzec wyrażenia regularnego, który dopasowuje jedną lub więcej cyfr.
## Krok 3: Sprawdź wsparcie wyszukiwania
Sprawdź, czy operacja wyszukiwania jest obsługiwana dla typu dokumentu:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Krok 4: Iteruj po wynikach wyszukiwania
Iteruj po wynikach wyszukiwania i przetwarzaj każde dopasowanie:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Ta pętla wydrukuje pozycję i pasujący tekst znaleziony w dokumencie.

## Wniosek
Podsumowując, wykorzystanie GroupDocs.Parser dla .NET umożliwia wydajne wyszukiwanie tekstu przy użyciu wyrażeń regularnych w różnych formatach dokumentów. Postępując zgodnie z tym przewodnikiem, programiści mogą bezproblemowo zintegrować analizowanie dokumentów i wyodrębnianie tekstu w oparciu o wyrażenia regularne ze swoimi aplikacjami .NET.

## Często zadawane pytania
### Czy GroupDocs.Parser może wyszukiwać w zaszyfrowanych dokumentach?
Nie, GroupDocs.Parser nie może przeszukiwać dokumentów zaszyfrowanych lub chronionych hasłem.
### Czy GroupDocs.Parser obsługuje OCR (optyczne rozpoznawanie znaków)?
Nie, GroupDocs.Parser nie wykonuje OCR. Polega na ekstrakcji tekstu z wewnętrznej struktury dokumentu.
### Czy mogę wyszukiwać złożone wzorce za pomocą wyrażeń regularnych?
Tak, GroupDocs.Parser obsługuje w pełni rozwinięte wyrażenia regularne, umożliwiając złożone dopasowywanie wzorców w dokumentach.
### Jakie formaty dokumentów są obsługiwane przy wyodrębnianiu tekstu?
GroupDocs.Parser obsługuje szeroką gamę formatów, w tym PDF, DOCX, XLSX, PPTX i inne.
### Czy GroupDocs.Parser jest zgodny z platformą .NET Core?
Tak, GroupDocs.Parser jest kompatybilny z .NET Core do programowania na wielu platformach.