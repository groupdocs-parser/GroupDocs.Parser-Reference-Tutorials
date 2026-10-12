---
date: '2026-10-12'
description: Tanulja meg, hogyan nyerhet ki QR-kódot PDF-ből Java-ban a GroupDocs.Parser
  használatával, és exportálhatja a vonalkód adatokat XML-be a további feldolgozáshoz.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Tanulja meg, hogyan nyerhet ki QR-kódot PDF-ből Java-ban a GroupDocs.Parser
  használatával, és exportálhatja a vonalkód adatokat XML-be a további feldolgozáshoz.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Hogyan nyerjünk ki QR-kódot PDF-ből Java-ban a GroupDocs.Parser-rel
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: Hogyan nyerjünk ki QR-kódot PDF-ből Java-ban a GroupDocs.Parser-rel
type: docs
url: /hu/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Hogyan lehet QR-kódot kinyerni PDF-ből Java-val a GroupDocs.Parser segítségével

A modern üzleti munkafolyamatokban a **PDF-ből QR-kódok kinyerése** fájlok esetén a manuális adatbevitel szűk keresztmetszetét teljesen automatizált csővezetékké alakíthatja. Legyen szó szállítmánylistákról, kiskereskedelmi nyugtákról vagy termékkatalógusokról, a QR-információk gyors és megbízható kinyerése elengedhetetlen a downstream rendszerek számára. Ez az útmutató végigvezet a **GroupDocs.Parser for Java** használatán, amely QR-kódokat (és más vonalkódokat) olvas ki a PDF-ekből, és az eredményeket egy tiszta XML-fájlba exportálja, amelyet az ERP, a készletkezelő vagy az elemző platform felhasználhat.

## Gyors válaszok
- **Mit csinál a GroupDocs.Parser for Java?** PDF-fájlokat olvas be, és strukturált adatokat nyer ki, például vonalkódokat, táblázatokat és szöveget.  
- **Hogyan lehet QR-kódokat kinyerni?** `BarcodeOptions`-t állítsa be a QR típusra, és hívja meg a `parser.getBarcodes()`-t.  
- **Olvashatok QR-kódokat Java-ban?** Igen—állítsa be a vonalkód típusát `"QR"`-re a beállításokban.  
- **Szükségem van licencre?** A próba verzió teszteléshez működik; a termeléshez kereskedelmi licenc szükséges.  
- **Milyen Java verzió szükséges?** Java 8 vagy újabb ajánlott.

## Mi az a „QR-kód kinyerése PDF-ből” a PDF feldolgozás kontextusában?
A PDF-ből QR-kódok kinyerése azt jelenti, hogy minden oldalt átvizsgálunk QR‑kódolt grafikák után, dekódoljuk a beágyazott adatokat, és programbarát formátumban adjuk vissza őket. A GroupDocs.Parser elrejti az alacsony szintű képelemzést, így Ön az üzleti logikára koncentrálhat a pixelmanipuláció helyett.

## Miért használja a GroupDocs.Parser-t QR kinyeréshez?
A GroupDocs.Parser támogat **több mint 30 bemeneti formátumot**, és akár **500 MB**-os PDF-eket is feldolgozhat anélkül, hogy a teljes fájlt memóriába töltené, magas pontosságú eredményeket biztosítva még alacsony felbontású szkennel is. Választhatja a `QualityMode.Low` módot a sebességért vagy a `QualityMode.High` módot a maximális pontosságért, és ugyanaz az API működik PDF-ekkel, képekkel és Office dokumentumokkal, ezzel megszüntetve több könyvtár használatának szükségességét.

## Előkövetelmények
- **GroupDocs.Parser for Java** (verzió 25.5 vagy újabb).  
- Maven vagy manuális JAR letöltés.  
- Java 8+ fejlesztői környezet (IntelliJ IDEA, Eclipse vagy bármely szerkesztő).  

## A GroupDocs.Parser beállítása Java-hoz
### Maven használata
Add the GroupDocs repository and dependency to your `pom.xml`:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

### Közvetlen letöltés
Alternatively, download the latest JAR from [GroupDocs.Parser Java kiadások](https://releases.groupdocs.com/parser/java/).

#### Licenc megszerzésének lépései
- **Ingyenes próba:** 30 napos próba teljes funkciókészlettel.  
- **Ideiglenes licenc:** Kérjen ideiglenes kulcsot a kibővített értékeléshez.  
- **Vásárlás:** Szerezzen kereskedelmi licencet a termelési telepítésekhez.

### Alap inicializálás és beállítás
Create a `Parser` instance that points to the PDF you want to analyze:

`Parser` is the core class in GroupDocs.Parser that represents a document and provides methods for extracting content such as text, tables, and barcodes.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## QR-kódok olvasása Java PDF-ekben a GroupDocs.Parser segítségével
Reading QR codes in Java PDFs with GroupDocs.Parser involves creating a parser instance, configuring barcode options to target QR types, invoking the barcode extraction method, and then handling the returned barcode objects. The process is straightforward, works on any PDF page, and returns the decoded values along with positional metadata for further processing.

### 1. lépés: a vonalkód támogatás ellenőrzése
Before attempting extraction, confirm that the document format supports barcode scanning:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Explanation:* This guard prevents runtime errors on unsupported file types.

### 2. lépés: vonalkód opciók konfigurálása (QR-kódok olvasása Java-ban)
`BarcodeOptions` is a configuration object that lets you specify which barcode symbologies to detect, set the scanning quality mode, and fine‑tune parameters such as detection thresholds, ensuring optimal performance for the target QR codes.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Explanation:* `QualityMode.Low` speeds up processing; switch to `High` if you need extra accuracy. The `"QR"` argument tells the engine to look for QR‑type barcodes only.

### 3. lépés: a QR-adatok kinyerése
`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions` and returns a collection of `PageBarcodeArea` objects, each encapsulating the decoded QR value, the page number, and the exact coordinates of the barcode within the page, allowing precise downstream handling.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Explanation:* `parser.getBarcodes` returns an iterable collection of `PageBarcodeArea` objects, each containing the decoded QR value and its location on the page.

## Kinyert adatok exportálása XML-be
### 4. lépés: az XML exportáló inicializálása
`XmlExporter` is a utility class that transforms a collection of barcode objects into a well‑structured XML document, automatically generating elements for each barcode with attributes for page index, position, and decoded value, which can then be saved or streamed to other systems.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Explanation:* The `XmlExporter` handles serialization of barcode objects into standard XML, ready for integration with ERP or inventory systems.

### 5. lépés: az XML fájl írása
Save the extracted QR information to disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Explanation:* The resulting `data.xml` contains one `<Barcode>` element per QR code, with attributes for page number, coordinates, and decoded value.

## Gyakorlati alkalmazások
1. **Készletkezelés:** Automatikusan töltse fel a készletadatbázist a bejövő szállítmány PDF-ek QR-címkéinek olvasásával.  
2. **Ellátási lánc láthatósága:** Kövesse a csomagokat valós időben a logisztikai dokumentumokba ágyazott QR-azonosítók kinyerésével.  
3. **Kiskereskedelmi nyugták:** Húzza ki a promóciós vagy garanciális információkat a digitális nyugtákra nyomtatott QR-kódokból.

## Teljesítmény szempontok
- **Memóriakezelés:** Nagyon nagy PDF-ek esetén dolgozza fel az oldalakat streaming módon, a teljes fájl memóriába betöltése helyett.  
- **QualityMode kiválasztása:** Használja a `Low` módot tömeges feldolgozáshoz; váltson `High`-ra, ha alacsony felbontású szkennel dolgozik.  
- **Könyvtár frissítések:** Tartsa a GroupDocs.Parser-t naprakészen, hogy élvezze a legújabb teljesítményjavításokat és hibajavításokat.

## Gyakori problémák és hibaelhárítás
| Tünet | Valószínű ok | Megoldás |
|---------|--------------|-----|
| Nem tér vissza vonalkód | Helytelen vonalkód típus megadva | Módosítsa a `"QR"`-t a megfelelő típusra (pl. `"CODE_128"`). |
| Memóriahiány hiba nagy PDF-eknél | A teljes dokumentum egyszerre betöltve | Dolgozza fel az oldalakat egyenként vagy növelje a JVM heap méretét (`-Xmx2g`). |
| Üres XML fájl | `exportBarcodes` meghívva a kinyerés előtt | Győződjön meg róla, hogy a `parser.getBarcodes(options)` adatot ad vissza a exportálás előtt. |

## Gyakran feltett kérdések
**Q: Kinyerhetek vonalkódokat képfájlokból a GroupDocs.Parser segítségével?**  
A: Igen, a könyvtár támogatja a vonalkód kinyerését a gyakori képformátumokból (PNG, JPEG, TIFF).

**Q: Milyen vonalkód formátumokat ismer fel?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 és még sok más. Tekintse meg az API dokumentációt a teljes listáért.

**Q: Hogyan kezeljem a jelszóval védett PDF-eket?**  
A: Adja át a jelszót a `Parser` konstruktorának: `new Parser(filePath, "password")`.

**Q: Elégséges-e a próba verzió a termelési teszteléshez?**  
A: A próba teljes funkcionalitást biztosít, de vízjelet ad a kinyert adatokhoz. Termeléshez szerezzen kereskedelmi licencet.

**Q: Mi van, ha a PDF-em QR és lineáris vonalkódokat is tartalmaz?**  
A: Hozzon létre több `BarcodeOptions` példányt, vagy adjon át egy típusok tömbjét, hogy egy futásban minden szükséges formátumot beolvasson.

---

**Legutóbb frissítve:** 2026-10-12  
**Tesztelve a következővel:** GroupDocs.Parser 25.5  
**Szerző:** GroupDocs  

## Erőforrások
- [GroupDocs.Parser Java dokumentáció](https://docs.groupdocs.com/parser/java/)
- [API referencia](https://reference.groupdocs.com/parser/java)
- [GroupDocs.Parser letöltése](https://releases.groupdocs.com/parser/java/)
- [GitHub tároló](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Ingyenes támogatási fórum](https://forum.groupdocs.com/c/parser)
- [Ideiglenes licenc igénylés](https://purchase.groupdocs.com/temporary-license/)

## Kapcsolódó oktatóanyagok

- [Vonalkód kinyerése PDF-ből GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Hogyan töltsünk be PDF-et URL-ből a GroupDocs.Parser for Java segítségével](/parser/java/document-loading/)
- [PDF űrlapadatok kinyerése a GroupDocs.Parser Java-val](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)