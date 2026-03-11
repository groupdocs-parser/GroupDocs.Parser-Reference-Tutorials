---
date: '2026-02-09'
description: Pelajari cara menggunakan OCR untuk mengekstrak teks dari gambar dan
  dokumen dalam Java dengan GroupDocs.Parser. Panduan ini mencakup pengaturan, konversi
  gambar ke teks di Java, dan contoh penggunaan praktis untuk pemrosesan dokumen yang
  efisien.
keywords:
- OCR Text Extraction
- GroupDocs.Parser Java
- Java OCR Integration
title: 'Cara Menggunakan OCR dengan GroupDocs.Parser Java: Mengekstrak Teks dari Gambar
  dan Dokumen'
type: docs
url: /id/java/ocr-integration/ocr-text-extraction-groupdocs-parser-java/
weight: 1
---

 final content.

# Cara Menggunakan OCR dengan GroupDocs.Parser Java

Apakah Anda ingin mengekstrak teks secara efisien dari gambar atau dokumen yang dipindai? **Cara menggunakan OCR** dengan pustaka GroupDocs.Parser untuk Java menawarkan solusi yang kuat, memungkinkan integrasi mulus Optical Character Recognition (OCR) ke dalam aplikasi Anda. Panduan komprehensif ini akan memandu Anda mengekstrak area teks dari file gambar menggunakan konektor Aspose OCR dengan GroupDocs.Parser di Java, meningkatkan kemampuan pemrosesan dokumen Anda.

**Apa yang Akan Anda Pelajari**
- Menyiapkan dan menggunakan GroupDocs.Parser untuk Java.
- Menginisialisasi `ParserSettings` dengan konektor OCR.
- Teknik untuk mengekstrak area teks dari gambar menggunakan teknologi Aspose OCR.
- Aplikasi praktis fitur ini dalam skenario dunia nyata seperti konversi **java image to text** dan mengekstrak posisi teks di Java.

## Jawaban Cepat
- **Apa arti “how to use OCR”?** Ini merujuk pada mengintegrasikan mesin OCR untuk membaca teks dari file berbasis gambar.  
- **Library mana yang menyediakan OCR untuk Java?** GroupDocs.Parser yang digabungkan dengan konektor Aspose OCR.  
- **Apakah saya memerlukan lisensi?** Tersedia percobaan gratis; lisensi permanen diperlukan untuk produksi.  
- **Bisakah saya mendapatkan koordinat teks?** Ya, API mengembalikan posisi area teks (left, top, width, height).  
- **Versi Java apa yang diperlukan?** Java 8 atau yang lebih baru disarankan.

## Apa itu Ekstraksi Teks OCR?
Optical Character Recognition (OCR) mengubah teks visual—yang ditemukan dalam gambar yang dipindai, PDF, atau foto—menjadi karakter yang dapat dibaca mesin. Ketika Anda **cara menggunakan OCR** di Java, Anda memungkinkan aplikasi Anda untuk mencari, mengedit, dan menganalisis dokumen yang sebelumnya statis.

## Mengapa Menggunakan GroupDocs.Parser untuk OCR?
- **Unified API** – Menangani PDF, gambar, dan banyak format lain dengan satu basis kode.  
- **Accurate Recognition** – Ditenagai oleh Aspose OCR, yang mendukung banyak bahasa dan font.  
- **Position Data** – Mengambil koordinat tepat setiap blok teks, sempurna untuk pemrosesan yang memperhatikan tata letak.  
- **Scalable** – Bekerja dengan gambar kecil atau pekerjaan batch besar, dan dapat dijalankan di‑premise atau di cloud.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

### Perpustakaan dan Dependensi yang Diperlukan
- **GroupDocs.Parser for Java**: Versi 25.5 atau lebih baru.  
- **Maven** atau pengaturan unduhan langsung untuk instalasi pustaka.  
- **Aspose OCR Connector**: Akses ke teknologi OCR Aspose diperlukan.

### Persyaratan Penyiapan Lingkungan
- IDE yang kompatibel (IntelliJ IDEA, Eclipse, dll.) yang berjalan pada Java 8+.  
- Maven terpasang jika Anda lebih suka pendekatan repositori Maven.

### Prasyarat Pengetahuan
- Keterampilan pemrograman Java dasar.  
- Keterbiasaan dalam menangani dependensi proyek.

## Menyiapkan GroupDocs.Parser untuk Java

Anda dapat menambahkan pustaka melalui Maven atau mengunduhnya secara langsung.

### Menggunakan Maven
Add the following configurations to your `pom.xml` file:

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
Sebagai alternatif, unduh versi terbaru dari [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Langkah-langkah Akuisisi Lisensi
- **Free Trial** – Evaluasi pustaka tanpa biaya.  
- **Temporary License** – Gunakan kunci berjangka waktu untuk pengujian lanjutan.  
- **Purchase** – Dapatkan lisensi penuh untuk penerapan produksi.

### Inisialisasi dan Penyiapan Dasar

Setelah pustaka tersedia, Anda dapat menginisialisasi parser. Di bawah ini adalah kode Java penting yang membuat instance `ParserSettings` dengan konektor Aspose OCR:

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.ParserSettings;
import com.groupdocs.parser.ocr.AsposeOcrOnPremise;

ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

Dengan dasar-dasar selesai, mari kita selami ekstraksi area teks OCR.

## Cara Mengekstrak Area Teks dengan OCR (Langkah‑per‑Langkah)

### 1. Inisialisasi `ParserSettings` dengan Konektor OCR
Konektor OCR memungkinkan pengenalan teks dalam dokumen yang hanya berupa gambar.

```java
// Initialize ParserSettings with OCR Connector
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

### 2. Buka Dokumen dan Konfigurasikan Opsi Ekstraksi
Kami menggunakan `PageTextAreaOptions` untuk memberi tahu parser agar mengembalikan data posisi untuk setiap kata yang dikenali.

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
    // Configure PageTextAreaOptions for OCR processing
    PageTextAreaOptions options = new PageTextAreaOptions(true);
    
    // Extract text areas from the document
    java.lang.Iterable<PageTextArea> areas = parser.getTextAreas(options);

    if (areas == null) {
        return; // Exit if text areas extraction is not supported
    }
    
    for (PageTextArea a : areas) {
        String text = a.getText();
        int leftPosition = a.getRectangle().getLeft();
        int topPosition = a.getRectangle().getTop();
        int width = a.getRectangle().getSize().getWidth();
        int height = a.getRectangle().getSize().getHeight();

        // Process the extracted data as needed
    }
} catch (java.lang.Exception ex) {
    // Handle any exceptions that occur during processing
}
```

#### Apa yang Dilakukan Kode Ini
- **Creates** sebuah instance `Parser` yang menunjuk ke folder dokumen Anda.  
- **Enables** OCR melalui `PageTextAreaOptions(true)`.  
- **Iterates** setiap `PageTextArea`, memberi Anda teks yang dikenali **dan** persegi tepatnya (posisi dan ukuran).  
- **Allows** Anda menyimpan atau memanipulasi data, seperti memasukkannya ke dalam basis data atau menampilkannya di UI.

### 3. Proses Hasil
Sekarang Anda dapat menggunakan teks dan koordinat yang diekstrak untuk berbagai skenario:

- **Document Digitization** – Mengonversi kontrak yang dipindai menjadi PDF yang dapat dicari.  
- **Data Entry Automation** – Mengambil bidang seperti nomor faktur langsung dari gambar tanda terima.  
- **Content Management** – Mengindeks posisi teks untuk penyorotan pencarian lanjutan.

## Masalah Umum dan Solusinya

| Gejala | Penyebab Kemungkinan | Solusi |
|---------|--------------|-----|
| Tidak ada area teks yang dikembalikan | Konektor OCR tidak dikonfigurasi atau jalur gambar tidak benar | Verifikasi bahwa instance `AsposeOcrOnPremise` telah dilisensikan dengan benar dan jalur file dapat diakses. |
| Karakter rusak | Kualitas gambar rendah atau bahasa tidak didukung | Gunakan pemindaian resolusi lebih tinggi dan konfigurasikan paket bahasa OCR. |
| Kesalahan out‑of‑memory pada PDF besar | Memproses banyak halaman resolusi tinggi sekaligus | Proses halaman dalam batch atau aktifkan mode streaming (`ParserSettings.setEnableStreaming(true)`). |

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara menginstal GroupDocs.Parser untuk Java?**  
A: Tambahkan sebagai dependensi Maven (lihat potongan XML di atas) atau unduh secara langsung dari halaman rilis resmi.

**Q: Apa itu Aspose OCR, dan mengapa menggunakannya dengan GroupDocs.Parser?**  
A: Aspose OCR adalah mesin pengenalan teks berakurasi tinggi. Dipasangkan dengan GroupDocs.Parser, ia memperluas kemampuan parser untuk menangani file yang hanya berupa gambar dan memberikan posisi teks yang tepat.

**Q: Bisakah saya memproses banyak format gambar?**  
A: Ya. GroupDocs.Parser mendukung JPEG, PNG, BMP, TIFF, dan lainnya—pastikan konektor OCR dapat membaca format tersebut.

**Q: Apa yang harus saya lakukan jika tidak ada area teks yang diekstrak?**  
A: Periksa jalur file, pastikan konektor OCR berlisensi, dan verifikasi bahwa tipe dokumen didukung oleh Aspose OCR.

**Q: Di mana saya dapat menemukan lebih banyak sumber daya tentang GroupDocs.Parser?**  
A: Kunjungi [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/) untuk panduan detail dan referensi API.

## Sumber Daya
- [Dokumentasi](https://docs.groupdocs.com/parser/java/)
- [Referensi API](https://reference.groupdocs.com/parser/java)
- [Unduh Versi Terbaru](https://releases.groupdocs.com/parser/java/)
- [Repositori GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/parser)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

Jelajahi sumber daya ini untuk memperdalam pemahaman Anda dan memperluas kemampuan GroupDocs.Parser dalam proyek Anda.

**Terakhir Diperbarui:** 2026-02-09  
**Diuji Dengan:** GroupDocs.Parser 25.5 for Java  
**Penulis:** GroupDocs