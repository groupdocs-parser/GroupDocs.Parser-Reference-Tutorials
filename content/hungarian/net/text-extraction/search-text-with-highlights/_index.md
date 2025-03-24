---
title: Szöveg keresése a kiemelésekkel
linktitle: Szöveg keresése a kiemelésekkel
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan kereshet és jelölhet ki szöveget dokumentumokban a GroupDocs.Parser for .NET segítségével. Hatékonyan nyerhet ki értékes információkat.
weight: 24
url: /hu/net/text-extraction/search-text-with-highlights/
---

# Szöveg keresése a kiemelésekkel

## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan használhatjuk a GroupDocs.Parser for .NET-et szövegek keresésére egy dokumentumon belül, és kiemeljük a keresési eredményeket. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi, hogy különféle dokumentumformátumokkal dolgozzon, és kivonja a szöveget, a metaadatokat és egyebeket.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
1.  GroupDocs.Parser for .NET: Töltse le és telepítse a könyvtárat innen[itt](https://releases.groupdocs.com/parser/net/).
2. IDE: Használja a Visual Studio-t vagy bármely előnyben részesített IDE-t a .NET fejlesztéshez.
3. Mintafájl: Készítsen mintadokumentumot (pl. PDF, DOCX) a szöveges kereséshez.

## Névterek importálása
Először is importálja a szükséges névtereket a .NET-projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. lépés: Hozzon létre elemző példányt
 Kezdje a példányosítással`Parser` osztály a mintafájl elérési útjával:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Itt a kódod
}
```
## 2. lépés: Adja meg a kiemelési beállításokat
 Adja meg a`HighlightOptions` a keresési eredmények kiemelésének beállításához. Például egy 15 karakteres kontextusablak beállítása:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## 3. lépés: Szöveg keresése
Most végezzen szöveges keresést a dokumentumban. Adja meg a keresni kívánt kulcsszót (pl. "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## 4. lépés: A keresési eredmények feldolgozása
Ismételje meg a keresési eredményeket, és jelenítse meg a talált szöveget a kiemelésekkel együtt:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Következtetés
Ebben az oktatóanyagban megtanulta, hogyan használja a GroupDocs.Parser for .NET-et a dokumentumokon belüli szöveg keresésére és a keresési eredmények kiemelésére. Ez a funkció rendkívül hasznos lehet a .NET-alkalmazások szövegkinyeréséhez és elemzéséhez.

## GYIK
### A GroupDocs.Parser alkalmas különféle dokumentumformátumok feldolgozására?
Igen, a GroupDocs.Parser a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX és egyebeket.
### Használhatom a GroupDocs.Parser-t metaadatok kinyerésére a dokumentumokból?
Teljesen! A GroupDocs.Parser lehetővé teszi metaadatok, szövegek és strukturált adatok kinyerését a dokumentumokból.
### Hol találhatok támogatást, vagy hol tehetek fel kérdéseket a GroupDocs.Parserrel kapcsolatban?
 Meglátogathatja a[GroupDocs.Parser fórum](https://forum.groupdocs.com/c/parser/17) bármilyen támogatással kapcsolatos kérdés esetén.
### Van ingyenes próbaverzió a GroupDocs.Parser számára?
 Igen, hozzáférhet a[ingyenes próbaverzió](https://releases.groupdocs.com/) a GroupDocs.Parser alkalmazásban, hogy kiértékelje szolgáltatásait.
### Hogyan vásárolhatok licencet a GroupDocs.Parser számára?
 Engedélyt vásárolhat innen[itt](https://purchase.groupdocs.com/buy) és ideiglenes engedélyeket is szerezni[itt](https://purchase.groupdocs.com/temporary-license/).