---
title: Hledat text podle regulárního výrazu (regex)
linktitle: Hledat text podle regulárního výrazu (regex)
second_title: GroupDocs.Parser .NET API
description: Naučte se vyhledávat text pomocí regulárních výrazů v dokumentech pomocí GroupDocs.Parser for .NET. Extrahujte konkrétní obsah bez námahy.
weight: 23
url: /cs/net/text-extraction/search-text-by-regex/
---

# Hledat text podle regulárního výrazu (regex)

## Úvod
V tomto tutoriálu se ponoříme do používání GroupDocs.Parser pro .NET k vyhledávání textu podle regulárního výrazu (Regex) v dokumentech. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům extrahovat text a metadata z různých formátů souborů, jako jsou PDF, DOCX, XLSX a další. Hledání textu pomocí regulárních výrazů je zvláště užitečné pro efektivní vyhledávání vzorů nebo specifického obsahu v dokumentech.
## Předpoklady
Než se pustíte do tohoto návodu, ujistěte se, že máte následující:
1. Visual Studio: Nainstalujte Visual Studio IDE pro vývoj .NET.
2.  GroupDocs.Parser for .NET: Stáhněte a nainstalujte GroupDocs.Parser pro .NET z[tady](https://releases.groupdocs.com/parser/net/).
3. Vzorový soubor: Připravte vzorový dokument (PDF, DOCX atd.) pro testování funkčnosti vyhledávání.

## Import jmenných prostorů
Nejprve začněte zahrnutím potřebných jmenných prostorů do kódu C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Vytvořte instanci`Parser` třídy poskytnutím cesty k vašemu ukázkovému souboru:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kód jde sem
}
```
 Nahradit`"YourSampleFile.pdf"` s cestou k vašemu skutečnému souboru.
## Krok 2: Vyhledávání pomocí regulárního výrazu
Definujte a spusťte vyhledávání pomocí vzoru regulárních výrazů. Chcete-li například najít číselné sekvence (např. celá čísla) v dokumentu:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 V tomto příkladu`[0-9]+` je vzor regulárního výrazu, který odpovídá jedné nebo více číslicím.
## Krok 3: Zkontrolujte podporu vyhledávání
Ověřte, zda je operace vyhledávání podporována pro daný typ dokumentu:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Krok 4: Opakujte výsledky vyhledávání
Projděte si výsledky vyhledávání a zpracujte každou shodu:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Tato smyčka vytiskne pozici a odpovídající text nalezený v dokumentu.

## Závěr
Závěrem lze říci, že využití GroupDocs.Parser pro .NET umožňuje efektivní vyhledávání textu pomocí regulárních výrazů v různých formátech dokumentů. Podle této příručky mohou vývojáři bez problémů integrovat analýzu dokumentů a extrakci textu na základě regulárních výrazů do svých aplikací .NET.

## FAQ
### Může GroupDocs.Parser vyhledávat v zašifrovaných dokumentech?
Ne, GroupDocs.Parser nemůže vyhledávat v zašifrovaných nebo heslem chráněných dokumentech.
### Podporuje GroupDocs.Parser OCR (optické rozpoznávání znaků)?
Ne, GroupDocs.Parser neprovádí OCR. Spoléhá na extrakci textu z vnitřní struktury dokumentu.
### Mohu hledat složité vzory pomocí regulárních výrazů?
Ano, GroupDocs.Parser podporuje plnohodnotné regulární výrazy, které umožňují komplexní porovnávání vzorů v dokumentech.
### Které formáty dokumentů jsou podporovány pro extrakci textu?
GroupDocs.Parser podporuje širokou škálu formátů, včetně PDF, DOCX, XLSX, PPTX a dalších.
### Je GroupDocs.Parser kompatibilní s .NET Core?
Ano, GroupDocs.Parser je kompatibilní s .NET Core pro vývoj napříč platformami.