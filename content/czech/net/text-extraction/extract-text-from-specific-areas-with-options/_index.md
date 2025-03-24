---
title: Extrahujte text ze specifických oblastí pomocí možností
linktitle: Extrahujte text ze specifických oblastí pomocí možností
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat text z konkrétních oblastí v dokumentech pomocí GroupDocs.Parser for .NET. Prozkoumejte pokročilé možnosti extrakce textu s tímto výukovým programem.
weight: 14
url: /cs/net/text-extraction/extract-text-from-specific-areas-with-options/
---

# Extrahujte text ze specifických oblastí pomocí možností

## Úvod
V tomto tutoriálu prozkoumáme, jak pomocí GroupDocs.Parser for .NET extrahovat text z konkrétních oblastí v dokumentu pomocí přizpůsobitelných možností. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům snadno analyzovat a extrahovat text z různých formátů dokumentů.
## Předpoklady
Než se pustíme do kódování, ujistěte se, že máte následující:
1. Vývojové prostředí: Nainstalujte Visual Studio nebo jakékoli jiné vývojové IDE .NET.
2.  Knihovna GroupDocs.Parser: Stáhněte a nainstalujte GroupDocs.Parser for .NET z[tady](https://releases.groupdocs.com/parser/net/).
3. Vzorový soubor: Připravte si vzorový dokument (např. PDF, DOCX atd.), ze kterého chcete extrahovat text.

## Import jmenných prostorů
Nejprve budete muset importovat potřebné jmenné prostory pro přístup ke třídám a metodám GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Vytvořte instanci třídy analyzátoru
 Inicializujte instanci souboru`Parser` třídy poskytnutím cesty k vašemu ukázkovému souboru.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kód pro extrakci textové oblasti bude zde
}
```
## Krok 2: Definujte možnosti extrakce textové oblasti
 Vytvořit`PageTextAreaOptions` specifikovat kritéria pro extrakci textu.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
V tomto příkladu:
- `"\\s[a-z]{2}\\s"` je vzor regulárního výrazu, který odpovídá textovým oblastem obsahujícím pouze malá písmena.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` definuje obdélník (umístění a velikost) na stránce, ze kterého se má extrahovat text.
## Krok 3: Extrahujte textové oblasti
Pomocí definovaných voleb extrahujte oblasti textu, které splňují zadaná kritéria.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Krok 4: Zkontrolujte a iterujte extrahované textové oblasti
Zkontrolujte, zda je podporována extrakce textové oblasti, a poté extrahované oblasti iterujte.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Závěr
V tomto tutoriálu jsme se zabývali tím, jak extrahovat text z konkrétních oblastí v dokumentu pomocí GroupDocs.Parser for .NET. Tato knihovna nabízí rozsáhlé možnosti pro analýzu různých formátů dokumentů, což z ní činí cenný nástroj pro úlohy extrakce textu.

## FAQ
### Může GroupDocs.Parser extrahovat text z naskenovaných dokumentů?
Ano, GroupDocs.Parser podporuje extrakci textu naskenovaných dokumentů na základě OCR.
### Je GroupDocs.Parser kompatibilní s více formáty dokumentů?
Ano, umí analyzovat a extrahovat text z PDF, DOCX, XLSX, PPTX a dalších oblíbených formátů.
### Poskytuje GroupDocs.Parser podporu pro .NET Core?
Ano, GroupDocs.Parser je kompatibilní s .NET Core i .NET Framework.
### Mohu extrahovat metadata spolu s textem pomocí GroupDocs.Parser?
Ano, z dokumentů můžete extrahovat jak textový obsah, tak metadata.
### Je k dispozici zkušební verze pro GroupDocs.Parser?
 Ano, můžete získat bezplatnou zkušební verzi od[tady](https://releases.groupdocs.com/).