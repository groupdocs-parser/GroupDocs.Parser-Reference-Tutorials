---
title: Táblázatok kibontása a dokumentumoldalról
linktitle: Táblázatok kibontása a dokumentumoldalról
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan lehet programozottan táblákat kivonni dokumentumokból a GroupDocs.Parser for .NET segítségével. Ez az átfogó oktatóanyag lépésről lépésre nyújt útmutatást.
weight: 11
url: /hu/net/table-extraction/extract-tables-from-document-page/
---
## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet táblákat kivonni egy dokumentumoldalról a GroupDocs.Parser for .NET segítségével. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy különféle dokumentumformátumokkal dolgozzanak, például PDF, DOCX, XLSX stb. Funkcióinak kiaknázásával hatékonyan kinyerhetünk strukturált adatokat, például táblázatokat ezekből a dokumentumokból, lehetővé téve számunkra az információk programozott kezelését és elemzését.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
- Visual Studio telepítve van a gépedre.
- Alapvető ismeretek a C# és .NET fejlesztésről.
-  GroupDocs.Parser .NET könyvtárhoz. Letöltheti innen[itt](https://releases.groupdocs.com/parser/net/).
- Hozzáférés egy mintadokumentumhoz (PDF, DOCX stb.), amely táblázatokat tartalmaz kivonatolás céljából.

## Névterek importálása
Először is kezdje a szükséges névterek importálásával a C# projektben:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Példányosítsa a`Parser` osztályban, megadva a mintadokumentum elérési útját:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // kódod itt folytatódik...
}
```
## 2. lépés: Ellenőrizze a dokumentumtábla kivonatolási támogatását
A folytatás előtt ellenőrizze, hogy a dokumentum támogatja-e a táblázat kibontását:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## 3. lépés: Határozza meg a táblázat elrendezését
Határozza meg a dokumentumból kinyerendő táblázatok elrendezését. Adja meg az oszlopszélességet és a sormagasságot a dokumentum szerkezetének megfelelően:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Oszlopszélességek
    new double[] { 325, 340, 365, 395 });         // Sormagasságok
```
## 4. lépés: Konfigurálja a táblakivonási beállításokat
Hozzon létre beállításokat a táblázat kibontásához a megadott elrendezés használatával:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 5. lépés: A dokumentum információinak lekérése
Információk lekérése a dokumentumról, beleértve az oldalak számát:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 6. lépés: Ismételje meg a dokumentumoldalakat
A táblázatok kibontásához ismételje meg a dokumentum minden oldalát:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Táblázatok kibontása az aktuális oldalról
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Ismétlés a kivont táblákon keresztül
    foreach (PageTableArea table in tables)
    {
        // Ismételje meg a táblázat sorait
        for (int row = 0; row < table.RowCount; row++)
        {
            // Iteráljon a táblázat oszlopai között
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Szerezd meg a táblázat celláját
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Nyomtassa ki a táblázat cellájának szövegét
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Következtetés
Ebben az oktatóanyagban a táblák dokumentumoldalakról történő kinyerésének folyamatát ismertettük a GroupDocs.Parser for .NET használatával. A megadott lépések követésével zökkenőmentesen integrálhatja a táblakivonási funkciókat .NET-alkalmazásaiba, lehetővé téve a dokumentumokon belüli strukturált adatok hatékony kezelését és manipulálását.

## GYIK
### A GroupDocs.Parser ki tudja bontani a táblákat minden típusú dokumentumból?
A GroupDocs.Parser különféle dokumentumformátumokat támogat, mint például a PDF, DOCX, XLSX és még sok más, lehetővé téve a táblázatok kibontását a kompatibilis fájltípusokból.
### A GroupDocs.Parser for .NET alkalmas nagyméretű dokumentumfeldolgozásra?
Igen, a GroupDocs.Parser nagyméretű dokumentumok hatékony kezelésére készült, így kiterjedt adatkészletek feldolgozására is alkalmas.
### A GroupDocs.Parser megőrzi a formázást a táblázat kibontása során?
Igen, a GroupDocs.Parser megőrzi a formázási részleteket, például a cellaszegélyeket, a szövegstílusokat és az igazításokat a táblázat kibontása során.
### Kivonhatok-e konkrét táblázatokat tartalmi feltételek alapján?
GroupDocs.Parser rugalmas lehetőségeket kínál meghatározott táblák célzására az elrendezési sablonok vagy a kinyerés tartalmi feltételei alapján.
### A GroupDocs.Parser kompatibilis a .NET Core-al?
Igen, a GroupDocs.Parser kompatibilis mind a .NET-keretrendszerrel, mind a .NET Core környezettel.