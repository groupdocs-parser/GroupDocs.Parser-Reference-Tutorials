---
title: Szöveg kibontása az oldalról nyers módban
linktitle: Szöveg kibontása az oldalról nyers módban
second_title: GroupDocs.Parser .NET API
description: Ebben az átfogó oktatóanyagban tanulhat meg hatékony szövegkivonást a dokumentumoldalakról a Groupdocs.Parser for .NET segítségével.
type: docs
weight: 17
url: /hu/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## Bevezetés
Ebből az oktatóanyagból megtudhatja, hogyan használhatja a Groupdocs.Parser for .NET-et a dokumentumoldalak szövegének nyers módban történő kinyerésére. Ez a könyvtár hatékony eszközöket biztosít a különböző fájlformátumok tartalmának elemzéséhez és kibontásához, lehetővé téve a fejlesztők számára, hogy beépítsék a dokumentumszöveg-kivonást .NET-alkalmazásaikba.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
- C# és .NET programozási alapismeretek
- A Visual Studio telepítve van a gépedre
- Hozzáférés a Groupdocs.Parser for .NET könyvtárhoz
- Dokumentumfájl minta teszteléshez

## Névterek importálása
Kezdje azzal, hogy belefoglalja a szükséges névtereket a C# projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. lépés: Inicializálja az elemzőt
 Először hozzon létre egy példányt a`Parser` osztályba, megadva a mintadokumentumfájl elérési útját.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Itt a kódod
}
```
## 2. lépés: A dokumentumadatok lekérése
 Információk lekérése a dokumentumról a segítségével`GetDocumentInfo()` módszer.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## 3. lépés: Ismételje meg az oldalakat és vonja ki a szöveget
Ismételje meg a dokumentum minden oldalát, és bontsa ki a szöveges tartalmat.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Szöveg kibontása az oldalról
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Következtetés
Most már megtanulta, hogyan kell használni a Groupdocs.Parser for .NET alkalmazást a dokumentumoldalak szövegének nyers módban történő kinyerésére. Ez egy hatékony funkció lehet olyan alkalmazások számára, amelyeknek különféle fájlformátumokból származó szöveges tartalmakat kell elemezniük vagy feldolgozniuk.

## GYIK
### A Groupdocs.Parser for .NET kompatibilis az összes fájlformátummal?
A Groupdocs.Parser a fájlformátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX, EPUB és egyebeket.
### Kivonhatom a metaadatokat a szöveggel együtt ezzel a könyvtárral?
Igen, a Groupdocs.Parser lehetővé teszi a szöveg és a metaadatok kinyerését a dokumentumokból.
### Létezik próbaverzió tesztelésre?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).
### Hogyan kaphatok technikai támogatást a Groupdocs.Parser számára?
 Technikai segítségért keresse fel a[Groupdocs.Parser fórum](https://forum.groupdocs.com/c/parser/17).
### Hol vásárolhatok licencet a Groupdocs.Parser for .NET számára?
 Vásárolhat licencet[itt](https://purchase.groupdocs.com/buy).