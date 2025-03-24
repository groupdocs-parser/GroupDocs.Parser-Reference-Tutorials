---
title: Ekstrak Gambar dari Dokumen
linktitle: Ekstrak Gambar dari Dokumen
second_title: GroupDocs.Parser .NET API
description: Ekstrak gambar dari dokumen dengan mudah menggunakan GroupDocs.Parser untuk .NET. Kemampuan pemrosesan dokumen Anda dan menyederhanakan tugas ekstraksi gambar secara efisien.
weight: 11
url: /id/net/image-extraction/extract-images-from-document/
---

# Ekstrak Gambar dari Dokumen

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara mengekstrak gambar dari dokumen menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengekstrak teks, metadata, gambar, dan lainnya dari berbagai format dokumen.
## Prasyarat
Sebelum memulai, pastikan Anda telah menyiapkan prasyarat berikut:
- Visual Studio: Instal Visual Studio di mesin Anda.
-  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser dari[Unduh Halaman](https://releases.groupdocs.com/parser/net/).
- Contoh Dokumen: Siapkan contoh dokumen (PDF, DOCX, dll.) yang gambarnya ingin Anda ekstrak.

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Langkah 1: Buat Instance Kelas Parser
 Pertama, buat sebuah instance dari`Parser` kelas dengan menyediakan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode Anda ada di sini
}
```
 Mengganti`"YourSampleFile.pdf"` dengan jalur ke file dokumen Anda.
## Langkah 2: Ekstrak Gambar dari Dokumen
 Selanjutnya, ekstrak gambar dari dokumen menggunakan`GetImages()` metode.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 Itu`GetImages()` metode mengembalikan koleksi`PageImageArea` objek yang mewakili gambar yang ditemukan dalam dokumen.
## Langkah 3: Periksa Dukungan Ekstraksi Gambar
Sebelum mengulangi gambar, periksa apakah ekstraksi gambar didukung untuk dokumen tersebut.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Langkah ini memastikan bahwa dokumen berisi gambar yang dapat diekstraksi.
## Langkah 4: Ulangi Gambar yang Diekstraksi
Sekarang, ulangi gambar yang diekstraksi untuk mengakses informasi detail tentang setiap gambar, seperti indeks halaman, koordinat persegi panjang, dan jenis gambar.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Loop ini mencetak informasi tentang setiap gambar yang diekstraksi, termasuk lokasi dan jenisnya.

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak gambar dari dokumen secara terprogram. Dengan mengikuti langkah-langkah ini, Anda dapat mengintegrasikan fungsionalitas ekstraksi gambar dokumen ke dalam aplikasi .NET Anda dengan lancar.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak gambar dari semua format dokumen?
GroupDocs.Parser mendukung ekstraksi gambar dari berbagai format, termasuk PDF, DOCX, XLSX, dan banyak lagi.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat mengakses uji coba gratis GroupDocs.Parser dari[situs web](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dokumentasi untuk GroupDocs.Parser?
 Dokumentasi terperinci untuk GroupDocs.Parser dapat ditemukan[Di Sini](https://tutorials.groupdocs.com/parser/net/).
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat memperoleh lisensi sementara dari[halaman lisensi sementara](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Parser?
 Untuk dukungan dan bantuan teknis, kunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).