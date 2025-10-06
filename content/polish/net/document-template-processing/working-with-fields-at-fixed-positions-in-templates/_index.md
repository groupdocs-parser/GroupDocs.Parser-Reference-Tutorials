---
title: Praca z polami w ustalonych pozycjach w szablonach
linktitle: Praca z polami w ustalonych pozycjach w szablonach
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębniać dane z dokumentów za pomocą GroupDocs.Parser dla .NET. Obszerny samouczek z przykładami kodu.
weight: 11
url: /pl/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
type: docs
---
# Praca z polami w ustalonych pozycjach w szablonach

## Wstęp
W tym samouczku omówimy, jak pracować z polami w ustalonych pozycjach w szablonach przy użyciu GroupDocs.Parser dla .NET. GroupDocs.Parser to potężna biblioteka do analizowania dokumentów, która umożliwia programistom wyodrębnianie danych z różnych formatów dokumentów, takich jak PDF, Word, Excel i innych. W szczególności skupimy się na definiowaniu i wykorzystywaniu pól szablonów w celu wyodrębnienia ukierunkowanych informacji na podstawie ich stałych pozycji.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
- Podstawowa znajomość programowania w C# i .NET.
- Program Visual Studio zainstalowany w systemie.
- Zainstalowana biblioteka GroupDocs.Parser for .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/parser/net/).
- Przykładowe pliki dokumentów do testów.

## Importuj przestrzenie nazw
Zacznij od uwzględnienia niezbędnych przestrzeni nazw w projekcie C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Krok 1: Zdefiniuj pole szablonu
Najpierw zdefiniuj pole ze stałą pozycją w szablonie. To pole reprezentuje obszar, z którego zostaną wyodrębnione dane.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Tutaj:
- `Rectangle` określa położenie i wielkość pola.
- `Point(35, 135)` reprezentuje współrzędne lewego górnego rogu.
- `Size(100, 10)` określa szerokość i wysokość pola.
- `"FromCompany"` to nazwa przypisana do tego pola.
## Krok 2: Utwórz szablon
Skonstruuj szablon, korzystając ze zdefiniowanego pola.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 The`Template` obiekt przechowuje zdefiniowane pola.
## Krok 3: Przeanalizuj dokument przy użyciu szablonu
 Utwórz instancję`Parser` class z docelową ścieżką dokumentu, a następnie przeanalizuj dokument przy użyciu utworzonego szablonu.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Iteruj po wyodrębnionych danych
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Tutaj:
- `Parser` jest inicjowany przy użyciu ścieżki przykładowego pliku dokumentu.
- `ParseByTemplate` metoda służy do wyodrębniania danych na podstawie dostarczonego szablonu.
-  Dostęp do wyodrębnionych danych uzyskuje się za pomocą`DocumentData`gdzie każdy element odpowiada zdefiniowanemu polu.

## Wniosek
W tym samouczku omówiliśmy proces pracy z polami w ustalonych pozycjach w szablonach przy użyciu GroupDocs.Parser dla .NET. Definiując szablony z określonymi pozycjami pól, programiści mogą dokładnie wyodrębniać docelowe dane z różnych formatów dokumentów.

## Często zadawane pytania
### Czy GroupDocs.Parser jest kompatybilny ze wszystkimi formatami dokumentów?
 GroupDocs.Parser obsługuje szeroką gamę formatów plików, w tym PDF, Microsoft Word, Excel, PowerPoint i inne. Patrz[dokumentacja](https://tutorials.groupdocs.com/parser/net/) aby uzyskać szczegółową listę.
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Parser?
 Licencję tymczasową do celów testowych można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę znaleźć pomoc dotyczącą GroupDocs.Parser?
 Aby uzyskać pomoc techniczną i dyskusje, odwiedź stronę[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Czy mogę wypróbować GroupDocs.Parser przed zakupem?
 Tak, możesz przeglądać bibliotekę w ramach bezpłatnego okresu próbnego[Tutaj](https://releases.groupdocs.com/).
### Jak kupić licencję na GroupDocs.Parser?
 Aby kupić licencję, odwiedź stronę[strona zakupu](https://purchase.groupdocs.com/buy).