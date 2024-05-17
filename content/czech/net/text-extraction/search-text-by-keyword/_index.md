---
title: Hledat text podle klíčového slova
linktitle: Hledat text podle klíčového slova
second_title: GroupDocs.Parser .NET API
description: Naučte se vyhledávat text podle klíčových slov v dokumentech pomocí GroupDocs.Parser for .NET. Snadno efektivně extrahujte relevantní obsah.
type: docs
weight: 21
url: /cs/net/text-extraction/search-text-by-keyword/
---
## Úvod
V tomto tutoriálu se ponoříme do používání GroupDocs.Parser pro .NET k vyhledávání textu podle klíčových slov v dokumentech. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům extrahovat text, metadata a další informace z různých formátů souborů, jako jsou PDF, dokumenty Microsoft Office a další. Hledání konkrétních klíčových slov v těchto dokumentech může být zásadní pro aplikace, které pracují s velkými objemy textových dat.
## Předpoklady
Než začneme, ujistěte se, že máte následující nastavení:
1. Vývojové prostředí: Visual Studio nebo jakékoli preferované .NET IDE.
2.  GroupDocs.Parser pro .NET: Stáhněte si knihovnu z[tady](https://releases.groupdocs.com/parser/net/).
3. Přístup k ukázkovým souborům: Připravte si ukázkový soubor (např. PDF, DOCX), abyste otestovali funkci vyhledávání klíčových slov.

## Import jmenných prostorů
Nejprve musíte do projektu zahrnout potřebné jmenné prostory.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Začněte vytvořením instance souboru`Parser` třídy a zadejte cestu k vašemu ukázkovému souboru.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Vyhledejte klíčové slovo
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Opakujte výsledky vyhledávání
    foreach (SearchResult result in searchResults)
    {
        //Vytiskněte rejstřík a nalezený text
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Krok 2: Vyhledejte klíčové slovo
 V rámci`using` zablokovat, zavolat`Search` metoda na`parser` objekt a předá požadované klíčové slovo jako argument.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Nahradit`"test"` s klíčovým slovem, které chcete v dokumentu hledat.
## Krok 3: Opakujte výsledky vyhledávání
 Dále iterujte výsledky hledání získané z`Search` metoda využívající a`foreach` smyčka.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Pro každého`SearchResult` objekt`result` , můžete k němu přistupovat`Position` (index) a`Text` (nalezený text).

## Závěr
 V tomto tutoriálu jsme prozkoumali, jak používat GroupDocs.Parser pro .NET k snadnému vyhledávání textu podle klíčových slov v dokumentech. Využití`Search` metoda`Parser` třída umožňuje efektivní vyhledávání relevantních textových úryvků na základě konkrétních hledaných výrazů.

## FAQ
### Je GroupDocs.Parser kompatibilní s různými formáty dokumentů?
Ano, GroupDocs.Parser podporuje širokou škálu formátů souborů, včetně PDF, DOCX, XLSX, PPTX a dalších.
### Mohu provádět pokročilé operace extrakce textu pomocí GroupDocs.Parser?
Absolutně! Kromě textového vyhledávání umožňuje GroupDocs.Parser extrakci metadat, extrakci strukturovaného textu a další.
### Kde najdu podrobnou dokumentaci k GroupDocs.Parser?
Prozkoumejte kompletní dokumentaci[tady](https://reference.groupdocs.com/parser/net/).
### Jak mohu získat podporu nebo pomoc s dotazy týkajícími se GroupDocs.Parser?
 Navštivte fórum GroupDocs pro podporu a diskuse[tady](https://forum.groupdocs.com/c/parser/17).
### Je k dispozici zkušební verze pro vyhodnocení GroupDocs.Parser před zakoupením?
 Ano, máte přístup k bezplatné zkušební verzi[tady](https://releases.groupdocs.com/).