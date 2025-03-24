---
title: Formázott szöveg kibontása a dokumentumoldalról
linktitle: Formázott szöveg kibontása a dokumentumoldalról
second_title: GroupDocs.Parser .NET API
description: Formázott szöveg kinyerése a dokumentumoldalakról a GroupDocs.Parser for .NET segítségével. Hatékony és megbízható szövegkivonási megoldás.
weight: 11
url: /hu/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---

# Formázott szöveg kibontása a dokumentumoldalról

## Bevezetés
Ebben az oktatóanyagban végigvezetjük a formázott szöveg kinyerésének folyamatán a dokumentumoldalakról a GroupDocs.Parser for .NET segítségével. Ez a könyvtár lehetővé teszi a szövegek hatékony elemzését és kinyerését különféle dokumentumformátumokból, például PDF, Word, Excel stb.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
- A Visual Studio telepítve van a rendszerére.
- C# programozási alapismeretek.
-  GroupDocs.Parser .NET könyvtárhoz. Letöltheti[itt](https://releases.groupdocs.com/parser/net/).

## Névterek importálása
Először is kezdje a szükséges névterek importálásával a C# projektbe.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Kezdje a példány létrehozásával a`Parser` osztályba, megadva a mintafájl elérési útját.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // A kód ide fog kerülni
}
```
## 2. lépés: Ellenőrizze, hogy a formázott szöveg kibontása támogatott-e
Mielőtt folytatná a szövegkivonást, ellenőrizze, hogy a dokumentum támogatja-e a formázott szövegkivonást.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## 3. lépés: Dokumentuminformációk lekérése
Információk lekérése a dokumentumról, például az oldalak száma.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 4. lépés: Ismételje meg a dokumentumoldalakat és vonja ki a formázott szöveget
Ismételje meg a dokumentum minden oldalát, és bontsa ki a formázott szöveget meghatározott beállításokkal (pl. Markdown formátum).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Következtetés
Most már tudja, hogyan lehet formázott szöveget kivonni a dokumentumoldalakról a GroupDocs.Parser for .NET segítségével. Ez a könyvtár hatékony és könnyen használható megoldást kínál szövegek kinyerésére különféle fájlformátumokból.

## GYIK
### A GroupDocs.Parser képes kezelni a különböző fájlformátumokat?
Igen, a GroupDocs.Parser a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX stb.
### A GroupDocs.Parser kompatibilis a .NET Core-al?
Igen, a GroupDocs.Parser támogatja a .NET Core-t és a .NET-keretrendszert.
### A GroupDocs.Parser megőrzi a szöveg formázását a kibontás során?
Igen, a GroupDocs.Parser meg tudja őrizni a formázást, például a stílusokat és a betűtípusokat a szöveg kibontásakor.
### Kivonhatok képeket és metaadatokat a GroupDocs.Parser segítségével?
Igen, a GroupDocs.Parser lehetővé teszi képek, metaadatok és szövegek kinyerését a dokumentumokból.
### Hogyan kaphatok támogatást a GroupDocs.Parser számára?
 Támogatást kaphat a[GroupDocs.Parser fórum](https://forum.groupdocs.com/c/parser/17).