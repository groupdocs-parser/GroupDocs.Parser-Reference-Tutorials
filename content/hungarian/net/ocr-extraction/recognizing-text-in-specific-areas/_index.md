---
title: Szöveg felismerése meghatározott területeken
linktitle: Szöveg felismerése meghatározott területeken
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan használhatja a GroupDocs.Parser for .NET-et az OCR-képességgel rendelkező dokumentumok meghatározott területeiről szövegek kinyerésére.
weight: 13
url: /hu/net/ocr-extraction/recognizing-text-in-specific-areas/
---

# Szöveg felismerése meghatározott területeken

## Bevezetés
Ebben az oktatóanyagban azt fogjuk megvizsgálni, hogyan használható a GroupDocs.Parser for .NET a dokumentum meghatározott területeinek szöveg felismerésére és kibontására. A GroupDocs.Parser egy hatékony dokumentumelemző könyvtár, amely lehetővé teszi a fejlesztők számára, hogy különféle dokumentumformátumokkal dolgozzanak, beleértve a PDF, Word, Excel, PowerPoint stb. Konkrétan a GroupDocs.Parser OCR (Optical Character Recognition) képességeinek kihasználására fogunk összpontosítani, hogy szöveget kinyerhessünk a dokumentum meghatározott területeiről.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy beállította a következő előfeltételeket:
1. Visual Studio IDE: Győződjön meg arról, hogy a Visual Studio telepítve van a gépen.
2.  GroupDocs.Parser for .NET: Töltse le és telepítse a GroupDocs.Parser for .NET webhelyről[letöltési link](https://releases.groupdocs.com/parser/net/).
3. Dokumentumminták: Készítsen mintafájlokat (pl. PDF, DOCX), amelyekből szöveget szeretne kinyerni.

## Névterek importálása
A kezdéshez importálja a szükséges névtereket a projektbe:
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

Bontsuk le a folyamatot részletes lépésekre a GroupDocs.Parser for .NET használatával:
## 1. lépés: Hozzon létre elemző beállításokat az OCR csatlakozóval
 Először hozzon létre egy példányt a`ParserSettings`osztályt, és inicializálja egy OCR csatlakozóval, mint pl`AsposeOcrOnPremise`:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 2. lépés: Példányosítsa az Elemzőt a beállításokkal
 Ezután hozzon létre egy példányt a`Parser` osztályban a korábban létrehozott átadásával`ParserSettings`:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // A kódrészlet folytatódik...
}
```
 Cserélje ki`"YourSampleFile.pdf"` a céldokumentum elérési útjával.
## 3. lépés: Konfigurálja a szövegterület-kivonási beállításokat
 Hozzon létre egy példányt a`PageTextAreaOptions` az OCR-alapú szövegkivonás engedélyezéséhez:
```csharp
PageTextAreaOptions options = new PageTextAreaOptions(true);
```
 Készlet`true` hogy engedélyezze az OCR-t a jobb szövegfelismerés érdekében.
## 4. lépés: Szövegterületek kibontása
 Invokál`parser.GetTextAreas(options)` szöveges területek kivonásához a dokumentumból:
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## 5. lépés: A kivont szövegterületek feldolgozása
Iteráljon a kivont szövegterületeken, és kérjen le szöveget, pozíciót és méretet:
```csharp
foreach (PageTextArea area in areas)
{
    Console.WriteLine(area.Text);
    Console.WriteLine($"\tPosition: ({area.Rectangle.Left}; {area.Rectangle.Top})");
    Console.WriteLine($"\tSize: ({area.Rectangle.Size.Width}; {area.Rectangle.Size.Height})");
}
```

## Következtetés
Ebben az oktatóanyagban bemutattuk azt a folyamatot, amellyel egy dokumentum adott területeiről szöveget vonhatunk ki a GroupDocs.Parser for .NET segítségével OCR-képességekkel. Az alábbi lépések követésével hatékonyan kihasználhatja a GroupDocs.Parser elemzési funkcióit a szövegkivonási feladatok programozott kezelésére.

## GYIK
### A GroupDocs.Parser ki tudja bontani a szöveget a beolvasott dokumentumokból?
Igen, a GroupDocs.Parser támogatja az OCR-t a dokumentumokon belüli szkennelt képek szövegének kinyerésére.
### Mely dokumentumformátumokat támogatja a GroupDocs.Parser?
A GroupDocs.Parser a formátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX, TXT stb.
### A GroupDocs.Parser alkalmas dokumentumok kötegelt feldolgozására?
Igen, a GroupDocs.Parser hatékonyan tudja kezelni a kötegelt feldolgozási feladatokat a dokumentumok elemzéséhez és kibontásához.
### Testreszabhatom a szövegkivonási beállításokat a GroupDocs.Parser segítségével?
Igen, a GroupDocs.Parser különféle lehetőségeket kínál a szövegkivonat testreszabására az adott követelmények alapján.
### A GroupDocs.Parser támogatja a metaadatok dokumentumokból történő kinyerését?
Igen, a GroupDocs.Parser lehetővé teszi metaadatok, például szerző, létrehozási dátum és egyebek kinyerését a támogatott dokumentumformátumokból.