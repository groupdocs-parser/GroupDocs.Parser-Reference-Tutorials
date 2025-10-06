---
title: Załaduj dokument z dysku lokalnego
linktitle: Załaduj dokument z dysku lokalnego
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić tekst z różnych formatów dokumentów za pomocą GroupDocs.Parser dla .NET. Łatwa i wydajna ekstrakcja tekstu za pomocą języka C#.
weight: 11
url: /pl/net/document-loading/load-document-from-local-disk/
type: docs
---
# Załaduj dokument z dysku lokalnego

## Wstęp
W tym samouczku omówimy, jak używać GroupDocs.Parser dla .NET do wyodrębniania tekstu z dokumentów. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom analizowanie różnych formatów dokumentów i programowe wyodrębnianie zawartości tekstowej. Omówimy kroki niezbędne do rozpoczęcia ekstrakcji tekstu przy użyciu tej biblioteki.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz zainstalowane następujące wymagania wstępne:
- Program Visual Studio zainstalowany w systemie.
- Podstawowa znajomość języka programowania C#.
-  Zainstalowana biblioteka GroupDocs.Parser for .NET (pobierz[Tutaj](https://releases.groupdocs.com/parser/net/)).

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Krok 1: Załaduj dokument z dysku lokalnego
 Rozpocznij od załadowania dokumentu z dysku lokalnego. Zastępować`"Your Sample File"` ze ścieżką do dokumentu docelowego.
```csharp
// Ustaw ścieżkę pliku
string filePath = "Your Sample File";
// Utwórz instancję klasy Parser z filePath
using (Parser parser = new Parser(filePath))
{
    // Wyodrębnij tekst do czytnika
    using (TextReader reader = parser.GetText())
    {
        //Wydrukuj wyodrębniony tekst z dokumentu
        // Jeśli wyodrębnianie tekstu nie jest obsługiwane, czytnik będzie miał wartość null
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Wyjaśnienie kroków
1. Ustawianie ścieżki pliku: Rozpocznij od określenia ścieżki do dokumentu, z którego chcesz wyodrębnić tekst (`filePath` zmienny).
2.  Tworzenie instancji analizatora składni: Utwórz instancję`Parser` klasę, przechodząc`filePath`.
3.  Wyodrębnianie tekstu: Użyj`GetText()` metoda`Parser` przykład, aby uzyskać`TextReader` obiekt zawierający wyodrębniony tekst z dokumentu.
4.  Czytanie wyodrębnionego tekstu: Wykorzystaj`ReadToEnd()` metoda`TextReader` aby pobrać całą zawartość tekstową wyodrębnioną z dokumentu.
5.  Obsługa nieobsługiwanych formatów: Jeśli format dokumentu nie obsługuje wyodrębniania tekstu, plik`reader` obiekt będzie`null`i możesz odpowiednio obsłużyć ten scenariusz.

## Wniosek
tym samouczku omówiliśmy początkowe kroki wyodrębniania tekstu z dokumentu przy użyciu programu GroupDocs.Parser dla platformy .NET. Biblioteka ta oferuje rozbudowane funkcje analizowania dokumentów, umożliwiając programistom wydajną pracę z różnymi formatami plików w ich aplikacjach.

## Często zadawane pytania
### Czy GroupDocs.Parser jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Parser obsługuje szeroką gamę formatów, w tym PDF, dokumenty Microsoft Office (Word, Excel, PowerPoint) i inne.
### Czy mogę wyodrębnić metadane wraz z tekstem za pomocą GroupDocs.Parser?
Tak, GroupDocs.Parser umożliwia wyodrębnianie zarówno treści tekstowych, jak i metadanych z obsługiwanych formatów dokumentów.
### Gdzie mogę znaleźć więcej zasobów i wsparcia dla GroupDocs.Parser?
 Odwiedzić[Dokumentacja GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) aby uzyskać szczegółowe informacje o interfejsie API i zapoznać się z[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17) za wsparcie społeczności.
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Parser?
 Możesz poprosić o[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/) do celów oceny i testowania.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Parser?
 Tak, możesz pobrać plik[bezpłatna wersja próbna](https://releases.groupdocs.com/) wersja GroupDocs.Parser.