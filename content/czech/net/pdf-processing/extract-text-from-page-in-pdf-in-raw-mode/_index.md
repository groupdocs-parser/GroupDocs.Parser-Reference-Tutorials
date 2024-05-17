---
title: Extrahujte text ze stránky ve formátu PDF v režimu Raw
linktitle: Extrahujte text ze stránky ve formátu PDF v režimu Raw
second_title: GroupDocs.Parser .NET API
description: Extrahujte text z PDF pomocí GroupDocs.Parser v C#. Naučte se efektivní extrakci textu PDF pomocí této výkonné knihovny .NET.
type: docs
weight: 16
url: /cs/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak používat GroupDocs.Parser pro .NET k extrahování textu ze stránek v dokumentech PDF pomocí režimu raw. GroupDocs.Parser je výkonný nástroj, který umožňuje vývojářům programově pracovat s různými formáty dokumentů.
## Předpoklady
Před zahájením tohoto kurzu se ujistěte, že máte následující:
- Visual Studio nainstalované na vašem počítači.
- Základní znalost programování v C#.
- GroupDocs.Parser pro knihovnu .NET, kterou můžete[stáhnout zde](https://releases.groupdocs.com/parser/net/).
- Ukázkový soubor PDF pro testovací účely.

## Import jmenných prostorů
Nejprve se ujistěte, že jste do svého projektu C# importovali potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Chcete-li začít, vytvořte instanci`Parser`třídy poskytnutím cesty k vašemu ukázkovému souboru PDF.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Váš kód je zde
}
```
## Krok 2: Získejte informace o dokumentu a iterujte stránky
Dále načtěte informace o dokumentu a iterujte přes každou stránku, abyste extrahovali text.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Zde je váš kód pro extrakci textu
}
```
## Krok 3: Extrahujte text z každé stránky
 V rámci smyčky použijte`GetText` metoda extrahovat text z každé stránky a vytisknout ji.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Závěr
 V tomto tutoriálu jsme se naučili, jak extrahovat text ze stránek PDF v nezpracovaném režimu pomocí GroupDocs.Parser for .NET. Tento proces zahrnuje vytvoření a`Parser` získání informací o dokumentu, iterování každé stránky a extrahování textu pomocí`GetText` metoda.

## FAQ
### Co je GroupDocs.Parser for .NET?
GroupDocs.Parser for .NET je rozhraní API pro analýzu dokumentů, které umožňuje vývojářům programově extrahovat text, metadata a další informace z různých formátů souborů.
### Jak stáhnu GroupDocs.Parser pro .NET?
 Knihovnu si můžete stáhnout z[Web GroupDocs](https://releases.groupdocs.com/parser/net/).
### Je k dispozici bezplatná zkušební verze?
 Ano, máte přístup k bezplatné zkušební verzi GroupDocs.Parser pro .NET z[tady](https://releases.groupdocs.com/).
### Kde najdu podporu pro GroupDocs.Parser pro .NET?
 Pro technickou pomoc a podporu komunity navštivte stránku[fórum GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Jak si mohu zakoupit licenci pro GroupDocs.Parser for .NET?
 Licenci si můžete zakoupit od[nákupní stránku](https://purchase.groupdocs.com/buy) nebo získat dočasnou licenci[tady](https://purchase.groupdocs.com/temporary-license/).