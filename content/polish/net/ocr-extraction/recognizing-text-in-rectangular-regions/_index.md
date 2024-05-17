---
title: Rozpoznawanie tekstu w obszarach prostokątnych
linktitle: Rozpoznawanie tekstu w obszarach prostokątnych
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak rozpoznawać tekst w określonych obszarach dokumentów za pomocą GroupDocs.Parser dla .NET z funkcjami OCR.
type: docs
weight: 14
url: /pl/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## Wstęp
W tym samouczku omówimy, jak używać programu GroupDocs.Parser dla platformy .NET do rozpoznawania tekstu w określonych prostokątnych obszarach dokumentów. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom wyodrębnianie tekstu, metadanych i innych danych z różnych formatów plików, w tym PDF, Word, Excel i PowerPoint.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następującą konfigurację:
-  GroupDocs.Parser dla .NET: Pobierz i zainstaluj bibliotekę z[Tutaj](https://releases.groupdocs.com/parser/net/).
- Środowisko programistyczne: Visual Studio lub dowolne inne środowisko .NET IDE.
- Przykładowy dokument: Przygotuj przykładowy plik (np. PDF, DOCX) zawierający tekst do rozpoznania.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego kodu C#:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Zainicjuj ustawienia analizatora składni
 Rozpocznij od skonfigurowania`ParserSettings` ze złączem OCR. Tutaj użyjemy lokalnego łącznika Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Krok 2: Utwórz instancję analizatora składni
 Następnie utwórz instancję`Parser` class z wcześniej zdefiniowanymi ustawieniami:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Kod jest kontynuowany tutaj
}
```
 Zastępować`"YourSampleFile.pdf"` ze ścieżką do dokumentu.
## Krok 3: Zdefiniuj prostokąt OCR
 Zdefiniuj prostokąt w dokumencie, w którym będzie wykonywane rozpoznawanie tekstu. Na przykład prostokąt zaczynający się od`(0, 0)` z szerokością`400` i wysokość`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Krok 4: Skonfiguruj opcje rozpoznawania tekstu
 Tworzyć`TextOptions` aby określić użycie OCR wraz ze zdefiniowanym prostokątem:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Krok 5: Wyodrębnij tekst za pomocą OCR
 Użyj`GetText` metoda`Parser` instancja ze skonfigurowanym`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Przeczytaj wyodrębniony tekst lub obsłuż przypadek „nieobsługiwany”.
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Wniosek
tym samouczku zademonstrowaliśmy, jak wykorzystać GroupDocs.Parser dla .NET do wyodrębnienia tekstu z określonych prostokątnych regionów w dokumentach przy użyciu OCR. Proces ten można dodatkowo dostosować i zintegrować z różnymi aplikacjami w celu zautomatyzowanego wyodrębniania tekstu.

## Często zadawane pytania
### Czy GroupDocs.Parser może wyodrębnić tekst ze zeskanowanych dokumentów?
Tak, GroupDocs.Parser obsługuje OCR (optyczne rozpoznawanie znaków) w celu wyodrębniania tekstu z zeskanowanych dokumentów.
### Jakie formaty plików obsługuje GroupDocs.Parser?
GroupDocs.Parser obsługuje szeroką gamę formatów plików, w tym PDF, DOCX, XLSX, PPTX i inne.
### Jak mogę obsługiwać dokumenty, które nie są obsługiwane w przypadku wyodrębniania tekstu?
 Możesz sprawdzić, czy ekstrakcja tekstu jest obsługiwana za pomocą`TextReader` instancja zwrócona przez`parser.GetText(options)`.
### Czy GroupDocs.Parser nadaje się do zadań wyodrębniania tekstu na dużą skalę?
Tak, GroupDocs.Parser został zaprojektowany do wydajnej obsługi zadań wyodrębniania tekstu na dużą skalę.
### Gdzie mogę uzyskać pomoc dotyczącą problemów związanych z GroupDocs.Parser?
 Aby uzyskać wsparcie i dyskusje, odwiedź stronę[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).