---
title: Hledání textu v dokumentu aplikace Word podle klíčového slova
linktitle: Hledání textu v dokumentu aplikace Word podle klíčového slova
second_title: GroupDocs.Parser .NET API
description: Naučte se vyhledávat text v dokumentech aplikace Word pomocí GroupDocs.Parser for .NET. Extrahujte konkrétní klíčová slova efektivně.
weight: 18
url: /cs/net/word-document-processing/search-text-in-word-document-by-keyword/
---

# Hledání textu v dokumentu aplikace Word podle klíčového slova

## Úvod
V tomto tutoriálu prozkoumáme, jak používat GroupDocs.Parser pro .NET k hledání konkrétního textu v dokumentu aplikace Word pomocí C#. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům extrahovat text a metadata z různých formátů dokumentů, včetně dokumentů Word.
## Předpoklady
Než začnete, ujistěte se, že máte následující předpoklady:
1. Vývojové prostředí: Nainstalujte Visual Studio nebo jiné kompatibilní IDE.
2.  Knihovna GroupDocs.Parser: Stáhněte a nainstalujte knihovnu GroupDocs.Parser for .NET z[webová stránka](https://releases.groupdocs.com/parser/net/).
3. Ukázkový dokument aplikace Word: Připravte si ukázkový dokument aplikace Word, který se použije pro vyhledávání textu.

## Import jmenných prostorů
Začněte importováním potřebných jmenných prostorů do vašeho projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Nejprve vytvořte instanci souboru`Parser` třídy předáním cesty k ukázkovému dokumentu aplikace Word.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kód jde sem
}
```
## Krok 2: Vyhledejte klíčové slovo
 Dále použijte`Search` metoda`Parser` třídy k vyhledání konkrétního klíčového slova v dokumentu.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Nahradit`"keyword"` s textem, který chcete v dokumentu hledat.
## Krok 3: Opakujte výsledky vyhledávání
 Iterujte výsledky vyhledávání pomocí a`foreach` smyčka pro přístup ke každému`SearchResult` objekt.
```csharp
foreach (SearchResult result in searchResults)
{
    //Kód pro zpracování každého výsledku vyhledávání
}
```
## Krok 4: Přístup k podrobnostem o výsledcích vyhledávání
 V rámci smyčky můžete přistupovat k pozici a textu každého výsledku vyhledávání pomocí`Position` a`Text` vlastnosti`SearchResult` objekt.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Tento fragment kódu vytiskne index (`Position`) a nalezený text (`Text`) pro každý výsledek vyhledávání do konzole.

## Závěr
V tomto kurzu jste se naučili, jak používat GroupDocs.Parser for .NET k hledání konkrétního textu v dokumentu aplikace Word. Tato knihovna poskytuje pohodlný způsob, jak programově extrahovat a manipulovat s obsahem z různých formátů dokumentů.

## FAQ
### Dokáže GroupDocs.Parser zpracovat jiné formáty dokumentů kromě Wordu?
Ano, GroupDocs.Parser podporuje širokou škálu formátů, včetně PDF, Excel, PowerPoint a dalších.
### Je GroupDocs.Parser kompatibilní s .NET Core?
Ano, GroupDocs.Parser je kompatibilní s .NET Framework i .NET Core.
### Jak získám dočasnou licenci pro GroupDocs.Parser?
 Můžete požádat o dočasnou licenci od[Nákupní stránka GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Kde najdu další podporu nebo se zeptám na GroupDocs.Parser?
 Navštivte[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) za podporu komunity a diskuze.
### Mohu si GroupDocs.Parser před nákupem zdarma vyzkoušet?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[Stránka vydání GroupDocs](https://releases.groupdocs.com/).