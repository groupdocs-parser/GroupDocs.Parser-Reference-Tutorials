---
title: Szöveg felismerése téglalap alakú területeken
linktitle: Szöveg felismerése téglalap alakú területeken
second_title: GroupDocs.Parser .NET API
description: Tanulja meg, hogyan lehet szöveget felismerni a dokumentumok meghatározott régióiban az OCR-képességekkel rendelkező GroupDocs.Parser for .NET segítségével.
type: docs
weight: 14
url: /hu/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan használható a GroupDocs.Parser for .NET a dokumentumok meghatározott téglalap alakú régióiban lévő szövegek felismerésére. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy szöveget, metaadatokat és egyebeket kinyerjenek különféle fájlformátumokból, beleértve a PDF, Word, Excel és PowerPoint fájlokat.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy az alábbiakat beállította:
-  GroupDocs.Parser for .NET: Töltse le és telepítse a könyvtárat innen[itt](https://releases.groupdocs.com/parser/net/).
- Fejlesztői környezet: Visual Studio vagy bármely más .NET IDE.
- Mintadokumentum: rendelkezzen egy mintafájllal (pl. PDF, DOCX), amely a felismerendő szöveget tartalmazza.

## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# kódjába:
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
## 1. lépés: Inicializálja az elemző beállításait
 Kezdje a beállításával`ParserSettings` az OCR csatlakozóval. Itt az Aspose OCR helyszíni csatlakozóját fogjuk használni:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 2. lépés: Hozzon létre elemzőpéldányt
 Ezután példányosítsa a`Parser` osztály a korábban meghatározott beállításokkal:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // A kód itt folytatódik
}
```
 Cserélje ki`"YourSampleFile.pdf"` a dokumentum elérési útjával.
## 3. lépés: Határozza meg az OCR-téglalapot
 Határozzon meg egy téglalapot a dokumentumon belül, ahol a szövegfelismerés végrehajtásra kerül. Például egy téglalap, amelynek kezdőpontja`(0, 0)` szélességgel`400` és magasság`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## 4. lépés: Konfigurálja a szövegfelismerési beállításokat
 Teremt`TextOptions` az OCR használatának megadásához a meghatározott téglalappal együtt:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## 5. lépés: Szöveg kibontása az OCR segítségével
 Használja a`GetText` módszere a`Parser` példány a konfigurálttal`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Olvassa el a kivont szöveget, vagy kezelje a „nem támogatott” kis- és nagybetűket
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Következtetés
Ebben az oktatóanyagban bemutattuk, hogyan lehet kihasználni a GroupDocs.Parser for .NET-et a dokumentumok meghatározott téglalap alakú régióiból történő szöveg kivonásához az OCR használatával. Ez a folyamat tovább testreszabható és integrálható különféle alkalmazásokba az automatizált szövegkivonási feladatokhoz.

## GYIK
### A GroupDocs.Parser ki tudja bontani a szöveget a beolvasott dokumentumokból?
Igen, a GroupDocs.Parser támogatja az OCR (optikai karakterfelismerés) funkciót a beolvasott dokumentumok szövegének kinyeréséhez.
### Milyen fájlformátumokat támogat a GroupDocs.Parser?
A GroupDocs.Parser a fájlformátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX stb. fájlokat.
### Hogyan kezelhetem azokat a dokumentumokat, amelyek nem támogatottak a szövegkivonásban?
 Ellenőrizheti, hogy a szövegkivonás támogatott-e a használatával`TextReader` által visszaadott példány`parser.GetText(options)`.
### Alkalmas-e a GroupDocs.Parser nagyszabású szövegkinyerési feladatokra?
Igen, a GroupDocs.Parser célja a nagyszabású szövegkivonási feladatok hatékony kezelése.
### Hol kaphatok támogatást a GroupDocs.Parserrel kapcsolatos problémákhoz?
 Támogatásért és megbeszélésekért keresse fel a[GroupDocs.Parser fórum](https://forum.groupdocs.com/c/parser/17).