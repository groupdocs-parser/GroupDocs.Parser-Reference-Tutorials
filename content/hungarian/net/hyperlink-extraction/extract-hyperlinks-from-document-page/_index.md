---
title: Kivonja a hiperhivatkozásokat a dokumentumoldalról
linktitle: Kivonja a hiperhivatkozásokat a dokumentumoldalról
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan bonthat ki hiperhivatkozásokat dokumentumokból a GroupDocs.Parser for .NET segítségével. Útmutató lépésről lépésre a hiperhivatkozások kivonásához C#-ban.
weight: 11
url: /hu/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---

# Kivonja a hiperhivatkozásokat a dokumentumoldalról

## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan használható a GroupDocs.Parser for .NET hiperhivatkozások kinyerésére a dokumentumokból lépésről lépésre. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára a különböző dokumentumformátumok elemzését, valamint szövegek, metaadatok és egyéb elemek kinyerését.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
- Visual Studio: Telepítse a Visual Studio-t a fejlesztőgépére.
-  GroupDocs.Parser Library: Töltse le és hivatkozzon a GroupDocs.Parser könyvtárra. től lehet kapni[itt](https://releases.groupdocs.com/parser/net/).
- Mintadokumentum: Készítsen tesztelésre egy mintadokumentumot (pl. DOCX, PDF), amely hiperhivatkozásokat tartalmaz.

## Névterek importálása
Először is adja meg a GroupDocs.Parser funkcióinak használatához szükséges névtereket:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. lépés: Hozzon létre elemző példányt
 Példányosítsa a`Parser` osztályt a mintadokumentum elérési útjával.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // A kód ide megy...
}
```
## 2. lépés: Ellenőrizze a hiperhivatkozások kibontásának támogatását
A folytatás előtt győződjön meg arról, hogy a dokumentum támogatja a hiperhivatkozások kibontását.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## 3. lépés: A dokumentum információinak lekérése
Szerezzen be alapvető információkat a dokumentumról, és ellenőrizze, hogy tartalmaz-e oldalakat.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 4. lépés: Ismételje meg a dokumentumoldalakat
Ismételje meg a dokumentum minden oldalát.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Hiperhivatkozások kibontása az aktuális oldalról
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Iterálás a kivont hiperhivatkozásokon keresztül
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Üres sor az olvashatóság érdekében
    }
}
```

## Következtetés
Ebben az oktatóanyagban a GroupDocs.Parser for .NET használatának alapjait mutatjuk be hiperhivatkozások dokumentumokból való kinyerésére. Megtanulta, hogyan kell inicializálni az elemzőt, ellenőrizni a hiperhivatkozások támogatását, lekérni a dokumentuminformációkat, és a dokumentumoldalakon keresztül iterálni a hiperhivatkozások hatékony kibontása érdekében.

## GYIK
### Kivonhatok hiperhivatkozásokat különböző dokumentumformátumokból?
Igen, a GroupDocs.Parser különféle formátumokat támogat, például DOCX, PDF, PPTX stb., a hiperhivatkozások kivonásához.
### A GroupDocs.Parser könnyen integrálható a meglévő .NET alkalmazásokba?
A GroupDocs.Parser egyértelműen egyszerű, és könnyen integrálható .NET-projektjeibe.
### Kivonhatok-e más metaadatokat a hiperhivatkozásokkal együtt a GroupDocs.Parser segítségével?
Igen, a hiperhivatkozásokon kívül szöveget, képeket és metaadatokat is kivonhat a dokumentumokból ezzel a könyvtárral.
### A GroupDocs.Parser kezeli a titkosított vagy jelszóval védett dokumentumokat?
A GroupDocs.Parser képes elemezni a jelszóval védett dokumentumokat, ha megadja a jelszót.
### Létezik próbaverzió, amellyel vásárlás előtt tesztelhető?
 Igen, letölthet egy ingyenes próbaverziót[itt](https://releases.groupdocs.com/).