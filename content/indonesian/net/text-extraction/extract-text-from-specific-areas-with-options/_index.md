---
title: Ekstrak Teks dari Area Tertentu dengan Opsi
linktitle: Ekstrak Teks dari Area Tertentu dengan Opsi
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak teks dari area tertentu dalam dokumen menggunakan GroupDocs.Parser untuk .NET. Jelajahi opsi ekstraksi teks tingkat lanjut dengan tutorial ini.
weight: 14
url: /id/net/text-extraction/extract-text-from-specific-areas-with-options/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari area tertentu dalam dokumen menggunakan opsi yang dapat disesuaikan. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengurai dan mengekstrak teks dari berbagai format dokumen dengan mudah.
## Prasyarat
Sebelum kita mendalami pengkodean, pastikan Anda memiliki hal berikut:
1. Lingkungan Pengembangan: Instal Visual Studio atau IDE pengembangan .NET lainnya.
2.  Perpustakaan GroupDocs.Parser: Unduh dan instal GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/parser/net/).
3. File Contoh: Siapkan contoh dokumen (misalnya, PDF, DOCX, dll.) untuk mengekstrak teks.

## Impor Namespace
Pertama, Anda harus mengimpor namespace yang diperlukan untuk mengakses kelas dan metode GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Inisialisasi sebuah instance dari`Parser` kelas dengan menyediakan jalur ke file sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode untuk ekstraksi area teks akan ditempatkan di sini
}
```
## Langkah 2: Tentukan Opsi Ekstraksi Area Teks
 Membuat`PageTextAreaOptions` untuk menentukan kriteria ekstraksi teks.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
Dalam contoh ini:
- `"\\s[a-z]{2}\\s"` adalah pola ekspresi reguler untuk mencocokkan area teks yang hanya berisi huruf kecil.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` mendefinisikan persegi panjang (posisi dan ukuran) pada halaman untuk mengekstrak teks.
## Langkah 3: Ekstrak Area Teks
Gunakan opsi yang ditentukan untuk mengekstrak area teks yang memenuhi kriteria yang ditentukan.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Langkah 4: Periksa dan Ulangi Area Teks yang Diekstraksi
Periksa apakah ekstraksi area teks didukung dan kemudian ulangi area yang diekstraksi.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Kesimpulan
Dalam tutorial ini, kami telah membahas cara mengekstrak teks dari area tertentu dalam dokumen menggunakan GroupDocs.Parser untuk .NET. Pustaka ini menawarkan kemampuan ekstensif untuk mengurai berbagai format dokumen, menjadikannya alat yang berharga untuk tugas ekstraksi teks.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak teks dari dokumen yang dipindai?
Ya, GroupDocs.Parser mendukung ekstraksi teks berbasis OCR untuk dokumen yang dipindai.
### Apakah GroupDocs.Parser kompatibel dengan berbagai format dokumen?
Ya, itu dapat mengurai dan mengekstrak teks dari PDF, DOCX, XLSX, PPTX, dan format populer lainnya.
### Apakah GroupDocs.Parser menyediakan dukungan untuk .NET Core?
Ya, GroupDocs.Parser kompatibel dengan .NET Core serta .NET Framework.
### Bisakah saya mengekstrak metadata beserta teks menggunakan GroupDocs.Parser?
Ya, Anda dapat mengekstrak konten tekstual dan metadata dari dokumen.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Parser?
 Ya, Anda bisa mendapatkan uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).