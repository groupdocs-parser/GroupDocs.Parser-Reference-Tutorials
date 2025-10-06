---
title: Wyodrębnij tekst ze strony w formacie PDF w trybie surowym
linktitle: Wyodrębnij tekst ze strony w formacie PDF w trybie surowym
second_title: GroupDocs.Parser API .NET
description: Wyodrębnij tekst z plików PDF za pomocą GroupDocs.Parser w języku C#. Naucz się wydajnej ekstrakcji tekstu PDF dzięki tej potężnej bibliotece .NET.
weight: 16
url: /pl/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
type: docs
---
# Wyodrębnij tekst ze strony w formacie PDF w trybie surowym

## Wstęp
W tym samouczku omówimy, jak używać programu GroupDocs.Parser dla platformy .NET do wyodrębniania tekstu ze stron dokumentów PDF w trybie nieprzetworzonym. GroupDocs.Parser to potężne narzędzie umożliwiające programistom programową pracę z różnymi formatami dokumentów.
## Warunki wstępne
Przed rozpoczęciem tego samouczka upewnij się, że posiadasz następujące elementy:
- Program Visual Studio zainstalowany na Twoim komputerze.
- Podstawowa znajomość programowania w języku C#.
- Biblioteka GroupDocs.Parser dla .NET, którą możesz[Pobierz tutaj](https://releases.groupdocs.com/parser/net/).
- Przykładowy plik PDF do celów testowych.

## Importuj przestrzenie nazw
Najpierw pamiętaj o zaimportowaniu niezbędnych przestrzeni nazw do projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Aby rozpocząć, utwórz instancję`Parser`class, podając ścieżkę do przykładowego pliku PDF.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Twój kod trafia tutaj
}
```
## Krok 2: Uzyskaj informacje o dokumencie i przeglądaj strony
Następnie pobierz informacje o dokumencie i wykonaj iterację po każdej stronie, aby wyodrębnić tekst.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Twój kod do wyodrębniania tekstu znajduje się tutaj
}
```
## Krok 3: Wyodrębnij tekst z każdej strony
 W pętli użyj metody`GetText` metoda wyodrębniania tekstu z każdej strony i drukowania go.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Wniosek
 W tym samouczku nauczyliśmy się, jak wyodrębniać tekst ze stron PDF w trybie nieprzetworzonym przy użyciu narzędzia GroupDocs.Parser dla platformy .NET. Proces ten polega na utworzeniu`Parser` na przykład uzyskiwanie informacji o dokumencie, przeglądanie każdej strony i wyodrębnianie tekstu za pomocą metody`GetText` metoda.

## Często zadawane pytania
### Co to jest GroupDocs.Parser dla .NET?
GroupDocs.Parser dla .NET to interfejs API do analizowania dokumentów, który umożliwia programistom programowe wyodrębnianie tekstu, metadanych i innych informacji z różnych formatów plików.
### Jak pobrać GroupDocs.Parser dla .NET?
 Bibliotekę można pobrać ze strony[Witryna GroupDocs](https://releases.groupdocs.com/parser/net/).
### Czy dostępny jest bezpłatny okres próbny?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Parser dla .NET z[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć pomoc dotyczącą GroupDocs.Parser dla .NET?
 Aby uzyskać pomoc techniczną i wsparcie społeczności, odwiedź stronę[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Jak mogę kupić licencję na GroupDocs.Parser dla .NET?
 Licencję można kupić w witrynie[strona zakupu](https://purchase.groupdocs.com/buy) lub zdobądź licencję tymczasową[Tutaj](https://purchase.groupdocs.com/temporary-license/).