---
title: Szöveg keresése reguláris kifejezéssel (Regex)
linktitle: Szöveg keresése reguláris kifejezéssel (Regex)
second_title: GroupDocs.Parser .NET API
description: Tanulja meg, hogyan kereshet szöveget reguláris kifejezésekkel a dokumentumokban a GroupDocs.Parser for .NET segítségével. Konkrét tartalmat könnyedén kivonat.
weight: 23
url: /hu/net/text-extraction/search-text-by-regex/
---
## Bevezetés
Ebben az oktatóanyagban elmélyülünk a GroupDocs.Parser for .NET használatával szöveges kereséshez reguláris kifejezéssel (Regex) a dokumentumokon belül. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy szöveget és metaadatokat kinyerjenek különféle fájlformátumokból, például PDF, DOCX, XLSX stb. Szöveg keresése reguláris kifejezésekkel különösen hasznos a minták vagy konkrét tartalom hatékony megtalálásához a dokumentumokban.
## Előfeltételek
Mielőtt belevágna ebbe az oktatóanyagba, győződjön meg arról, hogy rendelkezik az alábbiakkal:
1. Visual Studio: Telepítse a Visual Studio IDE-t a .NET-fejlesztéshez.
2.  GroupDocs.Parser for .NET: Töltse le és telepítse a GroupDocs.Parser for .NET-et innen[itt](https://releases.groupdocs.com/parser/net/).
3. Mintafájl: Készítsen mintadokumentumot (PDF, DOCX stb.) a keresési funkció teszteléséhez.

## Névterek importálása
Először is vegye fel a szükséges névtereket a C# kódba:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Példányosítsa a`Parser` osztályban, megadva a mintafájl elérési útját:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // A kód ide kerül
}
```
 Cserélje ki`"YourSampleFile.pdf"` a tényleges fájl elérési útjával.
## 2. lépés: Keresés reguláris kifejezéssel
Határozza meg és hajtsa végre a keresést reguláris kifejezésmintával. Például numerikus sorozatok (pl. egész számok) kereséséhez a dokumentumban:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 Ebben a példában`[0-9]+` egy reguláris kifejezés minta, amely egy vagy több számjegynek felel meg.
## 3. lépés: Ellenőrizze a keresési támogatást
Ellenőrizze, hogy a keresési művelet támogatott-e a dokumentumtípushoz:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## 4. lépés: Ismételje meg a keresési eredményeket
Ismételje meg a keresési eredményeket, és dolgozzon fel minden egyezést:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Ez a hurok kinyomtatja a dokumentumban található pozíciót és egyező szöveget.

## Következtetés
Összefoglalva, a GroupDocs.Parser for .NET kihasználása hatékony szövegkeresést tesz lehetővé reguláris kifejezések használatával a különböző dokumentumformátumokban. Az útmutató követésével a fejlesztők zökkenőmentesen integrálhatják a dokumentumelemzést és a regex-alapú szövegkivonást .NET-alkalmazásaikba.

## GYIK
### GroupDocs.Parser tud keresni a titkosított dokumentumokban?
Nem, a GroupDocs.Parser nem tud keresni a titkosított vagy jelszóval védett dokumentumokban.
### A GroupDocs.Parser támogatja az OCR-t (optikai karakterfelismerést)?
Nem, a GroupDocs.Parser nem hajt végre OCR-t. A dokumentum belső szerkezetéből származó szövegkivonatokra támaszkodik.
### Kereshetek összetett mintákat reguláris kifejezésekkel?
Igen, a GroupDocs.Parser támogatja a teljes értékű reguláris kifejezéseket, lehetővé téve a dokumentumokon belüli összetett mintaillesztést.
### Mely dokumentumformátumok támogatottak a szövegkivonathoz?
A GroupDocs.Parser a formátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX és sok más formátumot.
### A GroupDocs.Parser kompatibilis a .NET Core-al?
Igen, a GroupDocs.Parser kompatibilis a .NET Core-al a többplatformos fejlesztéshez.