---
title: Ekstrak Gambar dari Dokumen Word
linktitle: Ekstrak Gambar dari Dokumen Word
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak gambar dari dokumen Word menggunakan GroupDocs.Parser untuk .NET. Tutorial ini memberikan panduan langkah demi langkah untuk mengintegrasikan gambar ke .NET Anda.
weight: 11
url: /id/net/word-document-processing/extract-images-from-word-document/
---

# Ekstrak Gambar dari Dokumen Word

## Perkenalan
Dalam tutorial ini, Anda akan mempelajari cara mengekstrak gambar dari dokumen Word menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah pustaka .NET canggih yang memungkinkan Anda mengurai dan mengekstrak teks, metadata, gambar, dan lainnya dari berbagai format dokumen termasuk Word (DOCX).
## Prasyarat
Sebelum memulai, pastikan Anda telah menyiapkan prasyarat berikut:
- Visual Studio diinstal pada mesin Anda.
- Pengetahuan dasar tentang pemrograman C#.
- GroupDocs.Parser untuk perpustakaan .NET diinstal. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/parser/net/).
## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda untuk menggunakan fungsionalitas GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Sekarang, mari kita uraikan proses mengekstraksi gambar dari dokumen Word menjadi langkah-langkah sederhana:
## Langkah 1: Buat Instance Kelas Parser
 Anda akan mulai dengan membuat sebuah instance dari`Parser`kelas, menyediakan jalur ke dokumen Word Anda sebagai masukan.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode untuk ekstraksi gambar ada di sini
}
```
## Langkah 2: Ekstrak Gambar dari Dokumen Word
 Selanjutnya, gunakan`GetImages()` metode`Parser` objek untuk mengekstrak gambar dari dokumen.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Langkah 3: Tentukan Opsi Penyimpanan Gambar
Tentukan opsi untuk menyimpan gambar yang diekstraksi. Misalnya, Anda dapat memilih format gambar (misalnya PNG) dan mengonfigurasi pengaturan lainnya.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Langkah 4: Ulangi Gambar yang Diekstraksi dan Simpan
Ulangi setiap gambar yang diekstraksi dan simpan ke file menggunakan opsi yang ditentukan.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Simpan gambar ke file PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Kesimpulan
Dalam tutorial ini, Anda telah mempelajari cara mengekstrak gambar dari dokumen Word menggunakan GroupDocs.Parser untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengintegrasikan kemampuan penguraian dokumen dan ekstraksi gambar ke dalam aplikasi .NET Anda.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak gambar dari format dokumen lain selain Word?
Ya, GroupDocs.Parser mendukung berbagai format dokumen termasuk PDF, PowerPoint, Excel, dan lainnya.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat memperoleh lisensi sementara untuk tujuan pengujian dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang GroupDocs.Parser untuk .NET?
 Anda dapat merujuk ke dokumentasi lengkapnya[Di Sini](https://tutorials.groupdocs.com/parser/net/).
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat menjelajahi fitur GroupDocs.Parser dengan uji coba gratis yang tersedia[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan atau mengajukan pertanyaan terkait GroupDocs.Parser?
 Anda dapat memposting pertanyaan Anda di[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).