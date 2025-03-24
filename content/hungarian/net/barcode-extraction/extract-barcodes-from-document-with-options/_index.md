---
title: Vonja ki a vonalkódokat a dokumentumból az opciókkal
linktitle: Vonja ki a vonalkódokat a dokumentumból az opciókkal
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan vonhat ki vonalkódokat dokumentumokból a GroupDocs.Parser for .NET segítségével. Átfogó oktatóanyag kódpéldákkal és GYIK-vel.
weight: 14
url: /hu/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük a vonalkódok dokumentumból történő kinyerésének folyamatát a GroupDocs.Parser for .NET segítségével. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi szövegek, metaadatok és vonalkódok kinyerését különféle dokumentumformátumokból, például PDF, Microsoft Word, Excel és egyebekből.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételeket teljesítette:
1. Fejlesztési környezet: Győződjön meg arról, hogy a Visual Studio telepítve van a gépen.
2.  GroupDocs.Parser Library: Töltse le és telepítse a GroupDocs.Parser for .NET könyvtárat innen[itt](https://releases.groupdocs.com/parser/net/).
3. Mintadokumentum: Készítsen vonalkódokat tartalmazó mintadokumentumot (pl. PDF, DOCX) a kivonathoz.

## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# projektbe a GroupDocs.Parser funkciók használatához.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 A kezdéshez hozzon létre egy példányt a`Parser` osztályt a mintadokumentum elérési útjának átadásával.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // A kódot a következő lépésekben kell hozzáadni
}
```
## 2. lépés: Ellenőrizze a vonalkód-kivonás támogatását
 Ezután ellenőrizze, hogy a dokumentum támogatja-e a vonalkód-kivonást a`Features` tulajdona a`Parser` példa.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## 3. lépés: Adja meg a vonalkód-kivonási beállításokat
 Most adja meg a vonalkód-kivonás beállításait a segítségével`BarcodeOptions`. Beállíthat olyan paramétereket, mint a minőségi módok és a vonalkód típusok.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## 4. lépés: Vonja ki a vonalkódokat a dokumentumból
 Használja a`GetBarcodes` módszere a`Parser` osztály vonalkódok kinyeréséhez a meghatározott beállítások alapján.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## 5. lépés: Ismételje meg és jelenítse meg a kivont vonalkódokat
Végül ismételje meg a kivont vonalkódokat, és jelenítse meg az oldalindexüket és az értékeket.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Következtetés
 Ebben az oktatóanyagban megtanultuk, hogyan lehet vonalkódokat kivonni egy dokumentumból a GroupDocs.Parser for .NET segítségével. Ez a folyamat magában foglalja a`Parser` például a kivonatolási lehetőségek meghatározása és a kivont vonalkódok iterációja. A GroupDocs.Parser leegyszerűsíti a vonalkód-kivonást a különböző dokumentumformátumokból, lehetővé téve a hatékony dokumentumfeldolgozást a .NET-alkalmazásokon belül.

## GYIK
### A GroupDocs.Parser ki tudja vonni a vonalkódokat PDF dokumentumokból?
Igen, a GroupDocs.Parser támogatja a vonalkód-kivonást PDF-dokumentumokból, más formátumokkal együtt, mint például a DOCX, XLSX stb.
### Milyen vonalkód-típusokat támogat a GroupDocs.Parser?
A GroupDocs.Parser különféle vonalkódtípusokat támogat, beleértve a QR-kódokat, a 39-es kódot, a 128-as kódot és még sok mást.
### A GroupDocs.Parser licencet igényel kereskedelmi használatra?
 Igen, kereskedelmi használatra érvényes engedély szükséges. Engedélyt szerezhet be[itt](https://purchase.groupdocs.com/buy).
### A GroupDocs.Parser alkalmas dokumentumok kötegelt feldolgozására?
Igen, a GroupDocs.Parser hatékonyan tudja kezelni a dokumentumok kötegelt feldolgozását szöveg-, metaadat-visszakeresés és vonalkód-kivonás céljából.
### Hol találok technikai támogatást a GroupDocs.Parser számára?
 Technikai támogatást kaphat, vagy kérdéseket tehet fel a[GroupDocs fórum](https://forum.groupdocs.com/c/parser/17).