---
title: Načíst dokument ze streamu
linktitle: Načíst dokument ze streamu
second_title: GroupDocs.Parser .NET API
description: Naučte se extrahovat text z různých formátů dokumentů v .NET pomocí GroupDocs.Parser. Podrobný průvodce s příklady kódu.
type: docs
weight: 12
url: /cs/net/document-loading/load-document-from-stream/
---
## Úvod
V oblasti zpracování dokumentů v aplikacích .NET je extrahování textu z různých formátů souborů běžným požadavkem. GroupDocs.Parser for .NET nabízí výkonné řešení pro bezproblémovou analýzu a extrahování textu z nejrůznějších dokumentů. Tento tutoriál vás provede procesem využití GroupDocs.Parser k extrahování textu z dokumentů krok za krokem.
## Předpoklady
Než se pustíte do používání GroupDocs.Parser pro .NET, ujistěte se, že máte následující nastavení:
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí .NET.
-  Balíček GroupDocs.Parser for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Parser for .NET z[tady](https://releases.groupdocs.com/parser/net/).
- Ukázky dokumentů: Připravte si vzorové dokumenty pro extrakci textu.
## Import jmenných prostorů
Začněte importováním potřebných jmenných prostorů do vašeho projektu .NET, abyste získali přístup k funkcím GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Následující kroky ukazují, jak extrahovat text z dokumentu pomocí GroupDocs.Parser z datového proudu.
## Krok 1: Načtěte dokument ze streamu
```csharp
// Vytvořte stream
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Vytvořte instanci třídy Parser se streamem
    using (Parser parser = new Parser(stream))
    {
        // Extrahujte text do čtečky
        using (TextReader reader = parser.GetText())
        {
            // Vytiskněte text z dokumentu
            // Pokud extrakce textu není podporována, bude čtečka null
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
V tomto příkladu:
- Otevřeme proud souboru pro soubor dokumentu (`YourSampleFile.docx`).
-  Inicializovat a`Parser` například s proudem.
-  Použití`parser.GetText()` získat a`TextReader` obsahující extrahovaný text.
- Vytiskněte extrahovaný text nebo zprávu, pokud extrakce textu není pro formát dokumentu podporována.
## Závěr
GroupDocs.Parser for .NET zjednodušuje extrakci textu z různých formátů dokumentů a umožňuje vývojářům efektivně zpracovávat a využívat textový obsah ve svých aplikacích. Podle kroků uvedených v tomto kurzu můžete bez problémů integrovat možnosti extrakce textu dokumentu do svých projektů .NET.

## FAQ
### Jaké formáty dokumentů podporuje GroupDocs.Parser pro .NET?
GroupDocs.Parser podporuje širokou škálu formátů dokumentů včetně DOCX, PDF, XLSX, PPTX, EPUB a dalších.
### Může GroupDocs.Parser extrahovat obrázky nebo metadata z dokumentů?
Ano, GroupDocs.Parser dokáže extrahovat obrázky, metadata a text z různých typů dokumentů.
### Je GroupDocs.Parser kompatibilní s aplikacemi .NET Core?
Ano, GroupDocs.Parser je kompatibilní s aplikacemi .NET Framework i .NET Core.
### Jak mohu získat dočasnou licenci pro GroupDocs.Parser?
 Dočasnou licenci můžete získat od[tady](https://purchase.groupdocs.com/temporary-license/).
### Kde najdu další podporu nebo dokumentaci pro GroupDocs.Parser?
 Další podporu získáte na adrese[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) nebo odkazovat na[dokumentace](https://reference.groupdocs.com/parser/net/).
