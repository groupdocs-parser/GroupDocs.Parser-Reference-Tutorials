---
title: Wyodrębnij tekst z określonych obszarów za pomocą opcji
linktitle: Wyodrębnij tekst z określonych obszarów za pomocą opcji
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić tekst z określonych obszarów dokumentów za pomocą GroupDocs.Parser dla .NET. Poznaj zaawansowane opcje wyodrębniania tekstu dzięki temu samouczkowi.
weight: 14
url: /pl/net/text-extraction/extract-text-from-specific-areas-with-options/
type: docs
---
# Wyodrębnij tekst z określonych obszarów za pomocą opcji

## Wstęp
W tym samouczku omówimy, jak używać programu GroupDocs.Parser dla platformy .NET do wyodrębniania tekstu z określonych obszarów dokumentu przy użyciu konfigurowalnych opcji. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom bezproblemowe analizowanie i wyodrębnianie tekstu z dokumentów o różnych formatach.
## Warunki wstępne
Zanim zagłębimy się w kodowanie, upewnij się, że masz następujące elementy:
1. Środowisko programistyczne: Zainstaluj program Visual Studio lub dowolne inne środowisko programistyczne .NET.
2.  Biblioteka GroupDocs.Parser: Pobierz i zainstaluj GroupDocs.Parser dla .NET z[Tutaj](https://releases.groupdocs.com/parser/net/).
3. Przykładowy plik: Przygotuj przykładowy dokument (np. PDF, DOCX itp.), z którego chcesz wyodrębnić tekst.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do klas i metod GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Zainicjuj instancję`Parser` class, podając ścieżkę do przykładowego pliku.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Tutaj będzie umieszczony kod do wyodrębniania obszaru tekstowego
}
```
## Krok 2: Zdefiniuj opcje wyodrębniania obszaru tekstowego
 Tworzyć`PageTextAreaOptions` aby określić kryteria wyodrębniania tekstu.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
W tym przykładzie:
- `"\\s[a-z]{2}\\s"` to wzorzec wyrażenia regularnego dopasowujący obszary tekstowe zawierające wyłącznie małe litery.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` definiuje prostokąt (położenie i rozmiar) na stronie, z którego ma zostać wyodrębniony tekst.
## Krok 3: Wyodrębnij obszary tekstowe
Użyj zdefiniowanych opcji, aby wyodrębnić obszary tekstowe spełniające określone kryteria.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Krok 4: Sprawdź i wykonaj iterację po wyodrębnionych obszarach tekstowych
Sprawdź, czy obsługiwane jest wyodrębnianie obszarów tekstowych, a następnie wykonaj iterację po wyodrębnionych obszarach.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Wniosek
W tym samouczku omówiliśmy sposób wyodrębniania tekstu z określonych obszarów dokumentu za pomocą programu GroupDocs.Parser dla platformy .NET. Biblioteka ta oferuje szerokie możliwości analizowania różnych formatów dokumentów, co czyni ją cennym narzędziem do zadań wyodrębniania tekstu.

## Często zadawane pytania
### Czy GroupDocs.Parser może wyodrębnić tekst ze zeskanowanych dokumentów?
Tak, GroupDocs.Parser obsługuje wyodrębnianie tekstu zeskanowanych dokumentów w oparciu o OCR.
### Czy GroupDocs.Parser jest kompatybilny z wieloma formatami dokumentów?
Tak, może analizować i wyodrębniać tekst z plików PDF, DOCX, XLSX, PPTX i innych popularnych formatów.
### Czy GroupDocs.Parser zapewnia obsługę platformy .NET Core?
Tak, GroupDocs.Parser jest kompatybilny z .NET Core i .NET Framework.
### Czy mogę wyodrębnić metadane wraz z tekstem za pomocą GroupDocs.Parser?
Tak, możesz wyodrębnić z dokumentów zarówno treść tekstową, jak i metadane.
### Czy dostępna jest wersja próbna programu GroupDocs.Parser?
 Tak, możesz uzyskać bezpłatną wersję próbną od[Tutaj](https://releases.groupdocs.com/).