---
title: Cari Teks di Dokumen Word berdasarkan Kata Kunci
linktitle: Cari Teks di Dokumen Word berdasarkan Kata Kunci
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mencari teks di dokumen Word menggunakan GroupDocs.Parser untuk .NET. Ekstrak kata kunci tertentu secara efisien.
weight: 18
url: /id/net/word-document-processing/search-text-in-word-document-by-keyword/
---

# Cari Teks di Dokumen Word berdasarkan Kata Kunci

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mencari teks tertentu dalam dokumen Word menggunakan C#. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengekstrak teks dan metadata dari berbagai format dokumen, termasuk dokumen Word.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki prasyarat berikut:
1. Lingkungan Pengembangan: Instal Visual Studio atau IDE lain yang kompatibel.
2.  Perpustakaan GroupDocs.Parser: Unduh dan instal perpustakaan GroupDocs.Parser untuk .NET dari[situs web](https://releases.groupdocs.com/parser/net/).
3. Contoh Dokumen Word: Siapkan contoh dokumen Word yang akan digunakan untuk pencarian teks.

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Langkah 1: Buat Instance Kelas Parser
 Pertama, buat sebuah instance dari`Parser` kelas dengan meneruskan jalur ke contoh dokumen Word Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode ada di sini
}
```
## Langkah 2: Cari Kata Kunci
 Selanjutnya, gunakan`Search` metode`Parser` kelas untuk mencari kata kunci tertentu dalam dokumen.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Mengganti`"keyword"` dengan teks yang ingin Anda cari di dalam dokumen.
## Langkah 3: Ulangi Hasil Pencarian
 Ulangi hasil pencarian menggunakan a`foreach` loop untuk mengakses masing-masing`SearchResult` obyek.
```csharp
foreach (SearchResult result in searchResults)
{
    //Kode untuk menangani setiap hasil pencarian
}
```
## Langkah 4: Akses Detail Hasil Pencarian
 Dalam loop, Anda dapat mengakses posisi dan teks setiap hasil pencarian menggunakan`Position` Dan`Text` properti dari`SearchResult` obyek.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Cuplikan kode ini mencetak indeks (`Position`) dan teks yang ditemukan (`Text`) untuk setiap hasil pencarian ke konsol.

## Kesimpulan
Dalam tutorial ini, Anda telah mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mencari teks tertentu dalam dokumen Word. Pustaka ini menyediakan cara mudah untuk mengekstrak dan memanipulasi konten dari berbagai format dokumen secara terprogram.

## FAQ
### Bisakah GroupDocs.Parser menangani format dokumen lain selain Word?
Ya, GroupDocs.Parser mendukung berbagai format, termasuk PDF, Excel, PowerPoint, dan banyak lagi.
### Apakah GroupDocs.Parser kompatibel dengan .NET Core?
Ya, GroupDocs.Parser kompatibel dengan .NET Framework dan .NET Core.
### Bagaimana cara mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat meminta lisensi sementara dari[Halaman pembelian GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya dapat menemukan dukungan tambahan atau mengajukan pertanyaan tentang GroupDocs.Parser?
 Mengunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) untuk dukungan dan diskusi komunitas.
### Bisakah saya mencoba GroupDocs.Parser secara gratis sebelum membeli?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Halaman rilis GroupDocs](https://releases.groupdocs.com/).