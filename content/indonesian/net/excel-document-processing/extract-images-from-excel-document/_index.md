---
title: Ekstrak Gambar dari Dokumen Excel
linktitle: Ekstrak Gambar dari Dokumen Excel
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak gambar dari dokumen Excel menggunakan GroupDocs.Parser untuk .NET. Panduan langkah demi langkah dengan contoh kode.
weight: 10
url: /id/net/excel-document-processing/extract-images-from-excel-document/
type: docs
---
# Ekstrak Gambar dari Dokumen Excel

## Perkenalan
Dalam tutorial ini, Anda akan mempelajari cara mengekstrak gambar dari dokumen Excel menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan Anda mengurai dan mengekstrak teks, metadata, dan gambar dari berbagai format dokumen termasuk file Excel.
## Prasyarat
Sebelum memulai, pastikan Anda telah menyiapkan prasyarat berikut:
1. Lingkungan Pengembangan: Instal Visual Studio atau lingkungan pengembangan .NET pilihan lainnya.
2.  Perpustakaan GroupDocs.Parser: Unduh dan rujuk perpustakaan GroupDocs.Parser. Anda bisa mendapatkan perpustakaan dari[Di Sini](https://releases.groupdocs.com/parser/net/).
3. Contoh File Excel: Siapkan contoh file Excel yang gambarnya ingin Anda ekstrak.
## Impor Namespace
Sertakan namespace yang diperlukan dalam proyek Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Ikuti langkah-langkah berikut untuk mengekstrak gambar dari dokumen Excel:
## Langkah 1: Buat instance Kelas Parser
 Pertama, buat sebuah instance dari`Parser` kelas dengan menyediakan jalur ke file Excel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Kode Anda di sini...
}
```
## Langkah 2: Ambil Gambar dari Dokumen Excel
 Menggunakan`GetImages()` metode untuk mengekstrak gambar dari file Excel.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Langkah 3: Tentukan Opsi Ekstraksi Gambar
Tentukan format gambar dan opsi lain untuk menyimpan gambar yang diekstraksi. Misalnya untuk menyimpan gambar dalam format PNG:
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Langkah 4: Ulangi dan Simpan Gambar
Ulangi gambar yang diekstraksi dan simpan setiap gambar ke file.
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
Dalam tutorial ini, Anda telah mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak gambar dari dokumen Excel. Dengan mengikuti langkah-langkah ini, Anda dapat menggabungkan kemampuan ekstraksi gambar ke dalam aplikasi .NET Anda secara efisien.

## FAQ
### T: Bisakah GroupDocs.Parser mengekstrak gambar dari format dokumen lain selain Excel?
J: Ya, GroupDocs.Parser mendukung berbagai format dokumen termasuk Word, PowerPoint, PDF, dan banyak lagi.
### T: Bagaimana saya bisa mendapatkan dukungan atau bantuan dengan integrasi GroupDocs.Parser?
 J: Untuk dukungan dan bantuan, kunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### T: Apakah GroupDocs.Parser gratis untuk digunakan?
 J: GroupDocs.Parser menawarkan uji coba gratis, namun untuk penggunaan berkelanjutan, Anda mungkin perlu membeli lisensi. Periksalah[penetapan harga dan lisensi](https://purchase.groupdocs.com/buy)detail.
### T: Dapatkah saya mencoba GroupDocs.Parser sebelum membeli lisensi?
 A: Ya, Anda bisa mendapatkan[uji coba gratis](https://releases.groupdocs.com/) untuk mengevaluasi GroupDocs.Parser.
### T: Di mana saya dapat menemukan dokumentasi terperinci untuk GroupDocs.Parser?
 A: Lihat secara komprehensif[dokumentasi](https://tutorials.groupdocs.com/parser/net/) untuk informasi rinci tentang penggunaan GroupDocs.Parser.