---
title: Extrahujte tabulky z dokumentu
linktitle: Extrahujte tabulky z dokumentu
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat tabulky z dokumentů pomocí Groupdocs.Parser for .NET. Postupujte podle podrobného průvodce integrací této funkce.
weight: 10
url: /cs/net/table-extraction/extract-tables-from-document/
---

# Extrahujte tabulky z dokumentu

## Úvod
Groupdocs.Parser for .NET je komplexní knihovna, která usnadňuje analýzu dokumentů a umožňuje vám z dokumentů extrahovat cenné informace, jako jsou tabulky, text, metadata a další. V tomto tutoriálu se zaměřujeme konkrétně na extrahování tabulek z dokumentů pomocí Groupdocs.Parser API.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
- Visual Studio nainstalované ve vašem systému.
- Nainstalované rozhraní .NET Framework nebo .NET Core.
- Základní znalost programování v C#.

## Import jmenných prostorů
Nejprve musíte importovat potřebné jmenné prostory pro přístup ke třídám a metodám Groupdocs.Parser.
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
 Inicializujte novou instanci souboru`Parser` třídy poskytnutím cesty k vašemu ukázkovému dokumentu.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Váš kód je zde
}
```
## Krok 2: Zkontrolujte podporu extrakce tabulky
 Ověřte, zda dokument podporuje extrakci tabulky pomocí`Features` vlastnictví`Parser` třída.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Krok 3: Definujte rozložení tabulky
Definujte rozvržení tabulek, které chcete pomocí extrahovat`TemplateTableLayout`. Určete šířky sloupců a výšky řádků na základě struktury dokumentu.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Krok 4: Nastavte možnosti extrakce tabulky
 Vytvořit`PageTableAreaOptions` s definovaným rozložením, abyste určili, jak mají být tabulky extrahovány.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Krok 5: Extrahujte tabulky
 Využijte`GetTables` metoda`Parser` třídy extrahovat tabulky z dokumentu na základě zadaných možností.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Krok 6: Iterace a přístup k datům tabulky
Iterováním extrahovaných tabulek a jejich příslušných řádků a sloupců získáte přístup k datům buněk.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Závěr
V tomto tutoriálu jsme probrali, jak používat Groupdocs.Parser pro .NET k efektivnímu extrahování tabulek z dokumentů. Využitím možností této knihovny můžete bez problémů integrovat extrakci tabulek do aplikací .NET.

## FAQ
### Dokáže Groupdocs.Parser zpracovat různé formáty dokumentů?
Ano, Groupdocs.Parser podporuje širokou škálu formátů dokumentů včetně DOCX, PDF, XLSX a dalších.
### Je k dispozici zkušební verze pro Groupdocs.Parser pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Jak mohu získat podporu pro dotazy související s Groupdocs.Parser?
 Můžete navštívit[Fórum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) pro pomoc.
### Kde si mohu zakoupit licenci pro Groupdocs.Parser?
 Licenci si můžete zakoupit od[tady](https://purchase.groupdocs.com/buy).
### Jak mohu získat dočasnou licenci pro účely hodnocení?
 Můžete získat dočasnou licenci[tady](https://purchase.groupdocs.com/temporary-license/).