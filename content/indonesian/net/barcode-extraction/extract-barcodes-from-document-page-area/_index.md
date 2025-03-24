---
title: Ekstrak Barcode dari Area Halaman Dokumen
linktitle: Ekstrak Barcode dari Area Halaman Dokumen
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak kode batang dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. Tingkatkan kemampuan pemrosesan dokumen Anda dengan tutorial langkah demi langkah ini.
weight: 13
url: /id/net/barcode-extraction/extract-barcodes-from-document-page-area/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara mengekstrak kode batang dari area tertentu pada dokumen menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan Anda mengurai dan mengekstrak data dari berbagai format dokumen seperti PDF, DOCX, XLSX, dan lainnya, termasuk mengekstraksi kode batang. Kami akan membahas prasyarat, namespace yang diperlukan, dan memberikan panduan langkah demi langkah dengan contoh kode untuk mendemonstrasikan prosesnya.
## Prasyarat
Sebelum mendalami proses ekstraksi kode batang, pastikan Anda telah menyiapkan prasyarat berikut:
1. Lingkungan Pengembangan: Instal Visual Studio atau lingkungan pengembangan .NET pilihan lainnya.
2.  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser untuk .NET dari[Unduh Halaman](https://releases.groupdocs.com/parser/net/).
3. Contoh Dokumen: Siapkan contoh dokumen (misalnya PDF, DOCX) yang berisi kode batang untuk diekstraksi.

## Impor Namespace
Untuk memulai ekstraksi kode batang, impor namespace yang diperlukan di proyek .NET Anda:
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Langkah 1: Buat Instans Parser
 Pertama, buat sebuah instance dari`Parser` kelas dengan menyediakan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode Anda untuk ekstraksi kode batang akan ditempatkan di sini
}
```
 Mengganti`"YourSampleFile.pdf"` dengan jalur ke dokumen Anda yang sebenarnya.
## Langkah 2: Periksa Dukungan Ekstraksi Barcode
 Sebelum mengekstrak kode batang, periksa apakah dokumen mendukung penggunaan ekstraksi kode batang`parser.Features.Barcodes`.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcodes extraction.");
    return;
}
```
Langkah ini memastikan bahwa dokumen memang dapat diproses untuk ekstraksi barcode.
## Langkah 3: Tentukan Area Ekstraksi Barcode
 Membuat`BarcodeOptions` menentukan area halaman dokumen untuk mengekstrak kode batang. Dalam contoh ini, kita akan mengekstrak barcode dari area persegi panjang tertentu (pojok kanan atas).
```csharp
BarcodeOptions options = new BarcodeOptions(new Rectangle(new Point(590, 80), new Size(150, 150)));
```
Sesuaikan koordinat dan ukuran (`Point` Dan`Size`) berdasarkan tata letak dokumen Anda dan area yang ingin Anda targetkan untuk ekstraksi barcode.
## Langkah 4: Ekstrak Barcode
 Menggunakan`parser.GetBarcodes(options)` untuk mengekstrak kode batang berdasarkan opsi yang ditentukan.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
Ini mengambil semua kode batang yang ditemukan dalam area tertentu pada dokumen.
## Langkah 5: Ulangi Barcode yang Diekstraksi
Ulangi kode batang yang diekstraksi untuk mengakses indeks dan nilai halaman setiap kode batang.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```
 Dalam putaran ini, masing-masing`barcode` objek berisi indeks halaman (`barcode.Page.Index`) dan nilai kode batang (`barcode.Value`).

## Kesimpulan
Dalam tutorial ini, kami telah membahas cara mengekstrak kode batang dari area halaman dokumen menggunakan GroupDocs.Parser untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan, Anda dapat mengintegrasikan kemampuan ekstraksi kode batang ke dalam aplikasi .NET Anda secara efektif.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak kode batang dari semua jenis dokumen?
Ya, GroupDocs.Parser mendukung ekstraksi kode batang dari berbagai format dokumen, tetapi tidak semua format mendukung fitur ini.
### Bagaimana cara menangani pengecualian selama ekstraksi kode batang?
Anda dapat menerapkan blok coba-tangkap di sekitar kode ekstraksi kode batang untuk menangani pengecualian dengan baik.
### Apakah GroupDocs.Parser memerlukan lisensi untuk penggunaan komersial?
Ya, lisensi GroupDocs.Parser yang valid diperlukan untuk penggunaan komersial. Anda dapat memperoleh lisensi dari[Di Sini](https://purchase.groupdocs.com/buy).
### Bisakah saya menyesuaikan area ekstraksi kode batang secara dinamis berdasarkan masukan pengguna?
 Ya, Anda dapat menyesuaikannya`Rectangle` koordinat dan ukuran secara dinamis berdasarkan parameter yang ditentukan pengguna.
### Di mana saya dapat menemukan bantuan dan dukungan lebih lanjut untuk GroupDocs.Parser?
 Mengunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) untuk dukungan dan diskusi komunitas.