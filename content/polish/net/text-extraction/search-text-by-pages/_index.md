---
title: Wyszukaj tekst według stron
linktitle: Wyszukaj tekst według stron
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyszukiwać tekst według stron przy użyciu GroupDocs.Parser dla .NET. Wydajnie wyodrębniaj określoną treść z dokumentów w aplikacjach .NET.
weight: 22
url: /pl/net/text-extraction/search-text-by-pages/
---
## Wstęp
W świecie programowania .NET wydajne analizowanie i wyodrębnianie tekstu z dokumentów jest kluczowym zadaniem. GroupDocs.Parser dla .NET oferuje zaawansowane możliwości pracy z różnymi formatami dokumentów, umożliwiając programistom płynne wyszukiwanie i wyodrębnianie określonej zawartości. Ten samouczek poprowadzi Cię przez proces wykorzystania GroupDocs.Parser do wyszukiwania tekstu według stron w aplikacjach .NET.
## Warunki wstępne
Zanim zagłębisz się w ten samouczek, upewnij się, że spełniasz następujące wymagania wstępne:
- Podstawowa znajomość C# i frameworku .NET
- Program Visual Studio zainstalowany w systemie
-  Zainstalowana biblioteka GroupDocs.Parser for .NET (pobierz z[Tutaj](https://releases.groupdocs.com/parser/net/))
- Przykładowe pliki do testowania funkcji wyszukiwania
## Importuj przestrzenie nazw
Po pierwsze, uwzględnij w projekcie niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Rozpocznij od utworzenia instancji`Parser` class ze ścieżką do przykładowego pliku:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Twój kod trafia tutaj
}
```
## Krok 2: Wyszukaj tekst za pomocą numerów stron
 Skorzystaj z`Search` metoda wyszukiwania określonych słów kluczowych w dokumencie wraz z numerami stron:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## Krok 3: Sprawdź wsparcie wyszukiwania
Sprawdź, czy operacja wyszukiwania jest obsługiwana dla typu dokumentu:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## Krok 4: Iteruj po wynikach wyszukiwania
Iteruj po wynikach wyszukiwania, aby pobrać zaindeksowane pozycje, numery stron i znaleziony tekst:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## Wniosek
W tym samouczku omówiliśmy, jak zaimplementować wyszukiwanie tekstu według stron przy użyciu programu GroupDocs.Parser dla platformy .NET. Wykonując poniższe kroki, możesz skutecznie zintegrować funkcje analizowania i wyszukiwania dokumentów z aplikacjami .NET.

## Często zadawane pytania
### Czy GroupDocs.Parser jest kompatybilny z różnymi formatami dokumentów?
Tak, GroupDocs.Parser obsługuje szeroką gamę formatów dokumentów, w tym DOCX, PDF, XLSX, PPTX i inne.
### Czy mogę wyodrębnić obrazy i metadane z dokumentów za pomocą GroupDocs.Parser?
Absolutnie GroupDocs.Parser umożliwia wyodrębnianie obrazów, metadanych i tekstu z dokumentów.
### Gdzie mogę znaleźć szczegółową dokumentację GroupDocs.Parser?
 Można uzyskać dostęp do dokumentacji[Tutaj](https://tutorials.groupdocs.com/parser/net/).
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Parser?
 Możesz poprosić o licencję tymczasową[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę uzyskać pomoc dotyczącą GroupDocs.Parser?
 Aby uzyskać pomoc i dyskusje, odwiedź forum GroupDocs.Parser[Tutaj](https://forum.groupdocs.com/c/parser/17).