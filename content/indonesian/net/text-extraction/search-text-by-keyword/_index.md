---
title: Cari Teks berdasarkan Kata Kunci
linktitle: Cari Teks berdasarkan Kata Kunci
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mencari teks berdasarkan kata kunci dalam dokumen menggunakan GroupDocs.Parser untuk .NET. Ekstrak konten relevan secara efisien dengan mudah.
weight: 21
url: /id/net/text-extraction/search-text-by-keyword/
type: docs
---
# Cari Teks berdasarkan Kata Kunci

## Perkenalan
Dalam tutorial ini, kita akan mempelajari penggunaan GroupDocs.Parser untuk .NET untuk mencari teks berdasarkan kata kunci dalam dokumen. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengekstrak teks, metadata, dan informasi lainnya dari berbagai format file, seperti PDF, dokumen Microsoft Office, dan banyak lagi. Mencari kata kunci spesifik dalam dokumen-dokumen ini dapat menjadi penting untuk aplikasi yang menangani data tekstual dalam jumlah besar.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan yang berikut:
1. Lingkungan Pengembangan: Visual Studio atau .NET IDE pilihan lainnya.
2.  GroupDocs.Parser untuk .NET: Unduh perpustakaan dari[Di Sini](https://releases.groupdocs.com/parser/net/).
3. Akses ke File Sampel: Siapkan file sampel (misalnya PDF, DOCX) untuk menguji fungsionalitas pencarian kata kunci.

## Impor Namespace
Pertama, Anda perlu memasukkan namespace yang diperlukan dalam proyek Anda.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Langkah 1: Buat instance Kelas Parser
 Mulailah dengan membuat sebuah instance dari`Parser` kelas dan berikan jalur ke file sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Cari kata kunci
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Ulangi hasil pencarian
    foreach (SearchResult result in searchResults)
    {
        //Cetak indeks dan teks yang ditemukan
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Langkah 2: Cari Kata Kunci
 Dalam`using` blok, hubungi`Search` metode pada`parser` objek, meneruskan kata kunci yang diinginkan sebagai argumen.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Mengganti`"test"` dengan kata kunci yang ingin Anda cari di dalam dokumen.
## Langkah 3: Ulangi Hasil Pencarian
 Selanjutnya, ulangi hasil pencarian yang diperoleh dari`Search` metode menggunakan a`foreach` lingkaran.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Untuk setiap`SearchResult` obyek`result` , Anda dapat mengaksesnya`Position` (indeks) dan`Text` (teks yang ditemukan).

## Kesimpulan
 Dalam tutorial ini, kita mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mencari teks berdasarkan kata kunci dalam dokumen dengan mudah. Memanfaatkan`Search` metode`Parser` kelas memungkinkan pengambilan cuplikan teks yang relevan secara efisien berdasarkan istilah pencarian tertentu.

## FAQ
### Apakah GroupDocs.Parser kompatibel dengan berbagai format dokumen?
Ya, GroupDocs.Parser mendukung berbagai format file, termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### Bisakah saya melakukan operasi ekstraksi teks tingkat lanjut menggunakan GroupDocs.Parser?
Sangat! Selain pencarian teks, GroupDocs.Parser memungkinkan ekstraksi metadata, ekstraksi teks terstruktur, dan banyak lagi.
### Di mana saya dapat menemukan dokumentasi terperinci untuk GroupDocs.Parser?
Jelajahi dokumentasi lengkapnya[Di Sini](https://tutorials.groupdocs.com/parser/net/).
### Bagaimana saya bisa mendapatkan dukungan atau bantuan dengan pertanyaan terkait GroupDocs.Parser?
 Kunjungi forum GroupDocs untuk dukungan dan diskusi[Di Sini](https://forum.groupdocs.com/c/parser/17).
### Apakah ada versi uji coba yang tersedia untuk mengevaluasi GroupDocs.Parser sebelum membeli?
 Ya, Anda dapat mengakses uji coba gratis[Di Sini](https://releases.groupdocs.com/).