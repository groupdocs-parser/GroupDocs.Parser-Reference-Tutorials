---
title: Kivonja a hiperhivatkozásokat a dokumentumból
linktitle: Kivonja a hiperhivatkozásokat a dokumentumból
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan bonthat ki hiperhivatkozásokat dokumentumokból a GroupDocs.Parser for .NET segítségével. Bővítse C# alkalmazásait ezzel az egyszerű útmutatóval.
weight: 10
url: /hu/net/hyperlink-extraction/extract-hyperlinks-from-document/
---

# Kivonja a hiperhivatkozásokat a dokumentumból

## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Parser for .NET hatékony képességeit mutatjuk be. Ez egy sokoldalú könyvtár, amely lehetővé teszi a fejlesztők számára, hogy könnyedén kinyerhessenek hiperhivatkozásokat a dokumentumokból. A hiperhivatkozások kinyerése általános követelmény a dokumentumfeldolgozás során, különösen akkor, ha szöveges fájlokkal, például PDF-ekkel vagy Word-dokumentumokkal foglalkozik. A GroupDocs.Parser használatával hatékonyan azonosíthatja és kinyerheti a hiperhivatkozásokat a hozzájuk tartozó URL-ekkel együtt a különböző dokumentumformátumokból.
## Előfeltételek
Mielőtt folytatná ezt az oktatóanyagot, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
- C# programozási alapismeretek
- A Visual Studio telepítve van a rendszerére
-  GroupDocs.Parser for .NET könyvtár, amely letölthető[itt](https://releases.groupdocs.com/parser/net/)
## Névterek importálása
Kezdésként importálja a szükséges névtereket a C# projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```

Most bontsuk le az egyes példákat több lépésre, amelyek végigvezetik Önt a GroupDocs.Parser for .NET segítségével történő hiperhivatkozások kibontásának folyamatán:
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Először példányosítsa a`Parser` osztályban, megadva a mintadokumentum elérési útját:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // A hiperhivatkozás-kivonat kódja ide kerül
}
```
 Cserélje ki`"YourSampleFile.docx"` a céldokumentum elérési útjával.
## 2. lépés: Ellenőrizze a hiperhivatkozások kibontásának támogatását
A hiperhivatkozások kibontása előtt fontos ellenőrizni, hogy a dokumentumformátum támogatja-e a hiperhivatkozások kibontását:
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
Ez a lépés biztosítja, hogy a hiperhivatkozások kivonatolása megvalósítható legyen az adott dokumentumhoz.
## 3. lépés: A hiperhivatkozások kibontása
 Folytassa a hiperhivatkozások kibontását a dokumentumból a`GetHyperlinks()` módszer:
```csharp
IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks();
```
 Ez a sor a következő gyűjteményét kéri le`PageHyperlinkArea` hiperhivatkozási információkat tartalmazó objektumok.
## 4. lépés: Ismételje meg a kivont hiperhivatkozásokat
Iteráljon a kivont hiperhivatkozások gyűjteményén keresztül, és kérje le azok szövegét és URL-címét:
```csharp
foreach (PageHyperlinkArea hyperlink in hyperlinks)
{
    // Nyomtassa ki a hiperhivatkozás szövegét
    Console.WriteLine(hyperlink.Text);
    
    // Nyomtassa ki a hiperhivatkozás URL-jét
    Console.WriteLine(hyperlink.Url);
    Console.WriteLine(); // Üres sort ad hozzá az olvashatóság érdekében
}
```
Iterációval a`hyperlinks` gyűjtemény, elérheti és kinyomtathatja az egyes hiperhivatkozások szövegét és URL-címét.
## Következtetés
Ebben az oktatóanyagban megvizsgáltuk, hogyan lehet hiperhivatkozásokat kivonni a dokumentumokból a GroupDocs.Parser for .NET segítségével. A könyvtár által biztosított funkciókat kihasználva a fejlesztők könnyedén integrálhatják a hiperhivatkozás-kivonatolási képességeket C# alkalmazásaikba.

## GYIK
### A GroupDocs.Parser képes kezelni a hiperhivatkozások kinyerését különböző dokumentumformátumokból?
Igen, a GroupDocs.Parser támogatja a hiperhivatkozások kivonatát számos fájlformátumból, beleértve a PDF, Word, Excel, PowerPoint és egyebeket.
### Van ingyenes próbaverzió a GroupDocs.Parser számára?
 Igen, hozzáférhet a GroupDocs.Parser ingyenes próbaverziójához[itt](https://releases.groupdocs.com/).
### Hol találom a GroupDocs.Parser dokumentációját?
 A GroupDocs.Parser részletes dokumentációja megtalálható[itt](https://tutorials.groupdocs.com/parser/net/).
### Hogyan szerezhetek ideiglenes licencet a GroupDocs.Parser számára?
 Ideiglenes licencet szerezhet a GroupDocs.Parser számára[itt](https://purchase.groupdocs.com/temporary-license/).
### A GroupDocs támogatja a hibaelhárítást?
 Igen, támogatást és hibaelhárítási segítséget kérhet a GroupDocs webhelyen[fórum](https://forum.groupdocs.com/c/parser/17).