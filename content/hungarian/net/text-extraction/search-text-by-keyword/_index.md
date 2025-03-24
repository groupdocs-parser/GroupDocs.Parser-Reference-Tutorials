---
title: Szöveg keresése kulcsszó szerint
linktitle: Szöveg keresése kulcsszó szerint
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan kereshet szöveget kulcsszó alapján a dokumentumokban a GroupDocs.Parser for .NET segítségével. Könnyedén, hatékonyan nyerhet ki releváns tartalmat.
weight: 21
url: /hu/net/text-extraction/search-text-by-keyword/
---

# Szöveg keresése kulcsszó szerint

## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Parser for .NET használatával foglalkozunk a dokumentumokon belüli kulcsszó szerinti kereséshez. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy szöveget, metaadatokat és egyéb információkat kinyerjenek különféle fájlformátumokból, például PDF-ekből, Microsoft Office dokumentumokból és egyebekből. A konkrét kulcsszavak keresése ezeken a dokumentumokon belül elengedhetetlen lehet a nagy mennyiségű szöveges adattal foglalkozó alkalmazások számára.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy az alábbiakat beállította:
1. Fejlesztői környezet: Visual Studio vagy bármely előnyben részesített .NET IDE.
2.  GroupDocs.Parser for .NET: Töltse le a könyvtárat innen[itt](https://releases.groupdocs.com/parser/net/).
3. Hozzáférés a mintafájlokhoz: Készítsen egy mintafájlt (pl. PDF, DOCX) a kulcsszókereső funkció teszteléséhez.

## Névterek importálása
Először is bele kell foglalnia a szükséges névtereket a projektbe.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## 1. lépés: Példányosítsa az elemző osztályt
 Kezdje a példány létrehozásával a`Parser` osztályt, és adja meg a mintafájl elérési útját.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Keressen egy kulcsszót
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Iteráljon a keresési eredmények között
    foreach (SearchResult result in searchResults)
    {
        //Nyomtassa ki az indexet és a talált szöveget
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## 2. lépés: Keressen rá egy kulcsszóra
 Belül`using` blokkolja, hívja a`Search` módszer a`parser` objektumot, argumentumként átadva a kívánt kulcsszót.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Cserélje ki`"test"` a keresni kívánt kulcsszóval a dokumentumban.
## 3. lépés: Ismételje meg a keresési eredményeket
 Ezután ismételje meg a keresési eredményeket, amelyeket a`Search` módszer segítségével a`foreach` hurok.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Az egyes`SearchResult` tárgy`result` , elérheti azt`Position` (index) és`Text` (a talált szöveg).

## Következtetés
 Ebben az oktatóanyagban megvizsgáltuk, hogyan használhatja a GroupDocs.Parser for .NET-et a szöveges kulcsszó szerinti kereséshez a dokumentumokon belül. Kihasználva a`Search` módszere a`Parser` osztály lehetővé teszi a releváns szövegrészletek hatékony visszakeresését meghatározott keresési kifejezések alapján.

## GYIK
### A GroupDocs.Parser kompatibilis a különböző dokumentumformátumokkal?
Igen, a GroupDocs.Parser a fájlformátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX stb. fájlokat.
### Végezhetek speciális szövegkivonási műveleteket a GroupDocs.Parser segítségével?
Teljesen! A szöveges keresésen kívül a GroupDocs.Parser lehetővé teszi a metaadatok kinyerését, a strukturált szöveg kinyerését stb.
### Hol találom a GroupDocs.Parser részletes dokumentációját?
Fedezze fel a teljes dokumentációt[itt](https://tutorials.groupdocs.com/parser/net/).
### Hogyan kaphatok támogatást vagy segítséget a GroupDocs.Parserrel kapcsolatos lekérdezésekhez?
 Keresse fel a GroupDocs fórumot támogatásért és megbeszélésekért[itt](https://forum.groupdocs.com/c/parser/17).
### Rendelkezésre áll a GroupDocs.Parser próbaverziója a vásárlás előtt?
 Igen, hozzáférhet az ingyenes próbaverzióhoz[itt](https://releases.groupdocs.com/).