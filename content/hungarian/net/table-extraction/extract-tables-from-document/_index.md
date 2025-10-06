---
title: Táblázatok kibontása a dokumentumból
linktitle: Táblázatok kibontása a dokumentumból
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan bonthat ki táblákat dokumentumokból a Groupdocs.Parser for .NET segítségével. Kövesse a részletes útmutatót a funkció integrálásához.
weight: 10
url: /hu/net/table-extraction/extract-tables-from-document/
type: docs
---
# Táblázatok kibontása a dokumentumból

## Bevezetés
A Groupdocs.Parser for .NET egy átfogó könyvtár, amely megkönnyíti a dokumentumok elemzését, lehetővé téve olyan értékes információk kinyerését a dokumentumokból, mint például táblázatok, szövegek, metaadatok és egyebek. Ebben az oktatóanyagban kifejezetten a táblázatok kinyerésére összpontosítunk a dokumentumokból a Groupdocs.Parser API használatával.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
- A Visual Studio telepítve van a rendszerére.
- .NET Framework vagy .NET Core telepítve.
- C# programozási alapismeretek.

## Névterek importálása
Először is importálnia kell a szükséges névtereket a Groupdocs.Parser osztályok és metódusok eléréséhez.
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
 Inicializálja a`Parser` osztályba, megadva a mintadokumentum elérési útját.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // A kódod ide kerül
}
```
## 2. lépés: Ellenőrizze a Táblázat kivonási támogatást
 Ellenőrizze, hogy a dokumentum támogatja-e a táblázat kibontását a`Features` tulajdona a`Parser` osztály.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## 3. lépés: Határozza meg a táblázat elrendezését
Határozza meg a kivonatolni kívánt táblák elrendezését`TemplateTableLayout`. Határozza meg az oszlopszélességet és a sormagasságot a dokumentum szerkezete alapján.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## 4. lépés: Állítsa be a táblázat kibontási beállításait
 Teremt`PageTableAreaOptions` a meghatározott elrendezéssel a táblák kibontásának módjának megadásához.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 5. lépés: Táblázatok kibontása
 Használja ki a`GetTables` módszere a`Parser` osztályban táblákat kinyerhet a dokumentumból a megadott beállítások alapján.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## 6. lépés: Iteráció és táblaadatok elérése
A cellaadatok eléréséhez ismételje meg a kibontott táblázatokat és a hozzájuk tartozó sorokat és oszlopokat.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Következtetés
Ebben az oktatóanyagban bemutattuk, hogyan használható a Groupdocs.Parser for .NET a táblák hatékony kinyerésére a dokumentumokból. Ennek a könyvtárnak a képességeit kihasználva zökkenőmentesen integrálhatja a táblakivonást .NET-alkalmazásaiba.

## GYIK
### A Groupdocs.Parser képes kezelni a különböző dokumentumformátumokat?
Igen, a Groupdocs.Parser a dokumentumformátumok széles skáláját támogatja, beleértve a DOCX, PDF, XLSX és egyebeket.
### Elérhető a Groupdocs.Parser for .NET próbaverziója?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást a Groupdocs.Parserrel kapcsolatos lekérdezésekhez?
 Meglátogathatja a[Groupdocs.Parser fórum](https://forum.groupdocs.com/c/parser/17) segítségért.
### Hol vásárolhatok licencet a Groupdocs.Parser számára?
 Engedélyt vásárolhat innen[itt](https://purchase.groupdocs.com/buy).
### Hogyan szerezhetek ideiglenes engedélyt értékelési célból?
 Kaphat ideiglenes engedélyt[itt](https://purchase.groupdocs.com/temporary-license/).