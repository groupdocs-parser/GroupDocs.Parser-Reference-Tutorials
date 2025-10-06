---
title: Formázott szöveg kibontása a dokumentumból
linktitle: Formázott szöveg kibontása a dokumentumból
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan vonhat ki formázott szöveget dokumentumokból a GroupDocs.Parser for .NET segítségével. Egyszerű és hatékony szövegkivonás az alkalmazásokhoz.
weight: 10
url: /hu/net/formatted-text-extraction/extract-formatted-text-from-document/
type: docs
---
# Formázott szöveg kibontása a dokumentumból

## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan használható a GroupDocs.Parser for .NET formázott szöveg kinyerésére különböző típusú dokumentumokból. A GroupDocs.Parser egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy egyszerűsített és hatékony módon dolgozzanak a dokumentumokkal. Az útmutató végére zökkenőmentesen integrálhatja a szövegkivonási képességeket .NET-alkalmazásaiba.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
- Visual Studio: Győződjön meg arról, hogy a Visual Studio telepítve van a rendszeren.
-  GroupDocs.Parser for .NET: Töltse le és telepítse a GroupDocs.Parser könyvtárat innen[itt](https://releases.groupdocs.com/parser/net/).
- Dokumentumminták: Készítsen mintadokumentumokat (pl. PDF, DOCX) szövegkivonathoz.
## Névterek importálása
Először is adja meg a szükséges névtereket a C# kódban:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 1. lépés: Hozzon létre egy példányt az elemző osztályból
 Kezdje inicializálásával a`Parser` objektum a mintadokumentum elérési útjával.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // A szövegkivonat kódja ide kerül
}
```
 Cserélje ki`"YourSampleFile.pdf"` a dokumentumfájl elérési útjával.

## 2. lépés: A formázott szöveg kibontása
 Belül`using` blokkolja, használja a`GetFormattedText` módszer a formázott szöveg kinyerésére a dokumentumból. Adja meg a kívánt kimeneti formátumot (pl. HTML) a segítségével`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // A formázott szöveg kibontása az olvasóba
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Ellenőrizze, hogy a kivonás támogatott-e
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Olvassa el és jelenítse meg a kivont szöveget
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Következtetés
Gratulálunk! Megtanulta, hogyan lehet formázott szöveget kivonni dokumentumokból a GroupDocs.Parser for .NET segítségével. Ez a sokoldalú könyvtár lehetőséget kínál az alkalmazásokon belüli szövegfeldolgozásra és -elemzésre.

## GYIK
### K: A GroupDocs.Parser ki tudja bontani a szöveget a jelszóval védett dokumentumokból?
V: Igen, a GroupDocs.Parser támogatja a szöveg kinyerését a jelszóval védett dokumentumokból.
### K: Mely dokumentumformátumokat támogatja a GroupDocs.Parser?
V: A GroupDocs.Parser a formátumok széles skáláját támogatja, beleértve a PDF, DOCX, XLSX, PPTX és egyebeket.
### K: Hogyan szerezhetek ideiglenes licencet a GroupDocs.Parser számára?
 V: Ideiglenes engedélyt szerezhet be[itt](https://purchase.groupdocs.com/temporary-license/).
### K: A GroupDocs.Parser támogatja a képek dokumentumokból történő kinyerését?
V: Igen, a GroupDocs.Parser támogatja a képkivonást a szövegkivonat mellett.
### K: Hol találhatok további támogatást, vagy hol tehetek fel kérdéseket a GroupDocs.Parserrel kapcsolatban?
 V: Látogassa meg a[GroupDocs.Parser fórum](https://forum.groupdocs.com/c/parser/17)támogatásért és megbeszélésekért.