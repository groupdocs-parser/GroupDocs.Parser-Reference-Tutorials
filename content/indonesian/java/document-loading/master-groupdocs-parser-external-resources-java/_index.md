---
date: '2025-12-29'
description: Pelajari cara mengekstrak gambar dari dokumen dan cara memfilter sumber
  daya menggunakan GroupDocs.Parser untuk Java. Panduan ini mencakup konfigurasi,
  penangan khusus, dan contoh praktis.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: Ekstrak Gambar dari Dokumen dengan GroupDocs.Parser Java – Panduan
type: docs
url: /id/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Ekstrak Gambar dari Dokumen dan Filter Sumber Daya dengan GroupDocs.Parser Java

Mengekstrak gambar dari dokumen adalah kebutuhan umum saat membangun pipeline pemrosesan dokumen. Dalam tutorial ini Anda akan menemukan **cara mengekstrak gambar dari dokumen** menggunakan GroupDocs.Parser untuk Java, dan Anda juga akan belajar **cara memfilter sumber daya** sehingga hanya file yang Anda butuhkan yang dimuat. Kami akan membahas cara menyiapkan pustaka, membuat `ExternalResourceHandler` khusus, dan menerapkan logika pemfilteran untuk menjaga aplikasi Anda tetap cepat dan aman.

## Jawaban Cepat
- **Apa yang dilakukan GroupDocs.Parser?** Ia mem‑parsing berbagai format dokumen dan memberi Anda akses ke teks, gambar, dan sumber daya tersemat lainnya.  
- **Bisakah saya melewatkan gambar yang tidak diinginkan?** Ya—dengan mengimplementasikan `ExternalResourceHandler` khusus Anda dapat memutuskan sumber daya mana yang akan dimuat.  
- **Versi Maven mana yang diperlukan?** Gunakan GroupDocs.Parser Java 25.5 atau yang lebih baru.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk evaluasi; lisensi permanen diperlukan untuk produksi.  
- **Apakah pendekatan ini thread‑safe?** Objek parsing tidak dibagikan antar thread; buat instance `Parser` baru per thread.

## Apa itu “ekstrak gambar dari dokumen”?
Ketika sebuah dokumen berisi gambar tersemat, diagram, atau media lain, “ekstrak gambar dari dokumen” berarti secara programatik mengambil file biner tersebut sehingga Anda dapat menyimpannya, menampilkannya, atau memprosesnya lebih lanjut di luar file asli.

## Mengapa memfilter sumber daya saat mengekstrak gambar?
- Mengurangi konsumsi memori dengan mengabaikan file yang besar atau tidak relevan.  
- Meningkatkan keamanan dengan mencegah pemuatan konten yang berpotensi tidak aman.  
- Mempercepat proses, terutama pada dokumen besar yang berisi banyak objek tersemat.

## Prerequisites
- **Java Development Kit (JDK)** – versi 8 atau lebih tinggi.  
- **Maven** – untuk manajemen dependensi.  
- Familiaritas dasar dengan Java I/O dan penanganan exception.

## Menyiapkan GroupDocs.Parser untuk Java

Tambahkan repositori GroupDocs dan dependensi parser ke `pom.xml` Anda:

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

Atau, unduh versi terbaru dari [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Akuisisi Lisensi
- **Free Trial** – jelajahi fitur inti tanpa biaya.  
- **Temporary License** – buka semua fungsi selama evaluasi.  
- **Purchased License** – diperlukan untuk penyebaran komersial.

## Cara memfilter sumber daya saat mengekstrak gambar

### Langkah 1: Buat handler khusus
Definisikan kelas yang memperluas `ExternalResourceHandler`. Di dalam metode `onLoading` Anda memutuskan sumber daya mana yang akan dipertahankan.

```java
import com.groupdocs.parser.options.ExternalResourceHandler;
import com.groupdocs.parser.data.ExternalResourceLoadingArgs;

class Handler extends ExternalResourceHandler {
    @Override
    public void onLoading(ExternalResourceLoadingArgs args) {
        if (!args.getUri().endsWith("installation.png")) {
            args.setSkipped(true);
        }
        super.onLoading(args);
    }
}
```

### Langkah 2: Konfigurasikan `ParserSettings` dengan handler
Berikan instance `Handler` Anda ke `ParserSettings` dan gunakan saat membuka dokumen.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.IOException;
import com.groupdocs.parser.options.ParserSettings;

public class LoadExternalResources {
    public static void run() throws IOException {
        ParserSettings settings = new ParserSettings(new Handler());
        
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
            Iterable<PageImageArea> images = parser.getImages();
            
            for (PageImageArea image : images) {
                System.out.println(image.getFileType());
            }
        }
    }
}
```

### Langkah 3: Sesuaikan logika pemfilteran
Jika Anda memerlukan aturan yang lebih canggih—seperti memfilter berdasarkan ukuran gambar, format, atau pola URI—perluas metode `onLoading` sesuai:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Aplikasi Praktis
1. **Document Management Systems** – Ambil hanya gambar yang diperlukan dari kontrak yang dipindai untuk menghasilkan thumbnail.  
2. **Data Extraction Services** – Lewati grafik dekoratif dan fokus pada diagram yang berisi data berharga.  
3. **Web Scraping Tools** – Filter pixel pelacakan saat mengambil media bermakna dari dokumen berbasis HTML.

## Pertimbangan Kinerja
- **Filter lebih awal**: Terapkan handler khusus Anda sebelum mengiterasi sumber daya untuk menghindari memuat data yang tidak diinginkan ke memori.  
- **Buang segera**: Gunakan try‑with‑resources (`try (Parser parser = …)`) untuk membebaskan sumber daya native.  
- **Pemrosesan async**: Untuk batch besar, proses dokumen dalam aliran paralel sambil memastikan setiap instance `Parser` terbatas pada satu thread.

## Masalah Umum & Solusi
| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Tidak ada gambar yang dikembalikan | Handler secara tidak sengaja melewatkan semua sumber daya | Verifikasi kondisi `if` dan pastikan `args.setSkipped(true)` hanya dipanggil untuk URI yang tidak diinginkan. |
| `IOException` pada file besar | Memori heap tidak cukup | Tingkatkan heap JVM (`-Xmx2g`) atau proses halaman dalam potongan yang lebih kecil. |
| Lisensi tidak dikenali | Menggunakan DLL percobaan dengan kode produksi | Terapkan jalur file lisensi yang benar melalui `License.setLicense("path/license")`. |

## Pertanyaan yang Sering Diajukan

**Q: Apa tujuan utama menggunakan `ExternalResourceHandler` khusus?**  
A: Itu memungkinkan Anda mengontrol sumber daya eksternal mana yang dimuat, meningkatkan keamanan dan kinerja dengan memfilter file yang tidak diperlukan.

**Q: Bisakah saya menggunakan GroupDocs.Parser untuk Java tanpa lisensi?**  
A: Ya, percobaan gratis tersedia, tetapi beberapa fitur lanjutan mungkin terbatas sampai Anda memperoleh lisensi sementara atau berbayar.

**Q: Bagaimana cara menangani exception selama parsing dengan GroupDocs.Parser?**  
A: Bungkus panggilan parsing dalam blok try‑catch untuk `IOException` dan exception spesifik lainnya untuk menangani kesalahan secara elegan.

**Q: Apa jebakan umum saat memfilter sumber daya?**  
A: Pemeriksaan URI yang salah dapat melewatkan file yang diperlukan; gunakan logging atau breakpoint untuk memverifikasi kondisi Anda.

**Q: Apakah memungkinkan untuk mem‑parsing dokumen non‑HTML menggunakan GroupDocs.Parser untuk Java?**  
A: Tentu—GroupDocs.Parser mendukung PDF, Word, Excel, PowerPoint, dan banyak format lainnya.

## Langkah Selanjutnya
Selami lebih dalam pustaka dengan menjelajahi [API Reference](https://reference.groupdocs.com/parser/java) atau bereksperimen dengan pengaturan tambahan seperti `ParserSettings.setDetectTables(true)` untuk ekstraksi tabel.

---

**Last Updated:** 2025-12-29  
**Tested With:** GroupDocs.Parser 25.5 for Java  
**Author:** GroupDocs  

**Resources**  
- **Documentation:** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API Reference:** [API Details](https://reference.groupdocs.com/parser/java)  
- **Downloads:** [Latest Versions](https://releases.groupdocs.com/parser/java/)