---
title: Wyodrębnij hiperłącza z dokumentu
linktitle: Wyodrębnij hiperłącza z dokumentu
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić hiperłącza z dokumentów za pomocą GroupDocs.Parser dla .NET. Ulepsz swoje aplikacje w języku C# dzięki temu prostemu przewodnikowi.
weight: 10
url: /pl/net/hyperlink-extraction/extract-hyperlinks-from-document/
---

# Wyodrębnij hiperłącza z dokumentu

## Wstęp
W tym samouczku zagłębimy się w potężne możliwości GroupDocs.Parser dla .NET, wszechstronnej biblioteki, która pozwala programistom z łatwością wyodrębniać hiperłącza z dokumentów. Wyodrębnianie hiperłączy jest powszechnym wymogiem w przetwarzaniu dokumentów, szczególnie w przypadku plików tekstowych, takich jak pliki PDF lub dokumenty Word. Korzystając z GroupDocs.Parser, możesz skutecznie identyfikować i wyodrębniać hiperłącza wraz z powiązanymi z nimi adresami URL z różnych formatów dokumentów.
## Warunki wstępne
Przed kontynuowaniem tego samouczka upewnij się, że spełnione są następujące wymagania wstępne:
- Podstawowa znajomość programowania w języku C#
- Program Visual Studio zainstalowany w systemie
-  Biblioteka GroupDocs.Parser for .NET, którą można pobrać[Tutaj](https://releases.groupdocs.com/parser/net/)
## Importuj przestrzenie nazw
Aby rozpocząć, zaimportuj niezbędne przestrzenie nazw do projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```

Teraz podzielmy każdy przykład na wiele kroków, które poprowadzą Cię przez proces wyodrębniania hiperłączy za pomocą GroupDocs.Parser dla .NET:
## Krok 1: Utwórz instancję klasy analizatora składni
 Najpierw utwórz instancję`Parser` class, podając ścieżkę do przykładowego dokumentu:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Twój kod do wyodrębnienia hiperłącza zostanie umieszczony tutaj
}
```
 Zastępować`"YourSampleFile.docx"` ze ścieżką do dokumentu docelowego.
## Krok 2: Sprawdź obsługę wyodrębniania hiperłączy
Przed wyodrębnieniem hiperłączy ważne jest sprawdzenie, czy format dokumentu obsługuje wyodrębnianie hiperłączy:
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
Ten krok zapewnia możliwość wyodrębnienia hiperłącza dla danego dokumentu.
## Krok 3: Wyodrębnij hiperłącza
 Kontynuuj wyodrębnianie hiperłączy z dokumentu za pomocą`GetHyperlinks()` metoda:
```csharp
IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks();
```
 Ta linia pobiera kolekcję`PageHyperlinkArea` obiekty zawierające informacje o hiperłączach.
## Krok 4: Iteruj po wyodrębnionych hiperłączach
Iteruj po kolekcji wyodrębnionych hiperłączy i pobierz ich tekst i adres URL:
```csharp
foreach (PageHyperlinkArea hyperlink in hyperlinks)
{
    // Wydrukuj tekst hiperłącza
    Console.WriteLine(hyperlink.Text);
    
    // Wydrukuj adres URL hiperłącza
    Console.WriteLine(hyperlink.Url);
    Console.WriteLine(); // Dodaje pustą linię dla czytelności
}
```
Iterując po`hyperlinks` kolekcji, możesz uzyskać dostęp i wydrukować tekst i adres URL każdego hiperłącza.
## Wniosek
W tym samouczku omówiliśmy, jak wyodrębnić hiperłącza z dokumentów za pomocą programu GroupDocs.Parser dla platformy .NET. Wykorzystując funkcje udostępniane przez tę bibliotekę, programiści mogą bez wysiłku integrować funkcje ekstrakcji hiperłączy ze swoimi aplikacjami C#.

## Często zadawane pytania
### Czy GroupDocs.Parser obsługuje wyodrębnianie hiperłączy z różnych formatów dokumentów?
Tak, GroupDocs.Parser obsługuje wyodrębnianie hiperłączy z szerokiej gamy formatów plików, w tym PDF, Word, Excel, PowerPoint i innych.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Parser?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Parser[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć dokumentację GroupDocs.Parser?
 Szczegółową dokumentację GroupDocs.Parser można znaleźć[Tutaj](https://tutorials.groupdocs.com/parser/net/).
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Parser?
 Możesz uzyskać tymczasową licencję na GroupDocs.Parser[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Czy GroupDocs oferuje pomoc w rozwiązywaniu problemów?
 Tak, możesz szukać wsparcia i pomocy w rozwiązywaniu problemów w GroupDocs[forum](https://forum.groupdocs.com/c/parser/17).