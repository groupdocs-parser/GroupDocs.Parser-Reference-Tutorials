---
title: Ekstrak Gambar dari Halaman Dokumen
linktitle: Ekstrak Gambar dari Halaman Dokumen
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak gambar dari dokumen menggunakan GroupDocs.Parser untuk .NET. Tingkatkan kemampuan pemrosesan dokumen Anda.
weight: 12
url: /id/net/image-extraction/extract-images-from-document-page/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara mengekstrak gambar dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan Anda mengekstrak teks, metadata, gambar, dan lainnya dari berbagai format dokumen seperti PDF, Microsoft Word, Excel, PowerPoint, dan lainnya. Kami akan memandu langkah-langkah yang diperlukan untuk mengekstrak gambar dari halaman dokumen menggunakan perpustakaan ini.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
- Visual Studio diinstal pada mesin Anda.
- Pemahaman dasar tentang pemrograman C# dan .NET.
- GroupDocs.Parser untuk perpustakaan .NET diinstal. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/parser/net/).

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan dalam proyek C# Anda untuk memanfaatkan fungsionalitas GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Mulailah dengan membuat sebuah instance dari`Parser` kelas dan tentukan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode Anda di sini
}
```
## Langkah 2: Periksa Dokumen untuk Dukungan Ekstraksi Gambar
 Selanjutnya, periksa apakah dokumen mendukung ekstraksi gambar menggunakan`Features.Images` Properti.
```csharp
if (!parser.Features.Images)
{
    Console.WriteLine("Document doesn't support image extraction.");
    return;
}
```
## Langkah 3: Dapatkan Informasi Dokumen
 Ambil informasi tentang dokumen menggunakan`GetDocumentInfo()` metode.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Langkah 4: Ulangi Halaman Dokumen
Periksa apakah dokumen berisi halaman dan kemudian ulangi setiap halaman untuk mengekstrak gambar.
```csharp
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Kode Anda untuk mengekstrak gambar dari halaman
}
```
## Langkah 5: Ekstrak Gambar dari Setiap Halaman
 Dalam loop iterasi halaman, gunakan`GetImages(pageIndex)` metode untuk mengambil gambar dari setiap halaman.
```csharp
foreach (PageImageArea image in parser.GetImages(pageIndex))
{
    Console.WriteLine($"Rectangle: {image.Rectangle}, FileType: {image.FileType}");
    // Kode tambahan untuk menyimpan atau memproses gambar
}
```

## Kesimpulan
Dalam tutorial ini, kita menjelajahi cara mengekstrak gambar dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. Kami membahas langkah-langkah penting seperti membuat instance parser, memeriksa dukungan ekstraksi gambar, mengambil informasi dokumen, mengulangi halaman, dan mengekstraksi gambar dari setiap halaman. Sekarang, Anda dapat mengintegrasikan fungsionalitas ekstraksi gambar ke dalam aplikasi .NET Anda secara efisien.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak gambar dari dokumen PDF?
Ya, GroupDocs.Parser mendukung ekstraksi gambar dari berbagai format dokumen termasuk PDF.
### Apakah GroupDocs.Parser cocok untuk pemrosesan dokumen secara batch?
Sangat! Anda dapat menggunakan GroupDocs.Parser untuk memproses banyak dokumen secara batch dan mengekstrak konten yang diinginkan secara efisien.
### Di mana saya dapat menemukan lebih banyak sumber daya dan dukungan untuk GroupDocs.Parser?
 Anda dapat mengunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) untuk dukungan dan diskusi komunitas.
### Bisakah saya mencoba GroupDocs.Parser sebelum membeli?
 Ya, Anda bisa mendapatkan[versi percobaan gratis](https://releases.groupdocs.com/) untuk mengevaluasi kemampuan perpustakaan.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat memperoleh a[izin sementara](https://purchase.groupdocs.com/temporary-license/) untuk tujuan pengujian dan pengembangan.