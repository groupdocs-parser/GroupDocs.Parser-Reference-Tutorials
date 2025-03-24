---
title: Extrahujte text z dokumentu aplikace Word jako HTML
linktitle: Extrahujte text z dokumentu aplikace Word jako HTML
second_title: GroupDocs.Parser .NET API
description: Naučte se používat GroupDocs.Parser for .NET k extrahování textu z dokumentů aplikace Word a jeho uložení jako HTML. Výukový program krok za krokem s příklady kódu.
weight: 16
url: /cs/net/word-document-processing/extract-text-from-word-document-as-html/
---

# Extrahujte text z dokumentu aplikace Word jako HTML

## Úvod
GroupDocs.Parser for .NET je výkonná knihovna pro analýzu dokumentů, která umožňuje vývojářům bezproblémově extrahovat text a metadata z různých formátů souborů. V tomto tutoriálu se zaměříme na využití GroupDocs.Parser k extrahování textu z dokumentů aplikace Word a jeho uložení jako HTML. Tento proces je nezbytný pro úkoly, jako je analýza obsahu, indexování nebo převod dokumentů do webových formátů. Na konci této příručky budete mít jasno v tom, jak efektivně používat GroupDocs.Parser ve vašich aplikacích .NET.
## Předpoklady
Než se pustíte do tohoto tutoriálu, ujistěte se, že máte následující předpoklady:
- Základní znalost programování v C#.
- Visual Studio nainstalované na vašem vývojovém počítači.
-  GroupDocs.Parser pro knihovnu .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/parser/net/).
- Přístup k ukázkovému dokumentu aplikace Word pro účely testování.
## Import jmenných prostorů
Chcete-li začít, musíte do svého projektu C# importovat potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Chcete-li extrahovat text z dokumentu aplikace Word a uložit jej jako HTML pomocí GroupDocs.Parser for .NET, postupujte podle těchto podrobných kroků:
## Krok 1: Vytvořte instanci třídy analyzátoru
 Nejprve vytvořte instanci souboru`Parser` třídy poskytnutím cesty k ukázkovému dokumentu aplikace Word:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Pokračujte krokem 2...
}
```
 Nahradit`"YourSampleFile.docx"` cestou k vašemu dokumentu aplikace Word.
## Krok 2: Extrahujte formátovaný text jako HTML
 Dále použijte`GetFormattedText` metoda spolu s`FormattedTextOptions`extrahovat text ve formátu HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extrahujte formátovaný text do čtečky
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Pokračujte krokem 3...
    }
}
```
## Krok 3: Přečtěte si a vytiskněte extrahovaný HTML
 Nakonec si přečtěte extrahovaný obsah HTML z`TextReader` a vytisknout do konzole:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extrahujte formátovaný text do čtečky
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Vytiskněte formátovaný text jako HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Závěr
V tomto tutoriálu jsme prozkoumali, jak pomocí GroupDocs.Parser for .NET extrahovat text z dokumentu aplikace Word a uložit jej jako HTML. Tato knihovna nabízí přímočarý a efektivní způsob analýzy obsahu dokumentů, což z ní činí neocenitelný nástroj pro úlohy zpracování dokumentů v aplikacích .NET.

## FAQ
### Jak mohu získat dočasnou licenci pro GroupDocs.Parser?
 Můžete požádat o dočasnou licenci z[tady](https://purchase.groupdocs.com/temporary-license/).
### Kde najdu další dokumentaci k GroupDocs.Parser?
 K dispozici je podrobná dokumentace[tady](https://tutorials.groupdocs.com/parser/net/).
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Parser?
 Ano, máte přístup k bezplatné zkušební verzi[tady](https://releases.groupdocs.com/).
### Jak získám podporu pro GroupDocs.Parser?
 Navštivte fórum podpory[tady](https://forum.groupdocs.com/c/parser/17).
### Jaké typy dokumentů podporuje GroupDocs.Parser?
GroupDocs.Parser podporuje různé formáty dokumentů včetně Wordu, PDF, Excelu, PowerPointu a dalších.