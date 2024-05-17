---
title: Práce s poli na pevných pozicích v šablonách
linktitle: Práce s poli na pevných pozicích v šablonách
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat data z dokumentů pomocí GroupDocs.Parser for .NET. Obsáhlý tutoriál s příklady kódu.
type: docs
weight: 11
url: /cs/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak pracovat s poli na pevných pozicích v šablonách pomocí GroupDocs.Parser for .NET. GroupDocs.Parser je výkonná knihovna pro analýzu dokumentů, která umožňuje vývojářům extrahovat data z různých formátů dokumentů, jako jsou PDF, Word, Excel a další. Konkrétně se zaměříme na definování a využití polí šablony k extrahování cílených informací na základě jejich pevných pozic.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
- Základní znalost vývoje C# a .NET.
- Visual Studio nainstalované ve vašem systému.
- Nainstalovaná knihovna GroupDocs.Parser for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/parser/net/).
- Ukázkové soubory dokumentů pro testování.

## Import jmenných prostorů
Začněte tím, že do svého projektu C# zahrnete potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Krok 1: Definujte pole šablony
Nejprve definujte pole s pevnou pozicí v šabloně. Toto pole představuje oblast, ze které budou data extrahována.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Tady:
- `Rectangle` určuje polohu a velikost pole.
- `Point(35, 135)` představuje souřadnice levého horního rohu.
- `Size(100, 10)` definuje šířku a výšku pole.
- `"FromCompany"` je název přiřazený tomuto poli.
## Krok 2: Vytvořte šablonu
Vytvořte šablonu pomocí definovaného pole.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 The`Template` objekt obsahuje definovaná pole.
## Krok 3: Analyzujte dokument pomocí šablony
 Vytvořte instanci`Parser` třídy s cestou cílového dokumentu a poté dokument analyzujte pomocí vytvořené šablony.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Iterujte extrahovaná data
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Tady:
- `Parser` je inicializována pomocí cesty k souboru vzorového dokumentu.
- `ParseByTemplate` metoda se používá k extrahování dat na základě poskytnuté šablony.
-  K extrahovaným datům se přistupuje pomocí`DocumentData`kde každá položka odpovídá definovanému poli.

## Závěr
V tomto tutoriálu jsme se zabývali procesem práce s poli na pevných pozicích v šablonách pomocí GroupDocs.Parser pro .NET. Definováním šablon se specifickými pozicemi v poli mohou vývojáři přesně extrahovat cílená data z různých formátů dokumentů.

## FAQ
### Je GroupDocs.Parser kompatibilní se všemi formáty dokumentů?
 GroupDocs.Parser podporuje širokou škálu formátů souborů, včetně PDF, Microsoft Word, Excel, PowerPoint a dalších. Odkazovat na[dokumentace](https://reference.groupdocs.com/parser/net/) pro podrobný seznam.
### Jak mohu získat dočasnou licenci pro GroupDocs.Parser?
 Dočasnou licenci pro testovací účely můžete získat od[tady](https://purchase.groupdocs.com/temporary-license/).
### Kde najdu podporu pro GroupDocs.Parser?
 Pro technickou pomoc a diskuse navštivte stránku[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Mohu GroupDocs.Parser před nákupem vyzkoušet?
 Ano, knihovnu můžete prozkoumat pomocí bezplatné zkušební verze[tady](https://releases.groupdocs.com/).
### Jak si koupím licenci pro GroupDocs.Parser?
 Chcete-li zakoupit licenci, navštivte stránku[nákupní stránku](https://purchase.groupdocs.com/buy).