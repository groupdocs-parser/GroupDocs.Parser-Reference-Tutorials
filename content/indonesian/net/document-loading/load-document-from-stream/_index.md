---
title: Muat Dokumen dari Aliran
linktitle: Muat Dokumen dari Aliran
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak teks dari berbagai format dokumen di .NET menggunakan GroupDocs.Parser. Panduan langkah demi langkah dengan contoh kode.
weight: 12
url: /id/net/document-loading/load-document-from-stream/
---
## Perkenalan
Dalam ranah pemrosesan dokumen pada aplikasi .NET, mengekstraksi teks dari berbagai format file merupakan kebutuhan umum. GroupDocs.Parser untuk .NET menawarkan solusi canggih untuk mengurai dan mengekstrak teks dengan lancar dari beragam dokumen. Tutorial ini akan memandu Anda melalui proses penggunaan GroupDocs.Parser untuk mengekstrak teks dari dokumen langkah demi langkah.
## Prasyarat
Sebelum mulai menggunakan GroupDocs.Parser untuk .NET, pastikan Anda telah menyiapkan hal berikut:
- Lingkungan Pengembangan: Visual Studio atau lingkungan pengembangan .NET lainnya.
-  GroupDocs.Parser untuk .NET Paket: Unduh dan instal perpustakaan GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Sampel Dokumen: Siapkan contoh dokumen untuk ekstraksi teks.
## Mengimpor Namespace
Mulailah dengan mengimpor namespace yang diperlukan ke proyek .NET Anda untuk mengakses fungsionalitas GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Langkah-langkah berikut menunjukkan cara mengekstrak teks dari dokumen menggunakan GroupDocs.Parser dari aliran.
## Langkah 1: Muat Dokumen dari Stream
```csharp
// Buat aliran
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Buat instance kelas Parser dengan aliran
    using (Parser parser = new Parser(stream))
    {
        // Ekstrak teks ke pembaca
        using (TextReader reader = parser.GetText())
        {
            // Cetak teks dari dokumen
            // Jika ekstraksi teks tidak didukung, pembaca akan menjadi nol
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
Dalam contoh ini:
- Kami membuka aliran file untuk file dokumen (`YourSampleFile.docx`).
-  Inisialisasi a`Parser` misalnya dengan aliran.
-  Menggunakan`parser.GetText()` untuk mengambil a`TextReader` berisi teks yang diekstraksi.
- Cetak teks atau pesan yang diekstraksi jika ekstraksi teks tidak didukung untuk format dokumen.
## Kesimpulan
GroupDocs.Parser untuk .NET menyederhanakan ekstraksi teks dari berbagai format dokumen, memungkinkan pengembang memproses dan memanfaatkan konten tekstual secara efisien dalam aplikasi mereka. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat dengan mudah mengintegrasikan kemampuan ekstraksi teks dokumen ke dalam proyek .NET Anda.

## FAQ
### Format dokumen apa yang didukung oleh GroupDocs.Parser untuk .NET?
GroupDocs.Parser mendukung berbagai format dokumen termasuk DOCX, PDF, XLSX, PPTX, EPUB, dan banyak lagi.
### Bisakah GroupDocs.Parser mengekstrak gambar atau metadata dari dokumen?
Ya, GroupDocs.Parser dapat mengekstrak gambar, metadata, dan teks dari berbagai jenis dokumen.
### Apakah GroupDocs.Parser kompatibel dengan aplikasi .NET Core?
Ya, GroupDocs.Parser kompatibel dengan aplikasi .NET Framework dan .NET Core.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat memperoleh lisensi sementara dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya dapat menemukan lebih banyak dukungan atau dokumentasi untuk GroupDocs.Parser?
 Untuk dukungan tambahan, kunjungi[GroupDocs.Forum Parser](https://forum.groupdocs.com/c/parser/17) atau rujuk ke[dokumentasi](https://tutorials.groupdocs.com/parser/net/).
