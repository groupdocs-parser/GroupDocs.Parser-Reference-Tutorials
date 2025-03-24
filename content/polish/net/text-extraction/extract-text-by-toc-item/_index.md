---
title: Wyodrębnij tekst według pozycji spisu treści (TOC).
linktitle: Wyodrębnij tekst według pozycji spisu treści (TOC).
second_title: GroupDocs.Parser API .NET
description: Wyodrębnij tekst według spisu treści (TOC) za pomocą GroupDocs.Parser dla .NET. Poznaj wydajne techniki analizowania dokumentów w celu ekstrakcji danych strukturalnych.
weight: 15
url: /pl/net/text-extraction/extract-text-by-toc-item/
---
## Wstęp
W tym samouczku pokażemy, jak wykorzystać GroupDocs.Parser dla .NET do wyodrębnienia tekstu na podstawie elementów spisu treści (TOC) z dokumentów. GroupDocs.Parser to potężne narzędzie umożliwiające wydajne analizowanie i wyodrębnianie dokumentów.
## Warunki wstępne
Przed kontynuowaniem tego samouczka upewnij się, że spełnione są następujące wymagania wstępne:
1. Visual Studio: Zainstaluj Visual Studio IDE w swoim systemie.
2.  GroupDocs.Parser dla .NET: Pobierz i zainstaluj GroupDocs.Parser dla .NET z[Tutaj](https://releases.groupdocs.com/parser/net/).
3. Przykładowy dokument ze spisem treści: Przygotuj dokument (np. PDF, DOCX) zawierający spis treści.

## Importowanie przestrzeni nazw
Najpierw uwzględnij niezbędne przestrzenie nazw w swoim projekcie C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Krok 1: Utwórz instancję klasy analizatora składni
 Utwórz instancję`Parser` class ze ścieżką do przykładowego dokumentu:
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // Kontynuuj, wykonując kolejne kroki tutaj...
}
```
## Krok 2: Wyodrębnij spis treści (TOC)
Pobierz elementy spisu treści (TOC) z dokumentu:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## Krok 3: Iteruj po pozycjach spisu treści i wyodrębnij tekst
Wykonaj iterację po każdym elemencie spisu treści i wyodrębnij odpowiedni tekst:
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Wniosek
W tym samouczku pokazano, jak wyodrębnić tekst z dokumentu na podstawie elementów spisu treści (TOC) przy użyciu programu GroupDocs.Parser dla platformy .NET. Wykonując opisane kroki, możesz efektywnie programowo analizować i wyodrębniać określoną treść z dokumentów.

## Często zadawane pytania
### Jakie formaty plików obsługuje GroupDocs.Parser?
GroupDocs.Parser obsługuje szeroką gamę formatów dokumentów, w tym PDF, Microsoft Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) i inne.
### Czy za pomocą GroupDocs.Parser mogę wyodrębnić dane strukturalne, takie jak tabele lub obrazy?
Tak, GroupDocs.Parser udostępnia interfejsy API umożliwiające wyodrębnianie danych strukturalnych, takich jak tabele, obrazy i metadane, z różnych typów dokumentów.
### Czy GroupDocs.Parser nadaje się do dużych dokumentów?
GroupDocs.Parser jest zoptymalizowany pod kątem wydajnej obsługi dużych dokumentów, umożliwiając bezproblemowe wyodrębnianie treści z obszernych plików.
### Jak mogę uzyskać pomoc techniczną dla GroupDocs.Parser?
 Możesz szukać pomocy technicznej i kontaktować się ze społecznością pod adresem[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Czy GroupDocs oferuje bezpłatną wersję próbną do oceny?
Tak, możesz pobrać bezpłatną wersję próbną GroupDocs.Parser ze strony[Tutaj](https://releases.groupdocs.com/).