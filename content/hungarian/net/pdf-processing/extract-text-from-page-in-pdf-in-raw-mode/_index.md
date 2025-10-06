---
title: Szöveg kibontása az oldalról PDF-ben nyers módban
linktitle: Szöveg kibontása az oldalról PDF-ben nyers módban
second_title: GroupDocs.Parser .NET API
description: Szöveg kinyerése PDF-ekből a GroupDocs.Parser segítségével C#-ban. Tanulja meg a hatékony PDF-szövegkivonást ezzel a hatékony .NET-könyvtárral.
weight: 16
url: /hu/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
type: docs
---
# Szöveg kibontása az oldalról PDF-ben nyers módban

## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan használhatja a GroupDocs.Parser for .NET-et a PDF-dokumentumok oldalaiból nyers módban történő szöveg kinyerésére. A GroupDocs.Parser egy hatékony eszköz, amely lehetővé teszi a fejlesztők számára, hogy programozottan dolgozzanak különféle dokumentumformátumokkal.
## Előfeltételek
Mielőtt elkezdené ezt az oktatóanyagot, győződjön meg arról, hogy rendelkezik az alábbiakkal:
- Visual Studio telepítve van a gépedre.
- C# programozási alapismeretek.
- GroupDocs.Parser for .NET könyvtár, amelyet megtehet[töltse le itt](https://releases.groupdocs.com/parser/net/).
- Egy minta PDF-fájl tesztelési célokra.

## Névterek importálása
Először is importálja a szükséges névtereket a C# projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Kezdésként példányosítsa a`Parser`osztályban, megadva a minta PDF-fájl elérési útját.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // A kódod ide kerül
}
```
## 2. lépés: Szerezze be a dokumentumadatokat, és ismételje meg az oldalakat
Ezután kérje le a dokumentum információit, és ismételje meg az egyes oldalakat a szöveg kibontásához.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // A szövegkivonat kódja ide kerül
}
```
## 3. lépés: Szöveg kibontása minden oldalról
 A cikluson belül használja a`GetText` módszert, amellyel minden oldalról kinyerhet szöveget és kinyomtathatja azokat.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Következtetés
 Ebben az oktatóanyagban megtanultuk, hogyan lehet szöveget kivonni PDF-oldalakból nyers módban a GroupDocs.Parser for .NET használatával. Ez a folyamat magában foglalja a`Parser` például a dokumentum információinak beszerzése, az egyes oldalak iterációja és a szöveg kibontása a`GetText` módszer.

## GYIK
### Mi az a GroupDocs.Parser for .NET?
GroupDocs.Parser for .NET egy dokumentumelemző API, amely lehetővé teszi a fejlesztők számára, hogy programozottan kinyerjenek szöveget, metaadatokat és egyéb információkat különböző fájlformátumokból.
### Hogyan tölthetem le a GroupDocs.Parser for .NET-et?
 A könyvtár letölthető a[GroupDocs webhely](https://releases.groupdocs.com/parser/net/).
### Van ingyenes próbaverzió?
 Igen, elérheti a GroupDocs.Parser for .NET ingyenes próbaverzióját innen[itt](https://releases.groupdocs.com/).
### Hol találok támogatást a GroupDocs.Parser for .NET számára?
 Technikai segítségért és közösségi támogatásért látogassa meg a[GroupDocs fórum](https://forum.groupdocs.com/c/parser/17).
### Hogyan vásárolhatok licencet a GroupDocs.Parser for .NET számára?
 Engedélyt vásárolhat a[vásárlási oldal](https://purchase.groupdocs.com/buy) vagy ideiglenes engedélyt szerezni[itt](https://purchase.groupdocs.com/temporary-license/).