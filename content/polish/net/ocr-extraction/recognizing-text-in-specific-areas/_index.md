---
title: Rozpoznawanie tekstu w określonych obszarach
linktitle: Rozpoznawanie tekstu w określonych obszarach
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak używać programu GroupDocs.Parser dla platformy .NET do wyodrębniania tekstu z określonych obszarów dokumentów za pomocą funkcji OCR.
type: docs
weight: 13
url: /pl/net/ocr-extraction/recognizing-text-in-specific-areas/
---
## Wstęp
W tym samouczku omówimy, jak używać GroupDocs.Parser dla .NET do rozpoznawania i wyodrębniania tekstu z określonych obszarów dokumentu. GroupDocs.Parser to potężna biblioteka do analizowania dokumentów, która umożliwia programistom pracę z różnymi formatami dokumentów, w tym PDF, Word, Excel, PowerPoint i innymi. W szczególności skupimy się na wykorzystaniu możliwości OCR (optycznego rozpoznawania znaków) programu GroupDocs.Parser w celu wyodrębnienia tekstu ze zdefiniowanych obszarów dokumentu.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz skonfigurowane następujące wymagania wstępne:
1. Visual Studio IDE: Upewnij się, że masz zainstalowany program Visual Studio na swoim komputerze.
2.  GroupDocs.Parser dla .NET: Pobierz i zainstaluj GroupDocs.Parser dla .NET z[link do pobrania](https://releases.groupdocs.com/parser/net/).
3. Próbki dokumentów: Przygotuj przykładowe pliki (np. PDF, DOCX), z których chcesz wyodrębnić tekst.

## Importuj przestrzenie nazw
Aby rozpocząć, zaimportuj niezbędne przestrzenie nazw do swojego projektu:
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

Podzielmy proces na szczegółowe kroki, korzystając z GroupDocs.Parser dla .NET:
## Krok 1: Utwórz ustawienia analizatora składni za pomocą złącza OCR
 Najpierw utwórz instancję`ParserSettings`class i zainicjuj ją za pomocą złącza OCR, takiego jak`AsposeOcrOnPremise`:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Krok 2: Utwórz instancję analizatora składni z ustawieniami
 Następnie utwórz instancję`Parser` klasę, przekazując wcześniej utworzoną`ParserSettings`:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Fragment kodu ciąg dalszy...
}
```
 Zastępować`"YourSampleFile.pdf"` ze ścieżką do dokumentu docelowego.
## Krok 3: Skonfiguruj opcje wyodrębniania obszaru tekstowego
 Utwórz instancję`PageTextAreaOptions` aby włączyć wyodrębnianie tekstu w oparciu o OCR:
```csharp
PageTextAreaOptions options = new PageTextAreaOptions(true);
```
 Ustawić`true` aby włączyć OCR w celu lepszego rozpoznawania tekstu.
## Krok 4: Wyodrębnij obszary tekstowe
 Odwołać się`parser.GetTextAreas(options)` aby wyodrębnić obszary tekstowe z dokumentu:
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Krok 5: Przetwórz wyodrębnione obszary tekstowe
Iteruj po wyodrębnionych obszarach tekstowych i pobieraj informacje o tekście, położeniu i rozmiarze:
```csharp
foreach (PageTextArea area in areas)
{
    Console.WriteLine(area.Text);
    Console.WriteLine($"\tPosition: ({area.Rectangle.Left}; {area.Rectangle.Top})");
    Console.WriteLine($"\tSize: ({area.Rectangle.Size.Width}; {area.Rectangle.Size.Height})");
}
```

## Wniosek
W tym samouczku omówiliśmy proces wyodrębniania tekstu z określonych obszarów dokumentu przy użyciu narzędzia GroupDocs.Parser dla platformy .NET z funkcjami OCR. Wykonując poniższe kroki, można skutecznie wykorzystać funkcje analizowania programu GroupDocs.Parser do programowej obsługi zadań wyodrębniania tekstu.

## Często zadawane pytania
### Czy GroupDocs.Parser może wyodrębnić tekst ze zeskanowanych dokumentów?
Tak, GroupDocs.Parser obsługuje OCR w celu wyodrębnienia tekstu z zeskanowanych obrazów w dokumentach.
### Jakie formaty dokumentów są obsługiwane przez GroupDocs.Parser?
GroupDocs.Parser obsługuje szeroką gamę formatów, w tym PDF, DOCX, XLSX, PPTX, TXT i inne.
### Czy GroupDocs.Parser nadaje się do wsadowego przetwarzania dokumentów?
Tak, GroupDocs.Parser może wydajnie obsługiwać zadania przetwarzania wsadowego w celu analizowania i wyodrębniania dokumentów.
### Czy mogę dostosować opcje wyodrębniania tekstu za pomocą GroupDocs.Parser?
Tak, GroupDocs.Parser oferuje różne opcje dostosowywania wyodrębniania tekstu w oparciu o określone wymagania.
### Czy GroupDocs.Parser zapewnia obsługę wyodrębniania metadanych z dokumentów?
Tak, GroupDocs.Parser umożliwia wyodrębnianie metadanych, takich jak autor, data utworzenia i inne, z obsługiwanych formatów dokumentów.