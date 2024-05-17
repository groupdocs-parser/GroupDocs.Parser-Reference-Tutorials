---
title: Wyszukaj tekst w dokumencie programu Word według słowa kluczowego
linktitle: Wyszukaj tekst w dokumencie programu Word według słowa kluczowego
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyszukiwać tekst w dokumentach programu Word przy użyciu narzędzia GroupDocs.Parser dla platformy .NET. Skutecznie wyodrębniaj określone słowa kluczowe.
type: docs
weight: 18
url: /pl/net/word-document-processing/search-text-in-word-document-by-keyword/
---
## Wstęp
W tym samouczku omówimy, jak używać GroupDocs.Parser dla platformy .NET do wyszukiwania określonego tekstu w dokumencie programu Word przy użyciu języka C#. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom wyodrębnianie tekstu i metadanych z różnych formatów dokumentów, w tym dokumentów programu Word.
## Warunki wstępne
Przed rozpoczęciem upewnij się, że spełnione są następujące wymagania wstępne:
1. Środowisko programistyczne: Zainstaluj Visual Studio lub inne kompatybilne IDE.
2.  Biblioteka GroupDocs.Parser: Pobierz i zainstaluj bibliotekę GroupDocs.Parser dla .NET z witryny[strona internetowa](https://releases.groupdocs.com/parser/net/).
3. Przykładowy dokument programu Word: Przygotuj przykładowy dokument programu Word do wykorzystania przy wyszukiwaniu tekstu.

## Importuj przestrzenie nazw
Rozpocznij od zaimportowania niezbędnych przestrzeni nazw do projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Najpierw utwórz instancję`Parser` class, przekazując ścieżkę do przykładowego dokumentu programu Word.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kod trafia tutaj
}
```
## Krok 2: Wyszukaj słowo kluczowe
 Następnie użyj`Search` metoda`Parser` class, aby wyszukać określone słowo kluczowe w dokumencie.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Zastępować`"keyword"` z tekstem, który chcesz wyszukać w dokumencie.
## Krok 3: Iteruj po wynikach wyszukiwania
 Iteruj po wynikach wyszukiwania, używając a`foreach` pętla, aby uzyskać dostęp do każdego z nich`SearchResult` obiekt.
```csharp
foreach (SearchResult result in searchResults)
{
    //Kod do obsługi każdego wyniku wyszukiwania
}
```
## Krok 4: Uzyskaj dostęp do szczegółów wyników wyszukiwania
 W pętli możesz uzyskać dostęp do pozycji i tekstu każdego wyniku wyszukiwania za pomocą`Position` I`Text` właściwości`SearchResult` obiekt.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Ten fragment kodu drukuje indeks (`Position`) i znaleziony tekst (`Text`) dla każdego wyniku wyszukiwania do konsoli.

## Wniosek
W tym samouczku nauczyłeś się używać programu GroupDocs.Parser dla platformy .NET do wyszukiwania określonego tekstu w dokumencie programu Word. Ta biblioteka zapewnia wygodny sposób programowego wyodrębniania i manipulowania zawartością z różnych formatów dokumentów.

## Często zadawane pytania
### Czy GroupDocs.Parser obsługuje inne formaty dokumentów niż Word?
Tak, GroupDocs.Parser obsługuje szeroką gamę formatów, w tym PDF, Excel, PowerPoint i inne.
### Czy GroupDocs.Parser jest zgodny z platformą .NET Core?
Tak, GroupDocs.Parser jest kompatybilny zarówno z .NET Framework, jak i .NET Core.
### Jak uzyskać tymczasową licencję na GroupDocs.Parser?
 Możesz poprosić o licencję tymczasową od[Strona zakupu GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę znaleźć dodatkową pomoc lub zadać pytania dotyczące GroupDocs.Parser?
 Odwiedzić[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) za wsparcie społeczności i dyskusje.
### Czy mogę bezpłatnie wypróbować GroupDocs.Parser przed zakupem?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Strona z wersjami GroupDocs](https://releases.groupdocs.com/).