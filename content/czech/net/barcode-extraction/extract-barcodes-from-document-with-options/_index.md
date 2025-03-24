---
title: Extrahujte čárové kódy z dokumentu pomocí možností
linktitle: Extrahujte čárové kódy z dokumentu pomocí možností
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat čárové kódy z dokumentů pomocí GroupDocs.Parser for .NET. Komplexní výukový program s příklady kódu a často kladenými dotazy.
weight: 14
url: /cs/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## Úvod
V tomto tutoriálu si projdeme proces extrahování čárových kódů z dokumentu pomocí GroupDocs.Parser for .NET. GroupDocs.Parser je výkonná knihovna, která umožňuje extrahovat text, metadata a čárové kódy z různých formátů dokumentů, jako je PDF, Microsoft Word, Excel a další.
## Předpoklady
Než začnete, ujistěte se, že máte splněny následující předpoklady:
1. Vývojové prostředí: Ujistěte se, že máte na svém počítači nainstalované Visual Studio.
2.  Knihovna GroupDocs.Parser: Stáhněte a nainstalujte knihovnu GroupDocs.Parser for .NET z[tady](https://releases.groupdocs.com/parser/net/).
3. Vzorový dokument: Připravte vzorový dokument (např. PDF, DOCX) obsahující čárové kódy pro extrakci.

## Import jmenných prostorů
Nejprve musíte do svého projektu C# importovat potřebné jmenné prostory, abyste mohli využívat funkce GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Chcete-li začít, vytvořte instanci souboru`Parser` třídy předáním cesty k vašemu vzorovému dokumentu.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kód, který bude přidán v dalších krocích
}
```
## Krok 2: Zkontrolujte podporu extrakce čárového kódu
 Dále zkontrolujte, zda dokument podporuje extrakci čárového kódu pomocí`Features` vlastnictví`Parser` instance.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Krok 3: Definujte možnosti extrakce čárového kódu
 Nyní zadejte možnosti pro extrakci čárového kódu pomocí`BarcodeOptions`. Můžete nastavit parametry, jako jsou režimy kvality a typy čárových kódů.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Krok 4: Extrahujte čárové kódy z dokumentu
 Použijte`GetBarcodes` metoda`Parser` třídy extrahovat čárové kódy na základě definovaných možností.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Krok 5: Iterujte a zobrazte extrahované čárové kódy
Nakonec projděte extrahované čárové kódy a zobrazte jejich index stránky a hodnoty.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Závěr
 V tomto tutoriálu jsme se naučili, jak extrahovat čárové kódy z dokumentu pomocí GroupDocs.Parser for .NET. Tento proces zahrnuje vytvoření a`Parser` definování možností extrakce a iterování extrahovaných čárových kódů. GroupDocs.Parser zjednodušuje extrakci čárových kódů z různých formátů dokumentů a umožňuje efektivní zpracování dokumentů ve vašich aplikacích .NET.

## FAQ
### Může GroupDocs.Parser extrahovat čárové kódy z dokumentů PDF?
Ano, GroupDocs.Parser podporuje extrakci čárových kódů z dokumentů PDF spolu s dalšími formáty jako DOCX, XLSX atd.
### Jaké typy čárových kódů podporuje GroupDocs.Parser?
GroupDocs.Parser podporuje různé typy čárových kódů včetně QR kódů, Code 39, Code 128 a dalších.
### Vyžaduje GroupDocs.Parser licenci pro komerční použití?
 Ano, pro komerční použití je nutná platná licence. Licenci můžete získat od[tady](https://purchase.groupdocs.com/buy).
### Je GroupDocs.Parser vhodný pro dávkové zpracování dokumentů?
Ano, GroupDocs.Parser dokáže efektivně zvládnout dávkové zpracování dokumentů pro extrakci textu, načítání metadat a extrakci čárových kódů.
### Kde najdu technickou podporu pro GroupDocs.Parser?
 Technickou podporu nebo dotazy můžete získat na[fórum GroupDocs](https://forum.groupdocs.com/c/parser/17).