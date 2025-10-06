---
title: Wyodrębnij tekst ze strony w trybie surowym
linktitle: Wyodrębnij tekst ze strony w trybie surowym
second_title: GroupDocs.Parser API .NET
description: W tym kompleksowym samouczku naucz się wydajnego wyodrębniania tekstu ze stron dokumentów za pomocą Groupdocs.Parser dla .NET.
weight: 17
url: /pl/net/text-extraction/extract-text-from-page-in-raw-mode/
type: docs
---
# Wyodrębnij tekst ze strony w trybie surowym

## Wstęp
W tym samouczku dowiesz się, jak używać Groupdocs.Parser dla .NET do wyodrębniania tekstu ze stron dokumentów w trybie nieprzetworzonym. Ta biblioteka zapewnia wydajne narzędzia do analizowania i wyodrębniania zawartości z różnych formatów plików, umożliwiając programistom włączenie wyodrębniania tekstu dokumentu do swoich aplikacji .NET.
## Warunki wstępne
Zanim zaczniesz, upewnij się, że masz następujące wymagania wstępne:
- Podstawowa znajomość programowania w C# i .NET
- Program Visual Studio zainstalowany na Twoim komputerze
- Dostęp do biblioteki Groupdocs.Parser for .NET
- Przykładowy plik dokumentu do testów

## Importuj przestrzenie nazw
Zacznij od uwzględnienia niezbędnych przestrzeni nazw w projekcie C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Zainicjuj analizator składni
 Najpierw utwórz instancję`Parser` class, podając ścieżkę do przykładowego pliku dokumentu.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Twój kod tutaj
}
```
## Krok 2: Pobierz informacje o dokumencie
 Pobierz informacje o dokumencie za pomocą`GetDocumentInfo()` metoda.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Krok 3: Iteruj po stronach i wyodrębnij tekst
Iteruj po każdej stronie dokumentu i wyodrębnij treść tekstową.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Wyodrębnij tekst ze strony
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Wniosek
Nauczyłeś się już, jak używać programu Groupdocs.Parser dla platformy .NET do wyodrębniania tekstu ze stron dokumentów w trybie nieprzetworzonym. Może to być zaawansowana funkcja w przypadku aplikacji, które muszą analizować lub przetwarzać treść tekstową z różnych formatów plików.

## Często zadawane pytania
### Czy Groupdocs.Parser dla .NET jest kompatybilny ze wszystkimi formatami plików?
Groupdocs.Parser obsługuje szeroką gamę formatów plików, w tym PDF, DOCX, XLSX, PPTX, EPUB i inne.
### Czy za pomocą tej biblioteki mogę wyodrębnić metadane wraz z tekstem?
Tak, Groupdocs.Parser umożliwia wyodrębnianie tekstu i metadanych z dokumentów.
### Czy dostępna jest wersja próbna do przetestowania?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc techniczną dla Groupdocs.Parser?
 Aby uzyskać pomoc techniczną, odwiedź stronę[Forum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Gdzie mogę kupić licencję na Groupdocs.Parser dla .NET?
 Możesz kupić licencję[Tutaj](https://purchase.groupdocs.com/buy).