---
title: Dokumentum betöltése a Streamből
linktitle: Dokumentum betöltése a Streamből
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan bonthat ki szöveget különböző dokumentumformátumokból a .NET-ben a GroupDocs.Parser segítségével. Útmutató lépésről lépésre kódpéldákkal.
weight: 12
url: /hu/net/document-loading/load-document-from-stream/
type: docs
---
# Dokumentum betöltése a Streamből

## Bevezetés
A .NET-alkalmazások dokumentumfeldolgozásának területén általános követelmény a szövegek kinyerése a különböző fájlformátumokból. A GroupDocs.Parser for .NET hatékony megoldást kínál a dokumentumok zökkenőmentes elemzésére és szövegek kinyerésére. Ez az oktatóanyag végigvezeti Önt a GroupDocs.Parser használatával a dokumentumokból szövegek kinyeréséhez lépésről lépésre.
## Előfeltételek
Mielőtt belemerülne a GroupDocs.Parser for .NET használatába, győződjön meg arról, hogy a következő beállításokkal rendelkezik:
- Fejlesztői környezet: Visual Studio vagy bármely más .NET fejlesztői környezet.
-  GroupDocs.Parser for .NET Package: Töltse le és telepítse a GroupDocs.Parser for .NET könyvtárat innen[itt](https://releases.groupdocs.com/parser/net/).
- Dokumentumminták: Készítsen mintadokumentumokat szövegkivonathoz.
## Névterek importálása
Kezdje a szükséges névterek importálásával a .NET-projektbe a GroupDocs.Parser funkciók eléréséhez.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

következő lépések bemutatják, hogyan lehet szöveget kivonni egy dokumentumból a GroupDocs.Parser segítségével egy adatfolyamból.
## 1. lépés: Töltse be a dokumentumot a Streamből
```csharp
// Hozd létre a streamet
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Hozzon létre egy Parser osztály példányt az adatfolyammal
    using (Parser parser = new Parser(stream))
    {
        // Szöveg kibontása az olvasóba
        using (TextReader reader = parser.GetText())
        {
            // Szöveg nyomtatása a dokumentumból
            // Ha a szövegkivonás nem támogatott, az olvasó null lesz
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
Ebben a példában:
- Megnyitunk egy fájlfolyamot a dokumentumfájlhoz (`YourSampleFile.docx`).
-  Inicializálás a`Parser` például a patammal.
-  Használat`parser.GetText()` visszaszerezni a`TextReader` tartalmazza a kivont szöveget.
- Nyomtassa ki a kivonatolt szöveget vagy üzenetet, ha a szövegkivonás nem támogatott a dokumentumformátumban.
## Következtetés
A GroupDocs.Parser for .NET leegyszerűsíti a szövegek kinyerését a különböző dokumentumformátumokból, lehetővé téve a fejlesztők számára a szöveges tartalom hatékony feldolgozását és felhasználását alkalmazásaikban. Az oktatóanyagban ismertetett lépések követésével zökkenőmentesen integrálhatja a dokumentumszöveg-kivonatolási lehetőségeket .NET-projektjeibe.

## GYIK
### Milyen dokumentumformátumokat támogat a GroupDocs.Parser for .NET?
GroupDocs.Parser a dokumentumformátumok széles skáláját támogatja, beleértve a DOCX, PDF, XLSX, PPTX, EPUB stb.
### A GroupDocs.Parser kinyerhet képeket vagy metaadatokat a dokumentumokból?
Igen, a GroupDocs.Parser képes képeket, metaadatokat és szövegeket kinyerni különféle dokumentumtípusokból.
### A GroupDocs.Parser kompatibilis a .NET Core alkalmazásokkal?
Igen, a GroupDocs.Parser a .NET Framework és a .NET Core alkalmazásokkal is kompatibilis.
### Hogyan szerezhetek ideiglenes licencet a GroupDocs.Parser számára?
 Ideiglenes jogosítványt szerezhet be[itt](https://purchase.groupdocs.com/temporary-license/).
### Hol találok további támogatást vagy dokumentációt a GroupDocs.Parser számára?
 További támogatásért keresse fel a[GroupDocs.Parser fórum](https://forum.groupdocs.com/c/parser/17) vagy hivatkozzon a[dokumentáció](https://tutorials.groupdocs.com/parser/net/).
