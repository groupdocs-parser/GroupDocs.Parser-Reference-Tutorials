---
title: Extrahujte text z dokumentu aplikace Excel jako HTML
linktitle: Extrahujte text z dokumentu aplikace Excel jako HTML
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat text z dokumentů aplikace Excel a převést jej do HTML pomocí GroupDocs.Parser for .NET.
type: docs
weight: 13
url: /cs/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak používat GroupDocs.Parser for .NET k extrahování textu z dokumentu aplikace Excel a jeho převodu do formátu HTML. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům pracovat s různými formáty dokumentů a efektivně extrahovat text a metadata.
## Předpoklady
Než začneme, ujistěte se, že máte následující nastavení:
- Visual Studio nainstalované ve vašem systému.
- Základní znalost programování v C#.
-  Knihovna GroupDocs.Parser pro .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/parser/net/).
## Import jmenných prostorů
Začněte tím, že do svého projektu C# zahrnete potřebné jmenné prostory, abyste získali přístup k funkcím GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Nejprve vytvořte instanci`Parser` třídy poskytnutím cesty k dokumentu aplikace Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Další kód bude uveden zde
}
```
 Nahradit`"YourSampleFile.xlsx"` s cestou k souboru Excel.
## Krok 2: Extrahujte text jako HTML
 V rámci`using` bloku`Parser` například použijte`GetFormattedText` metoda pro extrakci formátovaného textu v režimu HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Další kód bude uveden zde
    }
}
```
## Krok 3: Přečtěte si a vytiskněte extrahovaný HTML text
 Dále si přečtěte extrahovaný text HTML z`TextReader` a vytiskněte jej do konzole.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Po spuštění tento kód extrahuje text z dokumentu aplikace Excel a zobrazí jej v konzole jako formát HTML.
## Závěr
V tomto tutoriálu jsme se naučili používat GroupDocs.Parser for .NET k extrahování textu z dokumentu aplikace Excel a jeho převodu do formátu HTML. Tato knihovna poskytuje přímočarý způsob práce s různými formáty dokumentů a umožňuje vývojářům efektivně zvládat úlohy extrakce textu v jejich aplikacích.

## FAQ
### Dokáže GroupDocs.Parser zpracovat jiné formáty dokumentů kromě Excelu?
Ano, GroupDocs.Parser podporuje širokou škálu formátů souborů včetně PDF, Word, PowerPoint a dalších.
### Je GroupDocs.Parser kompatibilní s .NET Core?
Ano, GroupDocs.Parser je kompatibilní s .NET Framework i .NET Core.
### Zachová GroupDocs.Parser formátování během extrakce textu?
Ano, GroupDocs.Parser může během extrakce textu zachovat formátování, jako jsou fonty, styly a rozvržení.
### Mohu extrahovat metadata z dokumentů pomocí GroupDocs.Parser?
Ano, GroupDocs.Parser umožňuje extrahování metadat, jako je autor, datum vytvoření a další, z podporovaných typů dokumentů.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Parser?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).