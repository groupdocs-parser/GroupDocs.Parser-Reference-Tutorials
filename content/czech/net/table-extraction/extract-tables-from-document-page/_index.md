---
title: Extrahujte tabulky ze stránky dokumentu
linktitle: Extrahujte tabulky ze stránky dokumentu
second_title: GroupDocs.Parser .NET API
description: Naučte se, jak extrahovat tabulky z dokumentů programově pomocí GroupDocs.Parser for .NET. Tento obsáhlý návod poskytuje návod krok za krokem.
weight: 11
url: /cs/net/table-extraction/extract-tables-from-document-page/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak extrahovat tabulky ze stránky dokumentu pomocí GroupDocs.Parser for .NET. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům pracovat s různými formáty dokumentů, jako jsou PDF, DOCX, XLSX a další. Využitím jeho funkcí můžeme z těchto dokumentů efektivně extrahovat strukturovaná data, jako jsou tabulky, což nám umožňuje programově manipulovat a analyzovat informace.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
- Visual Studio nainstalované na vašem počítači.
- Základní znalost vývoje C# a .NET.
-  GroupDocs.Parser pro knihovnu .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/parser/net/).
- Přístup k vzorovému dokumentu (PDF, DOCX atd.) obsahujícímu tabulky pro extrakci.

## Import jmenných prostorů
Nejprve začněte importováním potřebných jmenných prostorů do vašeho projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Vytvořte instanci`Parser` třídy poskytnutím cesty k vašemu vzorovému dokumentu:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Váš kód pokračuje zde...
}
```
## Krok 2: Zkontrolujte podporu extrakce tabulky dokumentů
Než budete pokračovat, ověřte, zda dokument podporuje extrakci tabulky:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Krok 3: Definujte rozložení tabulky
Definujte rozvržení tabulek, které mají být extrahovány z dokumentu. Zadejte šířky sloupců a výšky řádků podle struktury dokumentu:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Šířky sloupců
    new double[] { 325, 340, 365, 395 });         // Výšky řádků
```
## Krok 4: Konfigurace možností extrakce tabulky
Vytvořte možnosti pro extrakci tabulky pomocí zadaného rozvržení:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Krok 5: Získejte informace o dokumentu
Načíst informace o dokumentu, včetně počtu stránek:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Krok 6: Iterujte přes stránky dokumentu
Projděte každou stránku dokumentu a extrahujte tabulky:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extrahujte tabulky z aktuální stránky
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Iterujte extrahované tabulky
    foreach (PageTableArea table in tables)
    {
        // Iterujte přes řádky tabulky
        for (int row = 0; row < table.RowCount; row++)
        {
            // Iterujte přes sloupce tabulky
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Získejte buňku tabulky
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Vytiskněte text buňky tabulky
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

## Závěr
tomto tutoriálu jsme se zabývali procesem extrahování tabulek ze stránek dokumentů pomocí GroupDocs.Parser pro .NET. Dodržováním uvedených kroků můžete bezproblémově integrovat funkci extrakce tabulek do svých aplikací .NET, což umožňuje efektivní manipulaci a manipulaci se strukturovanými daty v dokumentech.

## FAQ
### Může GroupDocs.Parser extrahovat tabulky ze všech typů dokumentů?
GroupDocs.Parser podporuje různé formáty dokumentů jako PDF, DOCX, XLSX a další, což umožňuje extrakci tabulek z kompatibilních typů souborů.
### Je GroupDocs.Parser for .NET vhodný pro zpracování dokumentů ve velkém měřítku?
Ano, GroupDocs.Parser je navržen tak, aby efektivně zpracovával velké dokumenty, takže je vhodný pro zpracování rozsáhlých datových sad.
### Zachová GroupDocs.Parser formátování během extrakce tabulky?
Ano, GroupDocs.Parser zachovává podrobnosti o formátování, jako jsou ohraničení buněk, styly textu a zarovnání během extrakce tabulky.
### Mohu extrahovat konkrétní tabulky na základě kritérií obsahu?
GroupDocs.Parser nabízí flexibilní možnosti cílení na konkrétní tabulky na základě šablon rozvržení nebo podmínek obsahu pro extrakci.
### Je GroupDocs.Parser kompatibilní s .NET Core?
Ano, GroupDocs.Parser je kompatibilní s prostředím .NET Framework i .NET Core.