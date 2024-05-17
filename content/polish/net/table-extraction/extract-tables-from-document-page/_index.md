---
title: Wyodrębnij tabele ze strony dokumentu
linktitle: Wyodrębnij tabele ze strony dokumentu
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak programowo wyodrębniać tabele z dokumentów przy użyciu programu GroupDocs.Parser dla platformy .NET. Ten kompleksowy samouczek zawiera wskazówki krok po kroku.
type: docs
weight: 11
url: /pl/net/table-extraction/extract-tables-from-document-page/
---
## Wstęp
W tym samouczku przyjrzymy się, jak wyodrębnić tabele ze strony dokumentu za pomocą GroupDocs.Parser dla .NET. GroupDocs.Parser to potężna biblioteka, która umożliwia programistom pracę z różnymi formatami dokumentów, takimi jak PDF, DOCX, XLSX i innymi. Wykorzystując jego funkcje, możemy skutecznie wyodrębniać z dokumentów ustrukturyzowane dane, takie jak tabele, co pozwala nam programowo manipulować i analizować informacje.
## Warunki wstępne
Zanim zaczniesz, upewnij się, że masz następujące elementy:
- Program Visual Studio zainstalowany na Twoim komputerze.
- Podstawowa znajomość programowania w C# i .NET.
-  Biblioteka GroupDocs.Parser dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/parser/net/).
- Dostęp do przykładowego dokumentu (PDF, DOCX itp.) zawierającego tabele do wyodrębnienia.

## Importuj przestrzenie nazw
Najpierw zacznij od zaimportowania niezbędnych przestrzeni nazw do projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Utwórz instancję`Parser` class, podając ścieżkę do przykładowego dokumentu:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Twój kod jest kontynuowany tutaj...
}
```
## Krok 2: Sprawdź obsługę wyodrębniania tabeli dokumentów
Przed kontynuowaniem sprawdź, czy dokument obsługuje wyodrębnianie tabeli:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Krok 3: Zdefiniuj układ tabeli
Zdefiniuj układ tabel, które mają zostać wyodrębnione z dokumentu. Określ szerokość kolumn i wysokość wierszy zgodnie ze strukturą dokumentu:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Szerokości kolumn
    new double[] { 325, 340, 365, 395 });         // Wysokości rzędów
```
## Krok 4: Skonfiguruj opcje wyodrębniania tabeli
Utwórz opcje wyodrębniania tabeli przy użyciu określonego układu:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Krok 5: Pobierz informacje o dokumencie
Pobierz informacje o dokumencie, w tym liczbę stron:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Krok 6: Iteruj po stronach dokumentu
Iteruj po każdej stronie dokumentu, aby wyodrębnić tabele:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Wyodrębnij tabele z bieżącej strony
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Iteruj po wyodrębnionych tabelach
    foreach (PageTableArea table in tables)
    {
        // Iteruj po wierszach tabeli
        for (int row = 0; row < table.RowCount; row++)
        {
            // Iteruj po kolumnach tabeli
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Zdobądź komórkę tabeli
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Wydrukuj tekst komórki tabeli
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Wniosek
tym samouczku omówiliśmy proces wyodrębniania tabel ze stron dokumentów przy użyciu programu GroupDocs.Parser dla platformy .NET. Wykonując podane kroki, możesz bezproblemowo zintegrować funkcję wyodrębniania tabel z aplikacjami .NET, umożliwiając wydajną obsługę i manipulowanie danymi strukturalnymi w dokumentach.

## Często zadawane pytania
### Czy GroupDocs.Parser może wyodrębniać tabele ze wszystkich typów dokumentów?
GroupDocs.Parser obsługuje różne formaty dokumentów, takie jak PDF, DOCX, XLSX i inne, umożliwiając wyodrębnianie tabel z kompatybilnych typów plików.
### Czy GroupDocs.Parser dla .NET nadaje się do przetwarzania dokumentów na dużą skalę?
Tak, GroupDocs.Parser został zaprojektowany do wydajnej obsługi dużych dokumentów, dzięki czemu nadaje się do przetwarzania dużych zbiorów danych.
### Czy GroupDocs.Parser zachowuje formatowanie podczas wyodrębniania tabeli?
Tak, podczas wyodrębniania tabeli GroupDocs.Parser zachowuje szczegóły formatowania, takie jak obramowania komórek, style tekstu i wyrównania.
### Czy mogę wyodrębnić określone tabele na podstawie kryteriów treści?
GroupDocs.Parser oferuje elastyczne opcje kierowania na określone tabele w oparciu o szablony układu lub warunki zawartości do wyodrębnienia.
### Czy GroupDocs.Parser jest zgodny z platformą .NET Core?
Tak, GroupDocs.Parser jest kompatybilny zarówno ze środowiskami .NET Framework, jak i .NET Core.