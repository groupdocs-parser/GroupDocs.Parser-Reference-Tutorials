---
title: Iteruj po polach
linktitle: Iteruj po polach
second_title: GroupDocs.Parser API .NET
description: Dowiedz się, jak wyodrębnić dane strukturalne z dokumentów za pomocą GroupDocs.Parser dla .NET. Ulepsz swoje aplikacje .NET dzięki możliwościom ekstrakcji danych z dokumentów.
type: docs
weight: 11
url: /pl/net/data-extraction-from-templates/iterate-through-fields/
---
## Wstęp
GroupDocs.Parser dla .NET to potężna biblioteka, która umożliwia programistom wyodrębnianie danych z różnych formatów dokumentów, takich jak PDF, Microsoft Word, Excel i PowerPoint. Ten samouczek poprowadzi Cię przez proces używania GroupDocs.Parser do iteracji po polach dokumentu i wyodrębniania określonych danych przy użyciu szablonów. Pod koniec tego samouczka będziesz w stanie efektywnie wyodrębniać uporządkowane dane z dokumentów w aplikacjach .NET.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz skonfigurowane następujące wymagania wstępne:
- Podstawowa znajomość programowania w języku C#.
- Program Visual Studio zainstalowany na Twoim komputerze.
- Zainstalowana biblioteka GroupDocs.Parser for .NET, do której odwołuje się Twój projekt.

## Importuj przestrzenie nazw
Aby rozpocząć, dodaj niezbędne przestrzenie nazw do pliku C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Podzielmy proces na instrukcje krok po kroku.
## Krok 1: Zdefiniuj pola szablonu
Najpierw zdefiniuj pola, które chcesz wyodrębnić z dokumentu, używając wyrażeń regularnych.
```csharp
// Zdefiniuj pole „cena”.
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Zdefiniuj pole „e-mail”.
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Utwórz szablon ze zdefiniowanymi polami
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
tym kroku zdefiniowaliśmy dwa pola: jedno do wyodrębniania cen (oznaczonych znakiem dolara i cyframi), a drugie do wyodrębniania adresów e-mail.
## Krok 2: Przeanalizuj dokument
 Następnie użyj`Parser` class do analizowania dokumentu przy użyciu zdefiniowanego szablonu.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Przeanalizuj dokument według szablonu
    DocumentData data = parser.ParseByTemplate(template);
    // Iteruj po wyodrębnionych danych
    for (int i = 0; i < data.Count; i++)
    {
        // Wydrukuj nazwę pola
        Console.Write(data[i].Name + ": ");
        // Sprawdź, czy wyodrębniony obszar jest tekstem
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Tutaj inicjujemy`Parser` ze ścieżką do przykładowego dokumentu, a następnie przeanalizuj dokument przy użyciu zdefiniowanego szablonu. Następnie iterujemy po wyodrębnionych danych i drukujemy nazwy pól wraz z wyodrębnionym tekstem.
## Wniosek
W tym samouczku omówiliśmy, jak używać programu GroupDocs.Parser dla platformy .NET do wyodrębniania określonych danych z dokumentów przy użyciu szablonów. Wykorzystując wyrażenia regularne i szablony, możesz efektywnie wyodrębniać uporządkowane informacje z różnych formatów dokumentów. Eksperymentuj z różnymi szablonami i typami dokumentów, aby dopasować je do swoich konkretnych potrzeb w zakresie ekstrakcji.

## Często zadawane pytania
### Czy GroupDocs.Parser może wyodrębnić dane ze zeskanowanych dokumentów?
Tak, GroupDocs.Parser może wyodrębniać tekst i metadane zarówno z zeskanowanych, jak i przeszukiwalnych dokumentów PDF.
### Czy GroupDocs.Parser jest zgodny z aplikacjami .NET Core?
Tak, GroupDocs.Parser obsługuje .NET Core wraz z .NET Framework.
### Jakie formaty dokumentów obsługuje GroupDocs.Parser?
GroupDocs.Parser obsługuje szeroką gamę formatów, w tym PDF, Microsoft Word, Excel, PowerPoint i inne.
### Jak mogę obsługiwać duże dokumenty za pomocą GroupDocs.Parser?
GroupDocs.Parser udostępnia opcje wyodrębniania danych z określonych stron lub sekcji dużych dokumentów, zapewniając wydajne przetwarzanie.
### Czy mogę używać GroupDocs.Parser tylko do wyodrębniania tekstu?
Tak, możesz wyodrębnić zawartość zwykłego tekstu z dokumentów za pomocą GroupDocs.Parser bez konieczności stosowania skomplikowanego formatowania.