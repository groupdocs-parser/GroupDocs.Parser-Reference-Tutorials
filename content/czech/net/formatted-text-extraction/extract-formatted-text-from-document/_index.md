---
title: Extrahujte formátovaný text z dokumentu
linktitle: Extrahujte formátovaný text z dokumentu
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat formátovaný text z dokumentů pomocí GroupDocs.Parser for .NET. Jednoduchá a efektivní extrakce textu pro vaše aplikace.
weight: 10
url: /cs/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak pomocí GroupDocs.Parser for .NET extrahovat formátovaný text z různých typů dokumentů. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům pracovat s dokumenty zjednodušeným a efektivním způsobem. Na konci této příručky budete schopni bezproblémově integrovat možnosti extrakce textu do vašich aplikací .NET.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
- Visual Studio: Ujistěte se, že máte v systému nainstalované Visual Studio.
-  GroupDocs.Parser for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Parser z[tady](https://releases.groupdocs.com/parser/net/).
- Ukázky dokumentů: Připravte vzorové dokumenty (např. PDF, DOCX) pro extrakci textu.
## Import jmenných prostorů
Nejprve do kódu C# zahrňte potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Začněte inicializací a`Parser` objekt s cestou k vašemu vzorovému dokumentu.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Zde je kód pro extrakci textu
}
```
 Nahradit`"YourSampleFile.pdf"` s cestou k souboru vašeho dokumentu.

## Krok 2: Extrahujte formátovaný text
 V rámci`using` blok, použijte`GetFormattedText` metoda extrahování formátovaného textu z dokumentu. Zadejte požadovaný výstupní formát (např. HTML) pomocí`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extrahujte formátovaný text do čtečky
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Zkontrolujte, zda je podporována extrakce
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Přečtěte si a zobrazte extrahovaný text
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Závěr
Gratulujeme! Naučili jste se extrahovat formátovaný text z dokumentů pomocí GroupDocs.Parser for .NET. Tato všestranná knihovna otevírá možnosti pro zpracování a analýzu textu ve vašich aplikacích.

## FAQ
### Otázka: Může GroupDocs.Parser extrahovat text z dokumentů chráněných heslem?
Odpověď: Ano, GroupDocs.Parser podporuje extrahování textu z dokumentů chráněných heslem.
### Otázka: Které formáty dokumentů podporuje GroupDocs.Parser?
Odpověď: GroupDocs.Parser podporuje širokou škálu formátů včetně PDF, DOCX, XLSX, PPTX a dalších.
### Otázka: Jak mohu získat dočasnou licenci pro GroupDocs.Parser?
 Odpověď: Můžete získat dočasnou licenci od[tady](https://purchase.groupdocs.com/temporary-license/).
### Otázka: Poskytuje GroupDocs.Parser podporu pro extrakci obrázků z dokumentů?
Odpověď: Ano, GroupDocs.Parser podporuje extrakci obrázků spolu s extrakcí textu.
### Otázka: Kde mohu najít další podporu nebo se zeptat na otázky ohledně GroupDocs.Parser?
 A: Navštivte[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)za podporu a diskuze.