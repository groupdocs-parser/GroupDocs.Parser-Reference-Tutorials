---
title: Hledat text se zvýrazněním
linktitle: Hledat text se zvýrazněním
second_title: GroupDocs.Parser .NET API
description: Naučte se vyhledávat a zvýrazňovat text v dokumentech pomocí GroupDocs.Parser for .NET. Extrahujte cenné poznatky efektivně.
weight: 24
url: /cs/net/text-extraction/search-text-with-highlights/
type: docs
---
# Hledat text se zvýrazněním

## Úvod
tomto tutoriálu prozkoumáme, jak používat GroupDocs.Parser pro .NET k vyhledávání textu v dokumentu a zvýraznění výsledků hledání. GroupDocs.Parser je výkonná knihovna, která vám umožní pracovat s různými formáty dokumentů a extrahovat text, metadata a další.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1.  GroupDocs.Parser for .NET: Stáhněte a nainstalujte knihovnu z[tady](https://releases.groupdocs.com/parser/net/).
2. IDE: Použijte Visual Studio nebo jakékoli preferované IDE pro vývoj .NET.
3. Vzorový soubor: Připravte vzorový dokument (např. PDF, DOCX) pro textové vyhledávání.

## Import jmenných prostorů
Nejprve začněte importováním potřebných jmenných prostorů do vašeho projektu .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Vytvořte instanci analyzátoru
 Začněte vytvořením instance`Parser` třída s cestou k vašemu ukázkovému souboru:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Váš kód zde
}
```
## Krok 2: Definujte možnosti zvýraznění
 Určete`HighlightOptions` pro konfiguraci způsobu zvýraznění výsledků vyhledávání. Například nastavení kontextového okna o 15 znacích:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Krok 3: Vyhledejte text
Nyní proveďte textové vyhledávání v dokumentu. Zadejte klíčové slovo, které chcete hledat (např. „lorem“):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Krok 4: Zpracujte výsledky vyhledávání
Procházejte výsledky vyhledávání a zobrazte nalezený text spolu se zvýrazněním:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Závěr
tomto tutoriálu jste se naučili používat GroupDocs.Parser pro .NET k vyhledávání textu v dokumentech a zvýraznění výsledků hledání. Tato funkce může být nesmírně užitečná pro extrakci a analýzu textu ve vašich aplikacích .NET.

## FAQ
### Je GroupDocs.Parser vhodný pro zpracování různých formátů dokumentů?
Ano, GroupDocs.Parser podporuje širokou škálu formátů dokumentů včetně PDF, DOCX, XLSX, PPTX a dalších.
### Mohu použít GroupDocs.Parser k extrahování metadat z dokumentů?
Absolutně! GroupDocs.Parser umožňuje extrahovat metadata, text a strukturovaná data z dokumentů.
### Kde najdu podporu nebo se zeptám na GroupDocs.Parser?
 Můžete navštívit[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) pro jakékoli dotazy týkající se podpory.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Parser?
 Ano, máte přístup k a[zkušební verze zdarma](https://releases.groupdocs.com/) GroupDocs.Parser k vyhodnocení jeho funkcí.
### Jak si mohu zakoupit licenci pro GroupDocs.Parser?
 Licenci si můžete zakoupit od[tady](https://purchase.groupdocs.com/buy) a také získat dočasné licence[tady](https://purchase.groupdocs.com/temporary-license/).