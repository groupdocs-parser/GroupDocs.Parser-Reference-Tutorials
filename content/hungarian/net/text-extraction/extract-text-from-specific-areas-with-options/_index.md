---
title: Szöveg kinyerése adott területekről opciókkal
linktitle: Szöveg kinyerése adott területekről opciókkal
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan bonthat ki szöveget a dokumentumok meghatározott területeiről a GroupDocs.Parser for .NET segítségével. Fedezze fel a speciális szövegkivonási lehetőségeket ezzel az oktatóanyaggal.
weight: 14
url: /hu/net/text-extraction/extract-text-from-specific-areas-with-options/
type: docs
---
# Szöveg kinyerése adott területekről opciókkal

## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan használhatja a GroupDocs.Parser for .NET-et a dokumentum adott területeinek szövegének kinyerésére testreszabható beállításokkal. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy könnyedén elemezzenek és bontsanak ki szöveget különböző dokumentumformátumokból.
## Előfeltételek
Mielőtt belemerülnénk a kódolásba, győződjön meg arról, hogy rendelkezik a következőkkel:
1. Fejlesztői környezet: Telepítse a Visual Studio-t vagy bármely más .NET fejlesztői IDE-t.
2.  GroupDocs.Parser Library: Töltse le és telepítse a GroupDocs.Parser for .NET alkalmazást innen[itt](https://releases.groupdocs.com/parser/net/).
3. Mintafájl: Készítsen egy mintadokumentumot (pl. PDF, DOCX stb.) a szöveg kivonásához.

## Névterek importálása
Először is importálnia kell a szükséges névtereket a GroupDocs.Parser osztályok és metódusok eléréséhez.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Inicializálja a`Parser` osztályba, megadva a mintafájl elérési útját.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // A szövegterület-kivonat kódja ide kerül
}
```
## 2. lépés: Adja meg a szövegterület kivonatolási beállításait
 Teremt`PageTextAreaOptions` a szövegkivonás kritériumainak megadásához.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
Ebben a példában:
- `"\\s[a-z]{2}\\s"` egy reguláris kifejezés minta, amely csak kisbetűket tartalmazó szövegterületekhez illeszkedik.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` meghatározza azt a téglalapot (pozíció és méret) az oldalon, amelyből a szöveget ki kell bontani.
## 3. lépés: Szövegterületek kibontása
Használja a megadott beállításokat a megadott feltételeknek megfelelő szövegterületek kibontásához.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## 4. lépés: Ellenőrizze és ismételje meg a kivont szövegterületeket
Ellenőrizze, hogy a szövegterület-kivonás támogatott-e, majd ismételje meg a kibontott területeket.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Következtetés
Ebben az oktatóanyagban bemutattuk, hogyan lehet szöveget kivonni egy dokumentum bizonyos területeiről a GroupDocs.Parser for .NET segítségével. Ez a könyvtár széleskörű lehetőségeket kínál különféle dokumentumformátumok elemzéséhez, így értékes eszköz a szövegkivonási feladatokhoz.

## GYIK
### A GroupDocs.Parser ki tudja bontani a szöveget a beolvasott dokumentumokból?
Igen, a GroupDocs.Parser támogatja az OCR-alapú szövegkivonást a beolvasott dokumentumokhoz.
### A GroupDocs.Parser kompatibilis több dokumentumformátummal?
Igen, képes elemezni és kivonatolni a szöveget PDF, DOCX, XLSX, PPTX és más népszerű formátumokból.
### A GroupDocs.Parser támogatja a .NET Core-t?
Igen, a GroupDocs.Parser kompatibilis a .NET Core-val és a .NET-keretrendszerrel.
### Kivonhatom a metaadatokat a szöveggel együtt a GroupDocs.Parser segítségével?
Igen, a dokumentumokból szöveges tartalmat és metaadatokat is kinyerhet.
### Elérhető a GroupDocs.Parser próbaverziója?
 Igen, ingyenes próbaverziót kaphat a webhelyen[itt](https://releases.groupdocs.com/).