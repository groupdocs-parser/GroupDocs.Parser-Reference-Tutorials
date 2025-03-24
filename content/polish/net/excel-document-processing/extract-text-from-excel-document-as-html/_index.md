---
title: Wyodrębnij tekst z dokumentu Excel jako HTML
linktitle: Wyodrębnij tekst z dokumentu Excel jako HTML
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić tekst z dokumentów Excel i przekonwertować go na format HTML za pomocą GroupDocs.Parser dla .NET.
weight: 13
url: /pl/net/excel-document-processing/extract-text-from-excel-document-as-html/
---

# Wyodrębnij tekst z dokumentu Excel jako HTML

## Wstęp
W tym samouczku omówimy, jak używać narzędzia GroupDocs.Parser dla platformy .NET do wyodrębniania tekstu z dokumentu programu Excel i konwertowania go do formatu HTML. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom pracę z różnymi formatami dokumentów, efektywnie wyodrębniając tekst i metadane.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następującą konfigurację:
- Program Visual Studio zainstalowany w systemie.
- Podstawowa znajomość programowania w języku C#.
-  Biblioteka GroupDocs.Parser dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/parser/net/).
## Importuj przestrzenie nazw
Zacznij od dołączenia niezbędnych przestrzeni nazw do projektu C#, aby uzyskać dostęp do funkcji GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Najpierw utwórz instancję`Parser` class, podając ścieżkę do dokumentu Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Dalszy kod będzie tutaj
}
```
 Zastępować`"YourSampleFile.xlsx"` ze ścieżką do pliku Excel.
## Krok 2: Wyodrębnij tekst jako HTML
 W ramach`using` blok`Parser` na przykład użyj`GetFormattedText` metoda wyodrębniania sformatowanego tekstu w trybie HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Dalszy kod będzie tutaj
    }
}
```
## Krok 3: Przeczytaj i wydrukuj wyodrębniony tekst HTML
 Następnie przeczytaj wyodrębniony tekst HTML z pliku`TextReader` i wydrukuj go na konsoli.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Po wykonaniu ten kod wyodrębni tekst z dokumentu Excel i wyświetli go w konsoli w formacie HTML.
## Wniosek
W tym samouczku nauczyliśmy się, jak używać GroupDocs.Parser dla .NET do wyodrębniania tekstu z dokumentu Excel i konwertowania go do formatu HTML. Ta biblioteka zapewnia prosty sposób pracy z różnymi formatami dokumentów, umożliwiając programistom efektywną obsługę zadań wyodrębniania tekstu w ich aplikacjach.

## Często zadawane pytania
### Czy GroupDocs.Parser obsługuje inne formaty dokumentów oprócz Excela?
Tak, GroupDocs.Parser obsługuje szeroką gamę formatów plików, w tym PDF, Word, PowerPoint i inne.
### Czy GroupDocs.Parser jest zgodny z platformą .NET Core?
Tak, GroupDocs.Parser jest kompatybilny zarówno z .NET Framework, jak i .NET Core.
### Czy GroupDocs.Parser zachowuje formatowanie podczas wyodrębniania tekstu?
Tak, GroupDocs.Parser może zachować formatowanie, takie jak czcionki, style i układ, podczas wyodrębniania tekstu.
### Czy mogę wyodrębnić metadane z dokumentów za pomocą GroupDocs.Parser?
Tak, GroupDocs.Parser umożliwia wyodrębnianie metadanych, takich jak autor, data utworzenia i inne, z obsługiwanych typów dokumentów.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Parser?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).