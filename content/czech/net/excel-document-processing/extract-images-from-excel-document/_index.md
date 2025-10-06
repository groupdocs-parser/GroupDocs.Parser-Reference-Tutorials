---
title: Extrahujte obrázky z dokumentu aplikace Excel
linktitle: Extrahujte obrázky z dokumentu aplikace Excel
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat obrázky z dokumentů aplikace Excel pomocí GroupDocs.Parser for .NET. Podrobný průvodce s příklady kódu.
weight: 10
url: /cs/net/excel-document-processing/extract-images-from-excel-document/
type: docs
---
# Extrahujte obrázky z dokumentu aplikace Excel

## Úvod
tomto tutoriálu se naučíte extrahovat obrázky z dokumentu aplikace Excel pomocí GroupDocs.Parser for .NET. GroupDocs.Parser je výkonná knihovna, která vám umožňuje analyzovat a extrahovat text, metadata a obrázky z různých formátů dokumentů včetně souborů aplikace Excel.
## Předpoklady
Než začnete, ujistěte se, že máte nastaveny následující předpoklady:
1. Vývojové prostředí: Nainstalujte Visual Studio nebo jakékoli preferované vývojové prostředí .NET.
2.  Knihovna GroupDocs.Parser: Stáhněte a odkazujte na knihovnu GroupDocs.Parser. Knihovnu můžete získat od[tady](https://releases.groupdocs.com/parser/net/).
3. Vzorový soubor Excel: Připravte si vzorový soubor Excel, ze kterého chcete extrahovat obrázky.
## Import jmenných prostorů
Zahrňte do projektu potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Chcete-li extrahovat obrázky z dokumentu aplikace Excel, postupujte takto:
## Krok 1: Vytvořte instanci třídy analyzátoru
 Nejprve vytvořte instanci souboru`Parser` třídy poskytnutím cesty k souboru Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Váš kód zde...
}
```
## Krok 2: Načtení obrázků z dokumentu aplikace Excel
 Použijte`GetImages()` metoda extrahování obrázků ze souboru aplikace Excel.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Krok 3: Definujte možnosti extrakce obrázku
Zadejte formát obrázku a další možnosti pro ukládání extrahovaných obrázků. Chcete-li například uložit obrázky ve formátu PNG:
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Krok 4: Opakujte a uložte obrázky
Iterujte extrahované obrázky a uložte každý obrázek do souboru.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Uložte obrázek do souboru PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Závěr
V tomto tutoriálu jste se naučili používat GroupDocs.Parser for .NET k extrahování obrázků z dokumentu aplikace Excel. Pomocí těchto kroků můžete efektivně začlenit možnosti extrakce obrázků do aplikací .NET.

## FAQ
### Otázka: Může GroupDocs.Parser extrahovat obrázky z jiných formátů dokumentů kromě Excelu?
Odpověď: Ano, GroupDocs.Parser podporuje širokou škálu formátů dokumentů včetně Wordu, PowerPointu, PDF a dalších.
### Otázka: Jak mohu získat podporu nebo pomoc s integrací GroupDocs.Parser?
 Odpověď: Podporu a pomoc získáte na adrese[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Otázka: Je GroupDocs.Parser zdarma k použití?
 Odpověď: GroupDocs.Parser nabízí bezplatnou zkušební verzi, ale pro další používání si možná budete muset zakoupit licenci. Zkontrolovat[ceny a licencování](https://purchase.groupdocs.com/buy)podrobnosti.
### Otázka: Mohu vyzkoušet GroupDocs.Parser před zakoupením licence?
 Odpověď: Ano, můžete získat a[zkušební verze zdarma](https://releases.groupdocs.com/) k vyhodnocení GroupDocs.Parser.
### Otázka: Kde najdu podrobnou dokumentaci k GroupDocs.Parser?
 Odpověď: Viz souhrn[dokumentace](https://tutorials.groupdocs.com/parser/net/) pro podrobné informace o používání GroupDocs.Parser.