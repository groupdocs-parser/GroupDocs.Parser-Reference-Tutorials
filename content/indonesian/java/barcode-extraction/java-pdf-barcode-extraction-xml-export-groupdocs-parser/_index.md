---
date: '2026-02-19'
description: Pelajari cara membaca kode QR dalam PDF Java menggunakan GroupDocs.Parser
  dan mengekspor data barcode ke XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Cara Membaca Kode QR pada PDF Java dengan GroupDocs.Parser
type: docs
url: /id/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Cara Membaca Kode QR dalam PDF Java dengan GroupDocs.Parser

Dalam alur kerja bisnis modern, **cara membaca QR** kode dari dokumen PDF dapat membuat perbedaan antara kemacetan entri data manual dan jalur otomatis sepenuhnya. Baik Anda menangani manifest pengiriman, struk ritel, atau katalog produk, mengekstrak informasi QR dengan cepat dan dapat diandalkan sangat penting. Tutorial ini memandu Anda menggunakan **GroupDocs.Parser for Java** untuk membaca kode QR (dan barcode lainnya) dari PDF dan mengekspor hasilnya ke file XML bersih yang dapat dikonsumsi oleh sistem hilir.

## Jawaban Cepat
- **What does GroupDocs.Parser for Java do?** It reads PDF files and extracts structured data such as barcodes.  
- **How to extract QR codes?** By configuring `BarcodeOptions` with the QR type and calling `parser.getBarcodes()`.  
- **Can I read QR codes Java?** Yes—set the barcode type to `"QR"` in the options.  
- **Do I need a license?** A trial works for testing; a commercial license is required for production.  
- **What Java version is required?** Java 8 or higher is recommended.

## Apa itu “cara membaca QR” dalam konteks pemrosesan PDF?
Membaca kode QR dari PDF berarti memindai setiap halaman untuk grafik yang dienkode QR, mendekode data yang tertanam, dan mengembalikannya dalam format yang ramah program. GroupDocs.Parser mengabstraksi analisis gambar tingkat rendah sehingga Anda dapat fokus pada logika bisnis daripada manipulasi piksel.

## Mengapa menggunakan GroupDocs.Parser untuk ekstraksi QR?
- **High accuracy:** Built‑in image‑processing algorithms handle low‑resolution scans.  
- **Performance options:** Choose `QualityMode.Low` for speed or `QualityMode.High` for maximum precision.  
- **Cross‑format support:** Works with PDFs, images, and even Office documents, so you can reuse the same code base for different file types.

## Prasyarat
- **GroupDocs.Parser for Java** (version 25.5 or later).  
- Maven or manual JAR download.  
- Java 8+ development environment (IntelliJ IDEA, Eclipse, or any editor).  

## Menyiapkan GroupDocs.Parser untuk Java
### Menggunakan Maven
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

### Unduh Langsung
Sebagai alternatif, unduh JAR terbaru dari [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Langkah-langkah Akuisisi Lisensi
- **Free Trial:** 30‑day trial with full feature set.  
- **Temporary License:** Request a temporary key for extended evaluation.  
- **Purchase:** Obtain a commercial license for production deployments.

### Inisialisasi dan Penyiapan Dasar
Create a `Parser` instance that points to the PDF you want to analyze:

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

## Cara membaca kode QR dalam PDF Java menggunakan GroupDocs.Parser
### Langkah 1: Verifikasi Dukungan Barcode
Before attempting extraction, confirm that the document format supports barcode scanning:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Explanation:* This guard prevents runtime errors on unsupported file types.

### Langkah 2: Konfigurasi Opsi Barcode (Baca Kode QR Java)
Set the scanning quality and specify that you’re interested in QR codes:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Explanation:* `QualityMode.Low` speeds up processing; switch to `High` if you need extra accuracy. The `"QR"` argument tells the engine to look for QR‑type barcodes only.

### Langkah 3: Ekstrak Data QR
Pull the barcode information from every page of the PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Explanation:* `parser.getBarcodes` returns an iterable collection of `PageBarcodeArea` objects, each containing the decoded QR value and its location on the page.

## Mengekspor Data yang Diekstrak ke XML
### Langkah 4: Inisialisasi Ekspor XML
Create an exporter that will transform the barcode collection into a well‑structured XML file:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Explanation:* The `XmlExporter` handles serialization of barcode objects into standard XML, ready for integration with ERP or inventory systems.

### Langkah 5: Tulis File XML
Save the extracted QR information to disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Explanation:* The resulting `data.xml` contains one `<Barcode>` element per QR code, with attributes for page number, coordinates, and decoded value.

## Aplikasi Praktis
1. **Inventory Management:** Auto‑populate stock databases by reading QR tags on incoming shipment PDFs.  
2. **Supply‑Chain Visibility:** Track packages in real time by extracting QR identifiers embedded in logistics documents.  
3. **Retail Receipts:** Pull promotional or warranty information from QR codes printed on digital receipts.

## Pertimbangan Kinerja
- **Memory Management:** For very large PDFs, process pages in a streaming fashion instead of loading the whole file into memory.  
- **QualityMode Selection:** Use `Low` for bulk processing; switch to `High` when dealing with low‑resolution scans.  
- **Library Updates:** Keep GroupDocs.Parser up‑to‑date to benefit from the latest performance improvements and bug fixes.

## Masalah Umum & Pemecahan Masalah
| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No barcodes returned | Wrong barcode type specified | Change `"QR"` to the appropriate type (e.g., `"CODE_128"`). |
| Out‑of‑memory error on large PDFs | Whole document loaded at once | Process pages individually or increase JVM heap size (`-Xmx2g`). |
| Empty XML file | `exportBarcodes` called before extraction | Ensure `parser.getBarcodes(options)` returns data before exporting. |

## Pertanyaan yang Sering Diajukan
**Q: Can I extract barcodes from image files using GroupDocs.Parser?**  
A: Yes, the library supports barcode extraction from common image formats (PNG, JPEG, TIFF).

**Q: What barcode formats are recognized?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the API docs for the full list.

**Q: How should I handle password‑protected PDFs?**  
A: Pass the password to the `Parser` constructor: `new Parser(filePath, "password")`.

**Q: Is the trial version sufficient for production testing?**  
A: The trial provides full functionality but adds a watermark to extracted data. For production, acquire a commercial license.

**Q: What if my PDF contains both QR and linear barcodes?**  
A: Create multiple `BarcodeOptions` instances or pass an array of types to scan for all needed formats in one pass.

---

**Last Updated:** 2026-02-19  
**Tested With:** GroupDocs.Parser 25.5  
**Author:** GroupDocs  

## Sumber Daya
- [GroupDocs.Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- [API Reference](https://reference.groupdocs.com/parser/java)
- [Download GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub Repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/parser)
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)