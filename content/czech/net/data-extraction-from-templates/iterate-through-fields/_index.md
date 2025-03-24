---
title: Iterovat přes pole
linktitle: Iterovat přes pole
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat strukturovaná data z dokumentů pomocí GroupDocs.Parser for .NET. Vylepšete své aplikace .NET o možnosti extrakce dat z dokumentů.
weight: 11
url: /cs/net/data-extraction-from-templates/iterate-through-fields/
---
## Úvod
GroupDocs.Parser for .NET je výkonná knihovna, která umožňuje vývojářům extrahovat data z různých formátů dokumentů, jako je PDF, Microsoft Word, Excel a PowerPoint. Tento tutoriál vás provede procesem používání GroupDocs.Parser k iteraci polí dokumentu a extrahování konkrétních dat pomocí šablon. Na konci tohoto kurzu budete schopni efektivně extrahovat strukturovaná data z dokumentů ve vašich aplikacích .NET.
## Předpoklady
Než začneme, ujistěte se, že máte nastaveny následující předpoklady:
- Základní znalost programování v C#.
- Visual Studio nainstalované na vašem počítači.
- Knihovna GroupDocs.Parser for .NET nainstalovaná a odkazovaná ve vašem projektu.

## Import jmenných prostorů
Chcete-li začít, přidejte do souboru C# potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Pojďme si tento proces rozdělit na pokyny krok za krokem.
## Krok 1: Definujte pole šablony
Nejprve pomocí regulárních výrazů definujte pole, která chcete z dokumentu extrahovat.
```csharp
// Definujte pole „cena“.
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Definujte pole „e-mail“.
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Vytvořte šablonu s definovanými poli
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
tomto kroku jsme definovali dvě pole: jedno pro extrahování cen (identifikované znakem dolaru a číslic) a druhé pro extrahování e-mailových adres.
## Krok 2: Analyzujte dokument
 Dále použijte`Parser` třídy k analýze dokumentu pomocí definované šablony.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analyzujte dokument podle šablony
    DocumentData data = parser.ParseByTemplate(template);
    // Iterujte extrahovaná data
    for (int i = 0; i < data.Count; i++)
    {
        // Tisk názvu pole
        Console.Write(data[i].Name + ": ");
        // Zkontrolujte, zda je extrahovaná oblast textem
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Zde inicializujeme`Parser` s cestou k vašemu vzorovému dokumentu a poté dokument analyzujte pomocí definované šablony. Poté iterujeme extrahovaná data a vytiskneme názvy polí spolu s extrahovaným textem.
## Závěr
V tomto tutoriálu jsme prozkoumali, jak pomocí GroupDocs.Parser for .NET extrahovat konkrétní data z dokumentů pomocí šablon. Využitím regulárních výrazů a šablon můžete efektivně extrahovat strukturované informace z různých formátů dokumentů. Experimentujte s různými šablonami a typy dokumentů, aby vyhovovaly vašim specifickým potřebám extrakce.

## FAQ
### Může GroupDocs.Parser extrahovat data z naskenovaných dokumentů?
Ano, GroupDocs.Parser dokáže extrahovat text a metadata z naskenovaných i prohledávatelných PDF dokumentů.
### Je GroupDocs.Parser kompatibilní s aplikacemi .NET Core?
Ano, GroupDocs.Parser podporuje .NET Core spolu s .NET Framework.
### Jaké formáty dokumentů podporuje GroupDocs.Parser?
GroupDocs.Parser podporuje širokou škálu formátů včetně PDF, Microsoft Word, Excel, PowerPoint a dalších.
### Jak mohu zpracovat velké dokumenty pomocí GroupDocs.Parser?
GroupDocs.Parser poskytuje možnosti pro extrahování dat z konkrétních stránek nebo částí velkých dokumentů, což zajišťuje efektivní zpracování.
### Mohu použít GroupDocs.Parser pouze pro extrakci textu?
Ano, můžete extrahovat obsah prostého textu z dokumentů pomocí GroupDocs.Parser bez nutnosti složitého formátování.