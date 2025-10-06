---
title: Képek kibontása a Word dokumentumból
linktitle: Képek kibontása a Word dokumentumból
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan bonthat ki képeket Word-dokumentumból a GroupDocs.Parser for .NET segítségével. Ez az oktatóanyag lépésről lépésre útmutatást nyújt a kép .NET-be való integrálásához.
weight: 11
url: /hu/net/word-document-processing/extract-images-from-word-document/
type: docs
---
# Képek kibontása a Word dokumentumból

## Bevezetés
Ebből az oktatóanyagból megtudhatja, hogyan bonthat ki képeket Word-dokumentumból a GroupDocs.Parser for .NET segítségével. A GroupDocs.Parser egy hatékony .NET-könyvtár, amely lehetővé teszi szövegek, metaadatok, képek és egyebek elemzését és kinyerését különféle dokumentumformátumokból, köztük a Wordből (DOCX).
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy beállította a következő előfeltételeket:
- Visual Studio telepítve van a gépedre.
- C# programozási alapismeretek.
-  GroupDocs.Parser for .NET könyvtár telepítve. Letöltheti innen[itt](https://releases.groupdocs.com/parser/net/).
## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# projektbe a GroupDocs.Parser funkcióinak használatához:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Most bontsuk le egyszerű lépésekre a képek Word-dokumentumból való kinyerésének folyamatát:
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Először létrehoz egy példányt a`Parser`osztályban, megadva bemenetként a Word-dokumentum elérési útját.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Itt található a képkivonat kódja
}
```
## 2. lépés: Képek kibontása a Word-dokumentumból
 Ezután használja a`GetImages()` módszere a`Parser` objektumot a képek kinyeréséhez a dokumentumból.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3. lépés: Adja meg a képmentési beállításokat
Adja meg a kibontott képek mentési beállításait. Például kiválaszthatja a képformátumot (pl. PNG) és konfigurálhat más beállításokat.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 4. lépés: Ismételje meg a kibontott képeket, és mentse
Ismételje meg az egyes kibontott képeket, és mentse el egy fájlba a megadott beállításokkal.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Mentse el a képet PNG fájlba
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Következtetés
Ebből az oktatóanyagból megtanulta, hogyan bonthat ki képeket Word-dokumentumból a GroupDocs.Parser for .NET segítségével. Az alábbi lépések követésével könnyedén integrálhatja a dokumentumelemzési és képkivonatolási lehetőségeket .NET-alkalmazásaiba.

## GYIK
### A GroupDocs.Parser ki tudja kinyerni a képeket más dokumentumformátumokból a Word mellett?
Igen, a GroupDocs.Parser különféle dokumentumformátumokat támogat, beleértve a PDF, PowerPoint, Excel és egyebeket.
### Hogyan szerezhetek ideiglenes licencet a GroupDocs.Parser számára?
 Ideiglenes licencet tesztelési célból szerezhet be[itt](https://purchase.groupdocs.com/temporary-license/).
### Hol találok további dokumentációt a GroupDocs.Parser for .NET-hez?
 A teljes dokumentációra hivatkozhat[itt](https://tutorials.groupdocs.com/parser/net/).
### Van ingyenes próbaverzió a GroupDocs.Parser számára?
 Igen, ingyenes próbaverzióval felfedezheti a GroupDocs.Parser szolgáltatásait[itt](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást, vagy hogyan tehetek fel kérdéseket a GroupDocs.Parser-rel kapcsolatban?
 Kérdéseit felteheti a[GroupDocs.Parser fórum](https://forum.groupdocs.com/c/parser/17).