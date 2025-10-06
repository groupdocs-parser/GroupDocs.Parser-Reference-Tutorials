---
title: Extrahujte formátovaný text ze stránky dokumentu
linktitle: Extrahujte formátovaný text ze stránky dokumentu
second_title: GroupDocs.Parser .NET API
description: Extrahujte formátovaný text ze stránek dokumentu pomocí GroupDocs.Parser for .NET. Efektivní a spolehlivé řešení extrakce textu.
weight: 11
url: /cs/net/formatted-text-extraction/extract-formatted-text-from-document-page/
type: docs
---
# Extrahujte formátovaný text ze stránky dokumentu

## Úvod
V tomto tutoriálu vás provedeme procesem extrahování formátovaného textu ze stránek dokumentu pomocí GroupDocs.Parser for .NET. Tato knihovna umožňuje efektivně analyzovat a extrahovat text z různých formátů dokumentů, jako je PDF, Word, Excel a další.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
- Visual Studio nainstalované ve vašem systému.
- Základní znalost programování v C#.
-  GroupDocs.Parser pro knihovnu .NET. Můžete si jej stáhnout[tady](https://releases.groupdocs.com/parser/net/).

## Import jmenných prostorů
Nejprve začněte importováním potřebných jmenných prostorů do vašeho projektu C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Začněte vytvořením instance souboru`Parser` třídy poskytnutím cesty k vašemu ukázkovému souboru.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kód půjde sem
}
```
## Krok 2: Zkontrolujte, zda je podporována extrakce formátovaného textu
Než budete pokračovat s extrakcí textu, ověřte, zda dokument podporuje extrakci formátovaného textu.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Krok 3: Získejte informace o dokumentu
Získejte informace o dokumentu, jako je počet stránek.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Krok 4: Iterujte stránky dokumentu a extrahujte formátovaný text
Iterujte každou stránku dokumentu a extrahujte formátovaný text pomocí zadaných možností (např. formát Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Závěr
Nyní víte, jak extrahovat formátovaný text ze stránek dokumentu pomocí GroupDocs.Parser for .NET. Tato knihovna poskytuje výkonné a snadno použitelné řešení pro extrakci textu z různých formátů souborů.

## FAQ
### Dokáže GroupDocs.Parser zpracovat různé formáty souborů?
Ano, GroupDocs.Parser podporuje širokou škálu formátů dokumentů, včetně PDF, DOCX, XLSX, PPTX a dalších.
### Je GroupDocs.Parser kompatibilní s .NET Core?
Ano, GroupDocs.Parser podporuje .NET Core a .NET Framework.
### Zachová GroupDocs.Parser během extrakce formátování textu?
Ano, GroupDocs.Parser může při extrahování textu zachovat formátování, jako jsou styly a písma.
### Mohu extrahovat obrázky a metadata pomocí GroupDocs.Parser?
Ano, GroupDocs.Parser umožňuje extrakci obrázků, metadat a textu z dokumentů.
### Jak mohu získat podporu pro GroupDocs.Parser?
 Můžete získat podporu od[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).