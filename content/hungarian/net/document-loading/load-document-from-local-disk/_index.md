---
title: Töltse be a dokumentumot a helyi lemezről
linktitle: Töltse be a dokumentumot a helyi lemezről
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan bonthat ki szöveget különböző dokumentumformátumokból a GroupDocs.Parser for .NET segítségével. Egyszerű és hatékony szövegkivonás C#-val.
weight: 11
url: /hu/net/document-loading/load-document-from-local-disk/
---
## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan használhatja a GroupDocs.Parser for .NET-et szövegek kinyerésére a dokumentumokból. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára a különböző dokumentumformátumok elemzését és a szöveges tartalom programozott kibontását. Leírjuk a szükséges lépéseket a könyvtár használatával történő szövegkivonás megkezdéséhez.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek telepítve vannak:
- A Visual Studio telepítve van a rendszerére.
- C# programozási nyelv alapismerete.
-  A GroupDocs.Parser for .NET könyvtár telepítve (letöltés[itt](https://releases.groupdocs.com/parser/net/)).

## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## 1. lépés: Töltse be a dokumentumot a helyi lemezről
 Kezdje azzal, hogy betölt egy dokumentumot a helyi lemezről. Cserélje ki`"Your Sample File"` a céldokumentum elérési útjával.
```csharp
// Állítsa be a filePath-et
string filePath = "Your Sample File";
// Hozzon létre egy Parser osztály példányt a filePath segítségével
using (Parser parser = new Parser(filePath))
{
    // Szöveg kibontása az olvasóba
    using (TextReader reader = parser.GetText())
    {
        //Nyomtassa ki a kivont szöveget a dokumentumból
        // Ha a szövegkivonás nem támogatott, az olvasó null lesz
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## A lépések magyarázata
1. Fájl elérési útjának beállítása: Először adja meg annak a dokumentumnak az elérési útját, amelyből szöveget szeretne kivonni (`filePath` változó).
2.  Elemző példány létrehozása: Példányosítsa a`Parser` osztály átadásával a`filePath`.
3.  Szöveg kibontása: Használja a`GetText()` módszere a`Parser` példány megszerzésére a`TextReader` a dokumentumból kinyert szöveget tartalmazó objektum.
4.  Kivont szöveg olvasása: Használja a`ReadToEnd()` módszere a`TextReader` a dokumentumból kivont teljes szövegtartalom lekéréséhez.
5.  Nem támogatott formátumok kezelése: Ha a dokumentumformátum nem támogatja a szövegkivonást, a`reader` tárgy lesz`null`, és ennek megfelelően kezelheti ezt a forgatókönyvet.

## Következtetés
Ebben az oktatóanyagban bemutattuk azokat a kezdeti lépéseket, amelyekkel a GroupDocs.Parser for .NET segítségével kinyerhet szöveget egy dokumentumból. Ez a könyvtár kiterjedt funkciókat kínál a dokumentumelemzéshez, lehetővé téve a fejlesztők számára, hogy hatékonyan dolgozzanak különféle fájlformátumokkal az alkalmazásaikban.

## GYIK
### A GroupDocs.Parser kompatibilis az összes dokumentumformátummal?
A GroupDocs.Parser a formátumok széles skáláját támogatja, beleértve a PDF-eket, a Microsoft Office dokumentumokat (Word, Excel, PowerPoint) és még sok mást.
### Kivonhatom a metaadatokat a szöveggel együtt a GroupDocs.Parser segítségével?
Igen, a GroupDocs.Parser lehetővé teszi a szövegtartalom és a metaadatok kinyerését a támogatott dokumentumformátumokból.
### Hol találok további erőforrásokat és támogatást a GroupDocs.Parser számára?
 Meglátogatni a[GroupDocs.Parser dokumentáció](https://tutorials.groupdocs.com/parser/net/) részletes API-referenciáért és fedezze fel a[GroupDocs fórum](https://forum.groupdocs.com/c/parser/17) közösségi támogatásért.
### Hogyan szerezhetek ideiglenes licencet a GroupDocs.Parser számára?
 Kérheti a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/) értékelési és tesztelési célokra.
### Van ingyenes próbaverzió a GroupDocs.Parser számára?
 Igen, letöltheti a[ingyenes próbaverzió](https://releases.groupdocs.com/) a GroupDocs.Parser verziója.