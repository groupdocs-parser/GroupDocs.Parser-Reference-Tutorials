---
title: Wyodrębnij hiperłącza ze strony dokumentu
linktitle: Wyodrębnij hiperłącza ze strony dokumentu
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić hiperłącza z dokumentów za pomocą GroupDocs.Parser dla .NET. Przewodnik krok po kroku dotyczący wyodrębniania hiperłączy w języku C#.
weight: 11
url: /pl/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Wstęp
W tym samouczku pokażemy, jak krok po kroku używać programu GroupDocs.Parser dla platformy .NET do wyodrębniania hiperłączy z dokumentów. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom analizowanie różnych formatów dokumentów i wyodrębnianie tekstu, metadanych i innych elementów.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
- Visual Studio: Zainstaluj program Visual Studio na komputerze programistycznym.
-  Biblioteka GroupDocs.Parser: pobierz bibliotekę GroupDocs.Parser i korzystaj z niej. Możesz to dostać od[Tutaj](https://releases.groupdocs.com/parser/net/).
- Przykładowy dokument: Przygotuj przykładowy dokument (np. DOCX, PDF) zawierający hiperłącza do testów.

## Importuj przestrzenie nazw
Najpierw uwzględnij niezbędne przestrzenie nazw, aby móc korzystać z funkcjonalności GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję analizatora składni
 Utwórz instancję`Parser` class ze ścieżką do przykładowego dokumentu.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kod trafia tutaj...
}
```
## Krok 2: Sprawdź obsługę wyodrębniania hiperłączy
Przed kontynuowaniem upewnij się, że dokument obsługuje wyodrębnianie hiperłączy.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Krok 3: Pobierz informacje o dokumencie
Uzyskaj podstawowe informacje o dokumencie i sprawdź, czy zawiera strony.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Krok 4: Iteruj po stronach dokumentu
Iteruj po każdej stronie dokumentu.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Wyodrębnij hiperłącza z bieżącej strony
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Iteruj po wyodrębnionych hiperłączach
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Pusta linia dla czytelności
    }
}
```

## Wniosek
W tym samouczku omówiliśmy podstawy używania programu GroupDocs.Parser dla platformy .NET do wyodrębniania hiperłączy z dokumentów. Nauczyłeś się, jak inicjować analizator składni, sprawdzać obsługę hiperłączy, pobierać informacje o dokumencie i przeglądać strony dokumentu w celu wydajnego wyodrębniania hiperłączy.

## Często zadawane pytania
### Czy mogę wyodrębnić hiperłącza z różnych formatów dokumentów?
Tak, GroupDocs.Parser obsługuje różne formaty, takie jak DOCX, PDF, PPTX itp., w celu wyodrębnienia hiperłączy.
### Czy GroupDocs.Parser można łatwo zintegrować z istniejącymi aplikacjami .NET?
Absolutnie GroupDocs.Parser został zaprojektowany tak, aby był prosty i można go łatwo zintegrować z projektami .NET.
### Czy mogę wyodrębnić inne metadane wraz z hiperłączami za pomocą GroupDocs.Parser?
Tak, oprócz hiperłączy za pomocą tej biblioteki możesz wyodrębniać tekst, obrazy i metadane z dokumentów.
### Czy GroupDocs.Parser obsługuje dokumenty zaszyfrowane lub chronione hasłem?
GroupDocs.Parser może analizować dokumenty chronione hasłem, jeśli hasło zostanie podane.
### Czy dostępna jest wersja próbna, którą można przetestować przed zakupem?
 Tak, możesz pobrać bezpłatną wersję próbną[Tutaj](https://releases.groupdocs.com/).