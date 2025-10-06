---
title: Wyodrębnij sformatowany tekst ze strony dokumentu
linktitle: Wyodrębnij sformatowany tekst ze strony dokumentu
second_title: GroupDocs.Parser API .NET
description: Wyodrębnij sformatowany tekst ze stron dokumentu za pomocą GroupDocs.Parser dla .NET. Wydajne i niezawodne rozwiązanie do ekstrakcji tekstu.
weight: 11
url: /pl/net/formatted-text-extraction/extract-formatted-text-from-document-page/
type: docs
---
# Wyodrębnij sformatowany tekst ze strony dokumentu

## Wstęp
W tym samouczku przeprowadzimy Cię przez proces wyodrębniania sformatowanego tekstu ze stron dokumentu za pomocą GroupDocs.Parser dla .NET. Ta biblioteka umożliwia wydajne analizowanie i wyodrębnianie tekstu z różnych formatów dokumentów, takich jak PDF, Word, Excel i innych.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
- Program Visual Studio zainstalowany w systemie.
- Podstawowa znajomość programowania w języku C#.
-  Biblioteka GroupDocs.Parser dla .NET. Możesz go pobrać[Tutaj](https://releases.groupdocs.com/parser/net/).

## Importuj przestrzenie nazw
Najpierw zacznij od zaimportowania niezbędnych przestrzeni nazw do projektu C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Rozpocznij od utworzenia instancji`Parser` class, podając ścieżkę do przykładowego pliku.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kod trafi tutaj
}
```
## Krok 2: Sprawdź, czy obsługiwana jest ekstrakcja sformatowanego tekstu
Przed przystąpieniem do wyodrębniania tekstu sprawdź, czy dokument obsługuje wyodrębnianie tekstu w formacie.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Krok 3: Uzyskaj informacje o dokumencie
Pobierz informacje o dokumencie, takie jak liczba stron.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Krok 4: Iteruj po stronach dokumentu i wyodrębnij sformatowany tekst
Iteruj po każdej stronie dokumentu i wyodrębnij sformatowany tekst, korzystając z określonych opcji (np. format Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Wniosek
Teraz wiesz, jak wyodrębnić sformatowany tekst ze stron dokumentu za pomocą GroupDocs.Parser dla .NET. Ta biblioteka zapewnia wydajne i łatwe w użyciu rozwiązanie do wyodrębniania tekstu z różnych formatów plików.

## Często zadawane pytania
### Czy GroupDocs.Parser obsługuje różne formaty plików?
Tak, GroupDocs.Parser obsługuje szeroką gamę formatów dokumentów, w tym PDF, DOCX, XLSX, PPTX i inne.
### Czy GroupDocs.Parser jest zgodny z platformą .NET Core?
Tak, GroupDocs.Parser obsługuje .NET Core i .NET Framework.
### Czy GroupDocs.Parser zachowuje formatowanie tekstu podczas wyodrębniania?
Tak, GroupDocs.Parser może podczas wyodrębniania tekstu zachować formatowanie, takie jak style i czcionki.
### Czy mogę wyodrębnić obrazy i metadane za pomocą GroupDocs.Parser?
Tak, GroupDocs.Parser umożliwia wyodrębnianie obrazów, metadanych i tekstu z dokumentów.
### Jak mogę uzyskać pomoc dotyczącą GroupDocs.Parser?
 Możesz uzyskać wsparcie od[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).