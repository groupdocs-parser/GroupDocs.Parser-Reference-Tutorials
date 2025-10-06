---
title: Ekstrak Gambar dari Area Halaman Dokumen
linktitle: Ekstrak Gambar dari Area Halaman Dokumen
second_title: GroupDocs.Parser .NET API
description: Temukan cara mengekstrak gambar dari dokumen dengan tepat menggunakan Groupdocs.Parser untuk .NET. Pelajari cara menargetkan area tertentu untuk ekstraksi gambar yang akurat.
weight: 10
url: /id/net/image-extraction/extract-images-from-document-page-area/
type: docs
---
# Ekstrak Gambar dari Area Halaman Dokumen

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan Groupdocs.Parser untuk .NET untuk mengekstrak gambar dari area tertentu pada halaman dokumen. Proses ini memungkinkan Anda menargetkan dan mengambil gambar secara tepat berdasarkan koordinat dan dimensi yang ditentukan dalam dokumen.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
- Visual Studio diinstal pada mesin Anda
-  Groupdocs.Parser untuk perpustakaan .NET. Anda dapat mengunduhnya[Di Sini](https://releases.groupdocs.com/parser/net/)
- Contoh file dokumen yang akan digunakan untuk ekstraksi gambar
## Mengimpor Namespace
Mulailah dengan mengimpor namespace yang diperlukan dalam kode C# Anda untuk mengakses fungsionalitas Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Inisialisasi Mesin Virtual Parser
 Buat sebuah instance dari`Parser` kelas dan berikan jalur ke file dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode Anda ada di sini
}
```
## Langkah 2: Tentukan Opsi Ekstraksi
 Tentukan opsi ekstraksi untuk menentukan area tempat Anda ingin mengekstrak gambar. Menggunakan`PageAreaOptions` dan menyediakan a`Rectangle` mewakili area yang diinginkan pada halaman.
```csharp
PageAreaOptions options = new PageAreaOptions(new Rectangle(new Point(340, 150), new Size(300, 100)));
```
Dalam contoh ini:
- `(340, 150)`mewakili koordinat sudut kiri atas area tersebut
- `300` adalah lebar area tersebut
- `100` adalah ketinggian daerah tersebut
## Langkah 3: Ekstrak Gambar
 Panggil`GetImages` metode`Parser` Misalnya, melewati yang ditentukan`PageAreaOptions` . Ini akan mengembalikan koleksi yang tak terhitung banyaknya`PageImageArea` objek yang berisi gambar yang diekstraksi.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages(options);
```
## Langkah 4: Periksa Dukungan Ekstraksi
 Verifikasi apakah operasi ekstraksi didukung untuk dokumen yang ditentukan. Jika`images` koleksi adalah`null`, ekstraksi gambar tidak didukung.
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## Langkah 5: Ulangi Gambar yang Diekstraksi
 Ulangi`images` koleksi untuk memproses setiap gambar yang diekstraksi. Gambar yang diekstraksi diwakili oleh`PageImageArea` objek, menyediakan indeks halaman, detail persegi panjang, dan tipe gambar.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
    // Pemrosesan lebih lanjut dapat dilakukan dengan setiap gambar
}
```
## Kesimpulan
Selamat! Anda telah mempelajari cara mengekstrak gambar dari area tertentu pada dokumen menggunakan Groupdocs.Parser untuk .NET. Pendekatan ini memungkinkan ekstraksi gambar secara tepat berdasarkan koordinat yang ditentukan, sehingga memungkinkan pengambilan gambar yang ditargetkan dari dokumen.

## FAQ
### Bisakah saya mengekstrak gambar dari file PDF menggunakan metode ini?
Ya, Groupdocs.Parser mendukung ekstraksi gambar dari berbagai format dokumen termasuk file PDF.
### Bagaimana cara menangani pengecualian selama ekstraksi gambar?
Anda dapat menggunakan blok try-catch untuk menangani pengecualian yang mungkin terjadi selama proses ekstraksi.
### Apakah ada versi uji coba yang tersedia untuk Groupdocs.Parser untuk .NET?
 Ya, Anda bisa mendapatkan uji coba gratis[Di Sini](https://releases.groupdocs.com/).
### Apakah Groupdocs.Parser mendukung ekstraksi dari dokumen terenkripsi atau dilindungi kata sandi?
Ya, Groupdocs.Parser dapat menangani ekstraksi dari dokumen yang dilindungi kata sandi dengan izin yang sesuai.
### Di mana saya bisa mendapatkan dukungan teknis untuk Groupdocs.Parser?
 Untuk dukungan teknis dan diskusi, kunjungi[Forum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).