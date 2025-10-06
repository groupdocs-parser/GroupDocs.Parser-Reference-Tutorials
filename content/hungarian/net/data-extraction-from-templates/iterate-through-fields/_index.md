---
title: Iterálás mezőkön keresztül
linktitle: Iterálás mezőkön keresztül
second_title: GroupDocs.Parser .NET API
description: Ismerje meg, hogyan nyerhet ki strukturált adatokat a dokumentumokból a GroupDocs.Parser for .NET segítségével. Bővítse .NET-alkalmazásait dokumentum-adatkinyerési lehetőségekkel.
weight: 11
url: /hu/net/data-extraction-from-templates/iterate-through-fields/
type: docs
---
# Iterálás mezőkön keresztül

## Bevezetés
GroupDocs.Parser for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy adatokat nyerjenek ki különféle dokumentumformátumokból, például PDF, Microsoft Word, Excel és PowerPoint. Ez az oktatóanyag végigvezeti Önt a GroupDocs.Parser használatának folyamatán, amellyel a dokumentummezőket ismételheti, és sablonok segítségével kinyerhet konkrét adatokat. Ennek az oktatóanyagnak a végére képes lesz hatékonyan strukturált adatokat kinyerni a .NET-alkalmazásaiban lévő dokumentumokból.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy beállította a következő előfeltételeket:
- C# programozási alapismeretek.
- Visual Studio telepítve van a gépedre.
- A GroupDocs.Parser for .NET könyvtár telepítve van, és hivatkozott rá a projektben.

## Névterek importálása
A kezdéshez adja hozzá a szükséges névtereket a C# fájlhoz:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Bontsuk le a folyamatot lépésről lépésre.
## 1. lépés: Határozza meg a sablonmezőket
Először reguláris kifejezésekkel határozza meg a dokumentumból kivonni kívánt mezőket.
```csharp
// Határozzon meg egy "ár" mezőt
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Határozzon meg egy "e-mail" mezőt
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Hozzon létre egy sablont meghatározott mezőkkel
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
Ebben a lépésben két mezőt határoztunk meg: az egyiket az árak kivonására (a dollárjel és a számjegyek azonosítják), a másikat pedig az e-mail címek kivonására.
## 2. lépés: Elemezze a dokumentumot
 Ezután használja a`Parser` osztályt a dokumentum elemzéséhez a meghatározott sablon segítségével.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Elemezze a dokumentumot a sablon alapján
    DocumentData data = parser.ParseByTemplate(template);
    // Iteráljon a kivont adatokon keresztül
    for (int i = 0; i < data.Count; i++)
    {
        // Nyomtassa ki a mező nevét
        Console.Write(data[i].Name + ": ");
        // Ellenőrizze, hogy a kivont terület szöveg-e
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Itt inicializáljuk a`Parser` a mintadokumentum elérési útjával, majd elemezze a dokumentumot a meghatározott sablon segítségével. Ezután ismételjük a kivont adatokat, és kinyomtatjuk a mezőneveket a kivont szöveggel együtt.
## Következtetés
Ebben az oktatóanyagban megvizsgáltuk, hogyan használhatja a GroupDocs.Parser for .NET-et bizonyos adatok kinyerésére a dokumentumokból sablonok segítségével. A reguláris kifejezések és sablonok felhasználásával hatékonyan kinyerhet strukturált információkat a különböző dokumentumformátumokból. Kísérletezzen különféle sablonokkal és dokumentumtípusokkal, hogy megfeleljen az Ön speciális kibontási igényeinek.

## GYIK
### GroupDocs.Parser kinyerhet adatokat a beolvasott dokumentumokból?
Igen, a GroupDocs.Parser képes szöveget és metaadatokat kinyerni a beolvasott és kereshető PDF-dokumentumokból egyaránt.
### A GroupDocs.Parser kompatibilis a .NET Core alkalmazásokkal?
Igen, a GroupDocs.Parser támogatja a .NET Core-t a .NET-keretrendszerrel együtt.
### Milyen dokumentumformátumokat támogat a GroupDocs.Parser?
A GroupDocs.Parser a formátumok széles skáláját támogatja, beleértve a PDF, Microsoft Word, Excel, PowerPoint és még sok más formátumot.
### Hogyan kezelhetek nagy dokumentumokat a GroupDocs.Parser segítségével?
A GroupDocs.Parser lehetőséget biztosít adatok kinyerésére nagy dokumentumok meghatározott oldalairól vagy szakaszairól, így biztosítva a hatékony feldolgozást.
### Használhatom a GroupDocs.Parser-t csak szövegkivonathoz?
Igen, a GroupDocs.Parser segítségével egyszerű szöveges tartalmat is kivonhat a dokumentumokból anélkül, hogy bonyolult formázásra lenne szüksége.