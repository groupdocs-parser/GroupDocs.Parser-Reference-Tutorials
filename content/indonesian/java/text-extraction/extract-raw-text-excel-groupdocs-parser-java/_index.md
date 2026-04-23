---
date: '2026-02-14'
description: Pelajari cara mengurai file Excel dengan GroupDocs.Parser untuk Java,
  meliputi pengaturan, ekstraksi teks mentah, dan tips kinerja.
keywords:
- extract raw text from excel with java
- groupdocs parser for java setup
- implementing text extraction in excel with java
title: Cara Mengurai Excel Menggunakan GroupDocs.Parser untuk Java – Panduan
type: docs
url: /id/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/
weight: 1
---

# Cara Mengurai Excel Menggunakan GroupDocs.Parser untuk Java – Panduan

Dalam aplikasi yang berfokus pada data saat ini, **cara mengurai file Excel** secara efisien dapat menentukan keberhasilan alur kerja. Baik Anda memigrasi data warisan, menghasilkan laporan otomatis, atau memasukkan teks mentah ke dalam pipeline analitik, mengekstrak teks tidak berformat dari setiap lembar kerja adalah kebutuhan umum. Tutorial ini memandu Anda menggunakan **GroupDocs.Parser untuk Java** untuk mengurai file Excel, membaca teks lembar Excel, dan mengambil konten mentah dengan kode minimal.

## Jawaban Cepat
- **Perpustakaan apa yang menangani penguraian Excel di Java?** GroupDocs.Parser untuk Java.  
- **Bisakah saya mengekstrak teks mentah dari setiap lembar?** Ya, dengan menggunakan `TextReader` dengan mode mentah diaktifkan.  
- **Apakah saya memerlukan lisensi?** Lisensi gratis sementara tersedia untuk evaluasi.  
- **Versi Java mana yang diperlukan?** JDK 8 atau lebih tinggi.  
- **Apakah Maven didukung?** Tentu – tambahkan repositori dan dependensi ke `pom.xml`.

## Apa itu “cara mengurai Excel” dengan GroupDocs.Parser?
Mengurai Excel dengan GroupDocs.Parser berarti membuka workbook `.xlsx` (atau format lain yang didukung) secara programatik, mengiterasi lembar-lemarnya, dan membaca teks polos tanpa format apa pun. Pendekatan ini lebih cepat daripada memuat seluruh workbook ke dalam API spreadsheet yang berat dan memberi Anda akses langsung ke karakter dasar.

## Mengapa Menggunakan GroupDocs.Parser untuk Java?
- **Kecepatan & jejak memori rendah:** Memproses satu lembar pada satu waktu.  
- **Dukungan format luas:** Menangani XLSX, XLS, CSV, dan lainnya.  
- **API sederhana:** Hanya beberapa baris kode untuk mulai mengekstrak teks.  
- **Lisensi siap perusahaan:** Uji coba gratis, kemudian opsi komersial yang dapat diskalakan.

## Prasyarat
- **Java Development Kit (JDK):** 8 atau lebih baru.  
- **IDE:** IntelliJ IDEA, Eclipse, atau editor kompatibel Java lainnya.  
- **Maven (opsional):** Untuk memudahkan manajemen dependensi.  

## Menyiapkan GroupDocs.Parser untuk Java

### Pengaturan Maven
Jika Anda mengelola dependensi dengan Maven, tambahkan repositori dan dependensi ke `pom.xml` Anda:

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

### Unduhan Langsung
Sebagai alternatif, unduh versi terbaru GroupDocs.Parser untuk Java langsung dari [GroupDocs releases](https://releases.groupdocs.com/parser/java/).

### Perolehan Lisensi
Untuk memulai dengan uji coba gratis, kunjungi [situs GroupDocs](https://purchase.groupdocs.com/temporary-license/) untuk memperoleh lisensi sementara. Ini memungkinkan Anda mengevaluasi semua kemampuan perpustakaan sebelum membeli lisensi produksi.

### Inisialisasi dan Pengaturan Dasar
Setelah perpustakaan berada di classpath Anda, Anda dapat membuat instance `Parser` yang menunjuk ke workbook Excel Anda:

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.TextReader;
import com.groupdocs.parser.options.IDocumentInfo;
import com.groupdocs.parser.options.TextOptions;

String excelFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";

try (Parser parser = new Parser(excelFilePath)) {
    // Your code to work with the document
} catch (Exception e) {
    e.printStackTrace();
}
```

Dengan lingkungan siap, mari kita selami logika ekstraksi sebenarnya.

## Cara Mengurai Excel: Mengekstrak Teks Mentah dari Lembar

### Langkah 1 – Mengambil Informasi Dokumen
Pertama, dapatkan metadata tentang workbook, seperti jumlah lembar kerja (halaman mentah).

```java
IDocumentInfo spreadsheetInfo = parser.getDocumentInfo();
```

### Langkah 2 – Loop Melalui Setiap Lembar dan Membaca Teks
Iterasi setiap lembar dan ambil teks mentah yang tidak berformat. Flag `TextOptions(true)` mengaktifkan mode mentah.

```java
for (int p = 0; p < spreadsheetInfo.getRawPageCount(); p++) {
    try (TextReader reader = parser.getText(p, new TextOptions(true))) {
        String sheetContent = reader.readToEnd();
        
        // Process or use extracted text data here
    }
}
```

#### Memproses Data yang Diekstrak
Pada titik ini `sheetContent` berisi teks polos dari lembar kerja saat ini. Anda dapat:

- Menuliskannya ke file `.txt` untuk arsip.  
- Memasukkannya ke pipeline pemrosesan bahasa alami.  
- Menyimpannya di basis data untuk kueri di kemudian hari.

## Masalah Umum dan Solusinya
| Masalah | Mengapa Terjadi | Solusi |
|---------|----------------|--------|
| **File tidak ditemukan** | `excelFilePath` salah. | Verifikasi jalur dan pastikan file dapat dibaca. |
| **Format tidak didukung** | Menggunakan file XLS lama dengan versi parser yang lebih baru. | Konversi file ke XLSX atau perbarui ke versi GroupDocs.Parser terbaru. |
| **Kesalahan out‑of‑memory pada workbook besar** | Memuat semua lembar sekaligus. | Proses satu lembar pada satu waktu (seperti yang ditunjukkan) dan lepaskan sumber daya segera. |
| **Pengecualian lisensi** | Uji coba kedaluwarsa atau file lisensi hilang. | Terapkan lisensi sementara atau berbayar yang valid sebelum mengurai. |

## Aplikasi Praktis (Membaca Teks Lembar Excel)
1. **Migrasi Data:** Pindahkan data spreadsheet warisan ke basis data modern tanpa menyalin‑tempel manual.  
2. **Pelaporan Otomatis:** Ambil nilai mentah dari banyak workbook untuk menghasilkan laporan PDF atau HTML terintegrasi.  
3. **Pengindeksan Pencarian:** Indeks teks yang diekstrak di Elasticsearch untuk penemuan konten yang cepat.  

## Tips Kinerja untuk File Excel Besar
- **Streaming per lembar:** Loop sudah memproses satu lembar pada satu waktu, menjaga penggunaan memori tetap rendah.  
- **Gunakan kembali objek `TextReader`:** Hindari membuat objek tidak perlu di dalam loop yang ketat.  
- **Pemrosesan paralel:** Untuk workbook yang sangat besar, pertimbangkan memproses lembar di thread terpisah, tetapi perhatikan keamanan thread pada instance `Parser`.  

## Pertanyaan yang Sering Diajukan

**T: Format spreadsheet lain apa yang didukung oleh GroupDocs.Parser?**  
J: Ia menangani XLSX, XLS, CSV, dan format Office Open XML lainnya.

**T: Bisakah saya mengekstrak informasi format sel juga?**  
J: Ya, dengan menggunakan `TextOptions` tanpa flag mentah, Anda dapat mengambil teks berformat.

**T: Bagaimana cara menangani file Excel yang dilindungi kata sandi?**  
J: Berikan kata sandi ke konstruktor `Parser`: `new Parser(filePath, "password")`.

**T: Apakah ada cara mengekstrak hanya kolom tertentu?**  
J: Anda dapat memproses `sheetContent` untuk menyaring baris atau menggunakan API `SpreadsheetOptions` untuk kontrol yang lebih granular.

**T: Di mana saya dapat menemukan contoh kode lebih lanjut?**  
J: Lihat [dokumentasi GroupDocs](https://docs.groupdocs.com/parser/java/) dan repositori GitHub untuk contoh tambahan.

## Sumber Daya
- Dokumentasi: [GroupDocs Parser Java Docs](https://docs.groupdocs.com/parser/java/)
- Referensi API: [API Reference](https://reference.groupdocs.com/parser/java)
- Unduhan: [Latest Releases](https://releases.groupdocs.com/parser/java/)
- Repositori GitHub: [GroupDocs.Parser on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- Forum Dukungan Gratis: [GroupDocs Parser Forum](https://forum.groupdocs.com/c/parser)
- Lisensi Sementara: [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/) 

---

**Terakhir Diperbarui:** 2026-02-14  
**Diuji Dengan:** GroupDocs.Parser 25.5 untuk Java  
**Penulis:** GroupDocs