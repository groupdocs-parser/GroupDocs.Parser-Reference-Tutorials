---
title: Načíst dokument z místního disku
linktitle: Načíst dokument z místního disku
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat text z různých formátů dokumentů pomocí GroupDocs.Parser for .NET. Snadná a efektivní extrakce textu pomocí C#.
type: docs
weight: 11
url: /cs/net/document-loading/load-document-from-local-disk/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak používat GroupDocs.Parser pro .NET k extrahování textu z dokumentů. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům analyzovat různé formáty dokumentů a programově extrahovat textový obsah. Probereme nezbytné kroky, jak začít s extrakcí textu pomocí této knihovny.
## Předpoklady
Než začneme, ujistěte se, že máte nainstalované následující předpoklady:
- Visual Studio nainstalované ve vašem systému.
- Základní znalost programovacího jazyka C#.
-  Nainstalovaná knihovna GroupDocs.Parser for .NET (stáhnout[tady](https://releases.groupdocs.com/parser/net/)).

## Import jmenných prostorů
Nejprve musíte do svého projektu C# importovat potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Krok 1: Načtěte dokument z místního disku
 Začněte načtením dokumentu z místního disku. Nahradit`"Your Sample File"` s cestou k cílovému dokumentu.
```csharp
// Nastavte cestu k souboru
string filePath = "Your Sample File";
// Vytvořte instanci třídy Parser s filePath
using (Parser parser = new Parser(filePath))
{
    // Extrahujte text do čtečky
    using (TextReader reader = parser.GetText())
    {
        //Vytiskněte extrahovaný text z dokumentu
        // Pokud extrakce textu není podporována, bude čtečka null
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Vysvětlení kroků
1. Nastavení cesty k souboru: Začněte zadáním cesty k dokumentu, ze kterého chcete extrahovat text (`filePath` proměnná).
2.  Vytvoření instance analyzátoru: Vytvořte instanci`Parser` třídy absolvováním`filePath`.
3.  Extrahování textu: Použijte`GetText()` metoda`Parser` příklad k získání a`TextReader` objekt obsahující extrahovaný text z dokumentu.
4.  Čtení extrahovaného textu: Použijte`ReadToEnd()` metoda`TextReader` k načtení celého textového obsahu extrahovaného z dokumentu.
5.  Zacházení s nepodporovanými formáty: Pokud formát dokumentu nepodporuje extrakci textu,`reader` objekt bude`null`a podle toho můžete tento scénář zpracovat.

## Závěr
tomto tutoriálu jsme probrali počáteční kroky k extrahování textu z dokumentu pomocí GroupDocs.Parser for .NET. Tato knihovna nabízí rozsáhlé funkce pro analýzu dokumentů a umožňuje vývojářům efektivně pracovat s různými formáty souborů v rámci jejich aplikací.

## FAQ
### Je GroupDocs.Parser kompatibilní se všemi formáty dokumentů?
GroupDocs.Parser podporuje širokou škálu formátů včetně PDF, dokumentů Microsoft Office (Word, Excel, PowerPoint) a dalších.
### Mohu extrahovat metadata spolu s textem pomocí GroupDocs.Parser?
Ano, GroupDocs.Parser umožňuje extrakci textového obsahu i metadat z podporovaných formátů dokumentů.
### Kde najdu další zdroje a podporu pro GroupDocs.Parser?
 Navštivte[GroupDocs.Parser dokumentace](https://reference.groupdocs.com/parser/net/) pro podrobnou referenci API a prozkoumejte[Fórum GroupDocs](https://forum.groupdocs.com/c/parser/17) za podporu komunity.
### Jak mohu získat dočasnou licenci pro GroupDocs.Parser?
 Můžete požádat a[dočasná licence](https://purchase.groupdocs.com/temporary-license/) pro účely hodnocení a testování.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Parser?
 Ano, můžete si stáhnout a[zkušební verze zdarma](https://releases.groupdocs.com/) verze GroupDocs.Parser.