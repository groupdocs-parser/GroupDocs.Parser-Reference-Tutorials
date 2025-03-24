---
title: Wyodrębnij kody kreskowe z dokumentu za pomocą opcji
linktitle: Wyodrębnij kody kreskowe z dokumentu za pomocą opcji
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić kody kreskowe z dokumentów za pomocą GroupDocs.Parser dla .NET. Obszerny samouczek z przykładami kodu i często zadawanymi pytaniami.
weight: 14
url: /pl/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## Wstęp
W tym samouczku omówimy proces wyodrębniania kodów kreskowych z dokumentu za pomocą programu GroupDocs.Parser dla platformy .NET. GroupDocs.Parser to potężna biblioteka, która umożliwia wyodrębnianie tekstu, metadanych i kodów kreskowych z różnych formatów dokumentów, takich jak PDF, Microsoft Word, Excel i innych.
## Warunki wstępne
Zanim zaczniesz, upewnij się, że spełnione są następujące wymagania wstępne:
1. Środowisko programistyczne: Upewnij się, że na komputerze jest zainstalowany program Visual Studio.
2.  Biblioteka GroupDocs.Parser: Pobierz i zainstaluj bibliotekę GroupDocs.Parser dla .NET ze strony[Tutaj](https://releases.groupdocs.com/parser/net/).
3. Przykładowy dokument: Przygotuj przykładowy dokument (np. PDF, DOCX) zawierający kody kreskowe do wyodrębnienia.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do projektu C#, aby móc korzystać z funkcjonalności GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Aby rozpocząć, utwórz instancję pliku`Parser` class, przekazując ścieżkę do przykładowego dokumentu.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kod do dodania w kolejnych krokach
}
```
## Krok 2: Sprawdź obsługę ekstrakcji kodów kreskowych
 Następnie sprawdź, czy dokument obsługuje ekstrakcję kodów kreskowych za pomocą`Features` własność`Parser` instancja.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Krok 3: Zdefiniuj opcje wyodrębniania kodów kreskowych
 Teraz określ opcje ekstrakcji kodów kreskowych za pomocą`BarcodeOptions`. Można ustawić parametry, takie jak tryby jakości i typy kodów kreskowych.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Krok 4: Wyodrębnij kody kreskowe z dokumentu
 Użyj`GetBarcodes` metoda`Parser` class do wyodrębniania kodów kreskowych na podstawie zdefiniowanych opcji.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Krok 5: Iteruj i wyświetl wyodrębnione kody kreskowe
Na koniec wykonaj iterację po wyodrębnionych kodach kreskowych i wyświetl ich indeks strony oraz wartości.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Wniosek
 W tym samouczku nauczyliśmy się wyodrębniać kody kreskowe z dokumentu za pomocą programu GroupDocs.Parser dla platformy .NET. Proces ten polega na utworzeniu`Parser` przykład, definiując opcje ekstrakcji i iterując po wyodrębnionych kodach kreskowych. GroupDocs.Parser upraszcza zadanie wyodrębniania kodów kreskowych z różnych formatów dokumentów, umożliwiając wydajne przetwarzanie dokumentów w aplikacjach .NET.

## Często zadawane pytania
### Czy GroupDocs.Parser może wyodrębniać kody kreskowe z dokumentów PDF?
Tak, GroupDocs.Parser obsługuje wyodrębnianie kodów kreskowych z dokumentów PDF oraz innych formatów, takich jak DOCX, XLSX itp.
### Jakie typy kodów kreskowych obsługuje GroupDocs.Parser?
GroupDocs.Parser obsługuje różne typy kodów kreskowych, w tym kody QR, Code 39, Code 128 i inne.
### Czy GroupDocs.Parser wymaga licencji do użytku komercyjnego?
 Tak, do użytku komercyjnego wymagana jest ważna licencja. Licencję można uzyskać od[Tutaj](https://purchase.groupdocs.com/buy).
### Czy GroupDocs.Parser nadaje się do wsadowego przetwarzania dokumentów?
Tak, GroupDocs.Parser może wydajnie obsługiwać wsadowe przetwarzanie dokumentów w celu wyodrębniania tekstu, pobierania metadanych i ekstrakcji kodów kreskowych.
### Gdzie mogę znaleźć pomoc techniczną dotyczącą GroupDocs.Parser?
 Możesz uzyskać pomoc techniczną lub zadać pytania na stronie[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17).