---
title: Rozpoznávání textu v pravoúhlých oblastech
linktitle: Rozpoznávání textu v pravoúhlých oblastech
second_title: GroupDocs.Parser .NET API
description: Naučte se rozpoznávat text v určitých oblastech dokumentů pomocí GroupDocs.Parser for .NET s funkcemi OCR.
weight: 14
url: /cs/net/ocr-extraction/recognizing-text-in-rectangular-regions/
type: docs
---
# Rozpoznávání textu v pravoúhlých oblastech

## Úvod
V tomto tutoriálu prozkoumáme, jak používat GroupDocs.Parser pro .NET k rozpoznání textu v konkrétních obdélníkových oblastech dokumentů. GroupDocs.Parser je výkonná knihovna, která umožňuje vývojářům extrahovat text, metadata a další z různých formátů souborů, včetně PDF, Wordu, Excelu a PowerPointu.
## Předpoklady
Než začneme, ujistěte se, že máte následující nastavení:
-  GroupDocs.Parser for .NET: Stáhněte a nainstalujte knihovnu z[tady](https://releases.groupdocs.com/parser/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné .NET IDE.
- Vzorový dokument: Mějte vzorový soubor (např. PDF, DOCX), který obsahuje text, který má být rozpoznán.

## Import jmenných prostorů
Nejprve budete muset importovat potřebné jmenné prostory do kódu C#:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Krok 1: Inicializujte nastavení analyzátoru
 Začněte nastavením`ParserSettings` s konektorem OCR. Zde použijeme on-premise konektor Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Krok 2: Vytvořte instanci analyzátoru
 Dále vytvořte instanci`Parser` třída s dříve definovaným nastavením:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Kód pokračuje zde
}
```
 Nahradit`"YourSampleFile.pdf"` s cestou k vašemu dokumentu.
## Krok 3: Definujte obdélník OCR
 Definujte v dokumentu obdélník, kde se bude provádět rozpoznávání textu. Například obdélník začínající na`(0, 0)` se šířkou`400` a výška`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Krok 4: Nakonfigurujte možnosti rozpoznávání textu
 Vytvořit`TextOptions` k určení použití OCR spolu s definovaným obdélníkem:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Krok 5: Extrahujte text pomocí OCR
 Použijte`GetText` metoda`Parser` instance s nakonfigurovaným`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Přečtěte si extrahovaný text nebo zpracujte případ „nepodporováno“.
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Závěr
tomto kurzu jsme si ukázali, jak využít GroupDocs.Parser pro .NET k extrahování textu z konkrétních obdélníkových oblastí v dokumentech pomocí OCR. Tento proces lze dále přizpůsobit a integrovat do různých aplikací pro úlohy automatizované extrakce textu.

## FAQ
### Může GroupDocs.Parser extrahovat text z naskenovaných dokumentů?
Ano, GroupDocs.Parser podporuje OCR (Optical Character Recognition) pro extrahování textu z naskenovaných dokumentů.
### Jaké formáty souborů podporuje GroupDocs.Parser?
GroupDocs.Parser podporuje širokou škálu formátů souborů, včetně PDF, DOCX, XLSX, PPTX a dalších.
### Jak mohu zpracovat dokumenty, které nejsou podporovány pro extrakci textu?
 Můžete zkontrolovat, zda je extrakce textu podporována pomocí`TextReader` instance vrácená uživatelem`parser.GetText(options)`.
### Je GroupDocs.Parser vhodný pro rozsáhlé úlohy extrakce textu?
Ano, GroupDocs.Parser je navržen tak, aby efektivně zvládal rozsáhlé úlohy extrakce textu.
### Kde mohu získat podporu pro problémy související s GroupDocs.Parser?
 Pro podporu a diskuse navštivte[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).