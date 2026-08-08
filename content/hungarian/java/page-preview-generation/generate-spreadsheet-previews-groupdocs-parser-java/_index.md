---
date: '2026-07-16'
description: Ismerje meg, hogyan hozhat létre táblázat bélyegképet Java-val a GroupDocs.Parser
  segítségével, előnézetet készíthet az Excel-hez Office nélkül, és megjelenítheti
  az Excel munkalapokat képként. Ez az útmutató bemutatja a beállítást, a megvalósítást
  és a gyakorlati felhasználási eseteket.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: Táblázat bélyegkép létrehozása Java-val a GroupDocs.Parser segítségével
  – előnézet készítése Excel-hez Office nélkül, és Excel munkalapok megjelenítése
  képként. Kövesse ezt a lépésről‑lépésre útmutatót a PNG előnézetek hatékony előállításához.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: Táblázat bélyegkép létrehozása Java-val a GroupDocs.Parser használatával
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: Táblázat bélyegkép létrehozása Java-val a GroupDocs.Parser használatával
type: docs
url: /hu/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Táblázat bélyegkép létrehozása Java-val a GroupDocs.Parser használatával

Ha **create spreadsheet thumbnail Java** programokat keresel, jó helyen jársz. Ebben az útmutatóban bemutatjuk, hogyan generálhatunk magas minőségű PNG előnézeteket `.xlsx` munkafüzetekből a GroupDocs.Parser for Java segítségével – tökéletes gyors bélyegképekhez, pillanatképek megosztásához vagy dokumentum‑előnézet funkció építéséhez az alkalmazásodban. A megoldás Microsoft Office telepítése nélkül működik, és nagy munkafüzetek esetén is alacsony memóriahasználattal skálázható.

## Gyors válaszok
- **Mi jelent a „preview Excel”?** Képfájlok (pl. PNG) generálása, amelyek minden munkalap oldalát ábrázolják.  
- **Melyik formátum ajánlott?** A PNG veszteségmentes minőséget biztosít, és jól működik webes bélyegképekhez.  
- **Szükségem van licencre?** Egy ingyenes próba verzió fejlesztéshez megfelelő; a termeléshez kereskedelmi licenc szükséges.  
- **Módosíthatom a kép felbontását?** Igen – állítsd be a DPI‑t a `PreviewOptions`‑ban.  
- **Lehetséges más formátumok előnézetét is készíteni?** A GroupDocs.Parser támogatja a PDF, Word és számos képformátum előnézetét is.

## Mi az a „hogyan előnézet Excel” a GroupDocs.Parser-rel?
Töltsd be az Excel munkafüzetet, és rendereld minden munkalapot PNG képként anélkül, hogy Microsoft Office-ra lenne szükség. A GroupDocs.Parser egyesével streameli az oldalakat, veszteségmentes bélyegképeket készítve, amelyeket lemezre menthetünk vagy HTTP‑n keresztül visszaküldhetünk, így ideális web‑alapú előnézeti szolgáltatásokhoz.

A GroupDocs.Parser beolvassa az Excel munkafüzeteket, minden munkalapot vizuális oldalként renderel, és lehetővé teszi ezen oldalak képfájlokba való streamelését. Ez megszünteti az Office interop vagy harmadik fél konverterek szükségességét.

## Miért használjuk a GroupDocs.Parser-t Excel előnézetekhez?
A GroupDocs.Parser-t azért érdemes használni, mert bármely Java szerveren működik, nem igényel Office telepítést, nagy munkafüzeteket kezel alacsony memóriaigénnyel, és konfigurálható DPI‑val veszteségmentes PNG képeket állít elő. Az SDK **100+ bemeneti és kimeneti formátumot** támogat, egy 200 oldalas munkafüzetet 3 másodperc alatt képes feldolgozni, és a memóriahasználatot laponként 50 MB alatt tartja.

- **Nincs szükség Office telepítésére** – bármely szerver‑oldali Java környezetben fut.  
- **Nagy fájlok támogatása** – egyesével streameli az oldalakat, alacsony memóriahasználatot biztosítva.  
- **Magas minőségű kimenet** – DPI, formátum és renderelési beállítások szabályozása.  
- **Kereszt‑formátum rugalmasság** – ugyanaz az API működik PDF‑ek, Word dokumentumok és egyéb formátumok esetén is.

## Előfeltételek
- **Java Development Kit** (8 +).  
- **IDE**, például IntelliJ IDEA vagy Eclipse.  
- **GroupDocs.Parser for Java SDK** – töltsd le [itt](https://releases.groupdocs.com/parser/java/).  
- **Documentation** – lásd a hivatalos [documentation](https://docs.groupdocs.com/parser/java/).  
- **Sample Excel file** (`.xlsx`), amelyet elő szeretnél nézni.  
- **Maven vagy Gradle** (opcionális) a függőségkezeléshez.

## Csomagok importálása
Ezek az importok hozzáférést biztosítanak a parserhez, az előnézeti beállításokhoz és a stream kezelő segédeszközökhöz.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## Lépésről‑lépésre útmutató a táblázat oldal előnézetek generálásához

### 1. lépés: A Parser példány inicializálása
A `Parser` a GroupDocs.Parser központi osztálya, amely olvasási hozzáférést biztosít a táblázatfájlokhoz, és lehetővé teszi az oldalankénti renderelést.  
Hozz létre egy `Parser` objektumot, amely a te Excel munkafüzetedre mutat. A *try‑with‑resources* blokk automatikusan bezárja a parser‑t.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Pro tipp:** Használj abszolút útvonalat vagy konfigurálj egy erőforrás mappát a `FileNotFoundException` elkerüléséhez.

### 2. lépés: Az előnézeti beállítások előkészítése
A `PreviewOptions` a renderelési paramétereket állítja be, például a kimeneti formátumot és a DPI‑t.  
Az `ICreatePageStream` egy callback interfész, amely minden generált oldalhoz egy kimeneti streamet biztosít. Határozd meg, hogyan legyen mentve az egyes oldalak. Az `ICreatePageStream` megvalósítás egy új `FileOutputStream`‑et ad vissza minden munkalap oldalhoz.

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> Ez a lépés, ahol **convert xlsx to png**—a stream PNG adatot ír a lemezre.

### 3. lépés: Delegált csatolása a renderelési információk rögzítéséhez
Ha részletekre van szükséged az egyes renderelt munkalapokról (pl. méretek, munkalap neve), regisztrálj egy callback‑et.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### 4. lépés: Kimeneti formátum és DPI megadása
Válaszd a PNG formátumot képként, és állíts be egy DPI‑t, amely egyensúlyban tartja a minőséget és a fájlméretet.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Állítsd be a DPI‑t, ha kisebb bélyegképekre (pl. 96) vagy nagy felbontású nyomtatásra (pl. 300) van szükség.

### 5. lépés: Az előnézetek generálása
Minden beállítás után hívd meg a `generatePreview`‑t. Az SDK végigiterál minden munkalapon, és meghívja a megadott streamet.

```java
parser.generatePreview(previewOptions);
```

### 6. lépés: A `getOutputPath()` segédfüggvény definiálása
A `getOutputPath()` a lap (munkalap) száma alapján épít fel egy fájlnevet, és visszaadja a kimeneti kép teljes útvonalát. Nyugodtan testreszabhatod a mappaszerkezetet.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Gyakori hibaforrás:** Ha előre nem hozod létre az `output` könyvtárat, `IOException` keletkezik. Hozd létre programozottan vagy győződj meg róla, hogy létezik.

## Teljes működő példa (Egyszerűsített)

Az alábbiakban egy tömör változat látható, amely összekapcsolja az összes elemet. Bemutatja a **create spreadsheet thumbnail Java** munkafolyamatot az elejétől a végéig.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

Futtasd ezt a kódrészletet, és a `output` mappában sorozatban megtalálod a `preview_page_1.png`, `preview_page_2.png`, … fájlokat – mindegyik az eredeti Excel munkafüzet egy munkalapját ábrázolja.

## Gyakori problémák és megoldások
| Probléma | Ok | Megoldás |
|----------|----|----------|
| **Nem jönnek létre képek** | `getOutputPath` érvénytelen könyvtárat ad vissza | Győződj meg róla, hogy a célkönyvtár létezik, vagy hozd létre a `new File("output").mkdirs();` segítségével |
| **Memóriahiány hiba hatalmas fájloknál** | A teljes munkafüzet egyszerre történő betöltése | Használd a streaming megközelítést (ahogy bemutattuk), és dolgozd fel az oldalakat egyesével |
| **Helytelen DPI** | `setDpi` nincs meghívva vagy alapértelmezett (96) értékre van állítva | Hívd meg a `previewOptions.setDpi(kívántÉrték);`‑t a `generatePreview` előtt |
| **Nem támogatott formátum** | Megpróbálsz előnézetet készíteni egy sérült `.xlsx` fájlból | Ellenőrizd a fájlt Excel‑lel, vagy a feldolgozás előtt használd a `Parser.isSupported`‑t |

## Gyakran feltett kérdések

**K: Generálhatok előnézetet PDF‑ekhez és képekhez a GroupDocs.Parser használatával?**  
V: Igen, ugyanaz az API működik PDF‑ek, Word dokumentumok és számos képformátum esetén.

**K: Hogyan változtathatom meg a kimeneti képformátumot?**  
V: Hívd meg a `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`‑t (vagy `Gif`, `Bmp`, stb.).

**K: Teljesítményprobléma merül fel nagyon nagy munkafüzeteknél?**  
V: Az SDK oldalakat streameli, ami alacsony memóriahasználatot biztosít. Nagy fájlok esetén fontold meg a párhuzamos kötegelt feldolgozást.

**K: Hogyan kezeljem a hibákat az előnézet generálása során?**  
V: Tedd a kódot try‑catch blokkokba (ahogy bemutattuk), és naplózd a kivétel részleteit. Győződj meg róla, hogy a stream-ek zárva vannak a `finally` blokkban, ha nem a try‑with‑resources‑t használod.

**K: A könyvtár megköveteli a Microsoft Office telepítését?**  
V: Nem. A GroupDocs.Parser egy tiszta Java megoldás, és bármely, Java 8+‑t támogató platformon működik.

**Utoljára frissítve:** 2026-07-16  
**Tesztelve ezzel:** GroupDocs.Parser 23.11 (a legújabb a írás időpontjában)  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok

- [Hogyan generáljunk előnézetet – Dokumentum oldal előnézet generálási oktatóanyagok a GroupDocs.Parser Java-hoz](/parser/java/page-preview-generation/)
- [Excel Java elemzése a GroupDocs.Parser-rel: Teljes útmutató](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [Hogyan nyerjünk ki nyers szöveget Excel munkalapokból a GroupDocs.Parser for Java használatával: Lépésről‑lépésre útmutató](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)