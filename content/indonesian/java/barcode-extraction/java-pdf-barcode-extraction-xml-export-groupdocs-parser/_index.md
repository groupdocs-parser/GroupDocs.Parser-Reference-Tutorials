---
date: '2026-10-12'
description: Pelajari cara mengekstrak QR dari PDF di Java menggunakan GroupDocs.Parser
  dan mengekspor data kode batang ke XML untuk pemrosesan lanjutan.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Pelajari cara mengekstrak QR dari PDF di Java menggunakan GroupDocs.Parser
  dan mengekspor data kode batang ke XML untuk pemrosesan lanjutan.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Cara mengekstrak QR dari PDF di Java dengan GroupDocs.Parser
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
title: Cara mengekstrak QR dari PDF di Java dengan GroupDocs.Parser
type: docs
url: /id/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Cara mengekstrak QR dari PDF di Java dengan GroupDocs.Parser

Dalam alur kerja bisnis modern, **mengekstrak QR dari PDF** dapat mengubah bottleneck entri data manual menjadi alur otomatis sepenuhnya. Apakah Anda menangani manifest pengiriman, struk ritel, atau katalog produk, mengambil informasi QR dengan cepat dan andal sangat penting bagi sistem hilir. Tutorial ini memandu Anda menggunakan **GroupDocs.Parser for Java** untuk membaca kode QR (dan barcode lainnya) dari PDF serta mengekspor hasilnya ke file XML bersih yang dapat dikonsumsi oleh ERP, inventaris, atau platform analitik Anda.

## Jawaban Cepat
- **Apa yang dilakukan GroupDocs.Parser for Java?** It reads PDF files and extracts structured data such as barcodes, tables, and text.  
- **Bagaimana cara mengekstrak kode QR?** Configure `BarcodeOptions` with the QR type and call `parser.getBarcodes()`.  
- **Apakah saya dapat membaca kode QR di Java?** Yes—set the barcode type to `"QR"` in the options.  
- **Apakah saya memerlukan lisensi?** A trial works for testing; a commercial license is required for production.  
- **Versi Java apa yang diperlukan?** Java 8 atau lebih tinggi disarankan.

## Apa itu “mengekstrak QR dari PDF” dalam konteks pemrosesan PDF?
Mengekstrak QR dari PDF berarti memindai setiap halaman untuk grafik yang dikodekan QR, mendekode data yang tertanam, dan mengembalikannya dalam format yang ramah program. GroupDocs.Parser mengabstraksi analisis gambar tingkat rendah sehingga Anda dapat fokus pada logika bisnis daripada manipulasi piksel.

## Mengapa menggunakan GroupDocs.Parser untuk ekstraksi QR?
GroupDocs.Parser mendukung **lebih dari 30 format input** dan dapat memproses PDF hingga **500 MB** tanpa memuat seluruh file ke memori, memberikan hasil akurasi tinggi bahkan pada pemindaian beresolusi rendah. Anda dapat memilih `QualityMode.Low` untuk kecepatan atau `QualityMode.High` untuk presisi maksimum, dan API yang sama bekerja untuk PDF, gambar, dan dokumen Office, menghilangkan kebutuhan akan banyak pustaka.

## Prasyarat
- **GroupDocs.Parser for Java** (versi 25.5 atau lebih baru).  
- Maven atau unduhan JAR manual.  
- Lingkungan pengembangan Java 8+ (IntelliJ IDEA, Eclipse, atau editor apa pun).  

## Menyiapkan GroupDocs.Parser untuk Java
### Menggunakan Maven
Tambahkan repositori GroupDocs dan dependensi ke `pom.xml` Anda:

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

### Unduhan langsung
Sebagai alternatif, unduh JAR terbaru dari [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Langkah-langkah memperoleh lisensi
- **Uji coba gratis:** uji coba 30 hari dengan semua fitur lengkap.  
- **Lisensi sementara:** Minta kunci sementara untuk evaluasi yang diperpanjang.  
- **Pembelian:** Dapatkan lisensi komersial untuk penerapan produksi.

### Inisialisasi dan pengaturan dasar
Buat instance `Parser` yang menunjuk ke PDF yang ingin Anda analisis:

`Parser` adalah kelas inti dalam GroupDocs.Parser yang mewakili dokumen dan menyediakan metode untuk mengekstrak konten seperti teks, tabel, dan barcode.  

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
Membaca kode QR dalam PDF Java dengan GroupDocs.Parser melibatkan pembuatan instance parser, mengonfigurasi opsi barcode untuk menargetkan tipe QR, memanggil metode ekstraksi barcode, dan kemudian menangani objek barcode yang dikembalikan. Proses ini sederhana, bekerja pada halaman PDF apa pun, dan mengembalikan nilai yang didekode beserta metadata posisi untuk pemrosesan lebih lanjut.

### Langkah 1: verifikasi dukungan barcode
Sebelum mencoba ekstraksi, pastikan format dokumen mendukung pemindaian barcode:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Penjelasan:* Guard ini mencegah error runtime pada tipe file yang tidak didukung.

### Langkah 2: konfigurasikan opsi barcode (baca kode QR Java)
`BarcodeOptions` adalah objek konfigurasi yang memungkinkan Anda menentukan simbologi barcode mana yang akan dideteksi, mengatur mode kualitas pemindaian, dan menyesuaikan parameter seperti ambang deteksi, memastikan kinerja optimal untuk kode QR target.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Penjelasan:* `QualityMode.Low` mempercepat pemrosesan; beralih ke `High` jika Anda memerlukan akurasi ekstra. Argumen `"QR"` memberi tahu mesin untuk mencari barcode tipe QR saja.

### Langkah 3: ekstrak data QR
`parser.getBarcodes(options)` memindai dokumen menggunakan `BarcodeOptions` yang diberikan dan mengembalikan koleksi objek `PageBarcodeArea`, masing‑masing berisi nilai QR yang didekode, nomor halaman, dan koordinat tepat barcode dalam halaman, memungkinkan penanganan hilir yang presisi.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Penjelasan:* `parser.getBarcodes` mengembalikan koleksi yang dapat diiterasi dari objek `PageBarcodeArea`, masing‑masing berisi nilai QR yang didekode dan lokasinya pada halaman.

## Mengekspor data yang diekstrak ke XML
### Langkah 4: inisialisasi exporter XML
`XmlExporter` adalah kelas utilitas yang mengubah koleksi objek barcode menjadi dokumen XML terstruktur dengan baik, secara otomatis menghasilkan elemen untuk setiap barcode dengan atribut indeks halaman, posisi, dan nilai terdekripsi, yang kemudian dapat disimpan atau dialirkan ke sistem lain.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Penjelasan:* `XmlExporter` menangani serialisasi objek barcode ke XML standar, siap untuk integrasi dengan sistem ERP atau inventaris.

### Langkah 5: tulis file XML
Simpan informasi QR yang diekstrak ke disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Penjelasan:* `data.xml` yang dihasilkan berisi satu elemen `<Barcode>` per kode QR, dengan atribut nomor halaman, koordinat, dan nilai terdekripsi.

## Aplikasi praktis
1. **Manajemen inventaris:** Mengisi otomatis basis data stok dengan membaca tag QR pada PDF pengiriman yang masuk.  
2. **Visibilitas rantai pasokan:** Melacak paket secara real time dengan mengekstrak identifier QR yang tertanam dalam dokumen logistik.  
3. **Struk ritel:** Mengambil informasi promosi atau garansi dari kode QR yang dicetak pada struk digital.

## Pertimbangan kinerja
- **Manajemen memori:** Untuk PDF yang sangat besar, proses halaman secara streaming alih-alih memuat seluruh file ke memori.  
- **Pemilihan QualityMode:** Gunakan `Low` untuk pemrosesan massal; beralih ke `High` ketika menangani pemindaian beresolusi rendah.  
- **Pembaruan pustaka:** Jaga GroupDocs.Parser tetap terbaru untuk mendapatkan peningkatan kinerja dan perbaikan bug terkini.

## Masalah umum & pemecahan masalah
| Gejala | Penyebab kemungkinan | Perbaikan |
|---------|--------------|-----|
| Tidak ada barcode yang dikembalikan | Tipe barcode yang salah ditentukan | Ubah `"QR"` ke tipe yang sesuai (mis., `"CODE_128"`). |
| Error out‑of‑memory pada PDF besar | Seluruh dokumen dimuat sekaligus | Proses halaman secara individual atau tingkatkan ukuran heap JVM (`-Xmx2g`). |
| File XML kosong | `exportBarcodes` dipanggil sebelum ekstraksi | Pastikan `parser.getBarcodes(options)` mengembalikan data sebelum mengekspor. |

## Pertanyaan yang sering diajukan
**Q: Bisakah saya mengekstrak barcode dari file gambar menggunakan GroupDocs.Parser?**  
A: Ya, pustaka mendukung ekstraksi barcode dari format gambar umum (PNG, JPEG, TIFF).

**Q: Format barcode apa yang dikenali?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417, dan banyak lagi. Lihat dokumentasi API untuk daftar lengkap.

**Q: Bagaimana saya menangani PDF yang dilindungi kata sandi?**  
A: Berikan kata sandi ke konstruktor `Parser`: `new Parser(filePath, "password")`.

**Q: Apakah versi percobaan cukup untuk pengujian produksi?**  
A: Versi percobaan menyediakan semua fungsi tetapi menambahkan watermark pada data yang diekstrak. Untuk produksi, dapatkan lisensi komersial.

**Q: Bagaimana jika PDF saya berisi QR dan barcode linier?**  
A: Buat beberapa instance `BarcodeOptions` atau berikan array tipe untuk memindai semua format yang dibutuhkan dalam satu kali proses.

---

**Terakhir diperbarui:** 2026-10-12  
**Diuji dengan:** GroupDocs.Parser 25.5  
**Penulis:** GroupDocs  

## Sumber daya
- [Dokumentasi GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Referensi API](https://reference.groupdocs.com/parser/java)
- [Unduh GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Repositori GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Forum dukungan gratis](https://forum.groupdocs.com/c/parser)
- [Aplikasi lisensi sementara](https://purchase.groupdocs.com/temporary-license/)

## Tutorial Terkait

- [Ekstrak Barcode PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Cara Memuat PDF dari URL dengan GroupDocs.Parser untuk Java](/parser/java/document-loading/)
- [Ekstrak Data Form PDF dengan GroupDocs.Parser di Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)