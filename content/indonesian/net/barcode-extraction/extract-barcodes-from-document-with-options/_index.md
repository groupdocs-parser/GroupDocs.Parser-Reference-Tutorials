---
title: Ekstrak Barcode dari Dokumen dengan Opsi
linktitle: Ekstrak Barcode dari Dokumen dengan Opsi
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak kode batang dari dokumen menggunakan GroupDocs.Parser untuk .NET. Tutorial komprehensif dengan contoh kode dan FAQ.
weight: 14
url: /id/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## Perkenalan
Dalam tutorial ini, kita akan memandu proses mengekstraksi kode batang dari dokumen menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan Anda mengekstrak teks, metadata, dan kode batang dari berbagai format dokumen seperti PDF, Microsoft Word, Excel, dan banyak lagi.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki prasyarat berikut:
1. Lingkungan Pengembangan: Pastikan Anda telah menginstal Visual Studio di mesin Anda.
2.  Perpustakaan GroupDocs.Parser: Unduh dan instal perpustakaan GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/parser/net/).
3. Contoh Dokumen: Siapkan contoh dokumen (misalnya PDF, DOCX) yang berisi kode batang untuk diekstraksi.

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda untuk memanfaatkan fungsionalitas GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Langkah 1: Buat Instance Kelas Parser
 Untuk memulai, buat sebuah instance dari`Parser` kelas dengan meneruskan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode yang akan ditambahkan pada langkah berikutnya
}
```
## Langkah 2: Periksa Dukungan Ekstraksi Barcode
 Selanjutnya, periksa apakah dokumen mendukung ekstraksi barcode menggunakan`Features` properti dari`Parser` contoh.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Langkah 3: Tentukan Opsi Ekstraksi Barcode
 Sekarang, tentukan pilihan untuk ekstraksi barcode menggunakan`BarcodeOptions`. Anda dapat mengatur parameter seperti mode kualitas dan jenis kode batang.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Langkah 4: Ekstrak Barcode dari Dokumen
 Menggunakan`GetBarcodes` metode`Parser` kelas untuk mengekstrak kode batang berdasarkan opsi yang ditentukan.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Langkah 5: Ulangi dan Tampilkan Barcode yang Diekstraksi
Terakhir, ulangi kode batang yang diekstraksi dan tampilkan indeks halaman dan nilainya.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Kesimpulan
 Dalam tutorial ini, kita telah mempelajari cara mengekstrak kode batang dari dokumen menggunakan GroupDocs.Parser untuk .NET. Proses ini melibatkan pembuatan a`Parser` Misalnya, menentukan opsi ekstraksi, dan mengulangi kode batang yang diekstraksi. GroupDocs.Parser menyederhanakan tugas ekstraksi kode batang dari berbagai format dokumen, memungkinkan pemrosesan dokumen yang efisien dalam aplikasi .NET Anda.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak kode batang dari dokumen PDF?
Ya, GroupDocs.Parser mendukung ekstraksi kode batang dari dokumen PDF bersama dengan format lain seperti DOCX, XLSX, dll.
### Jenis kode batang apa yang didukung GroupDocs.Parser?
GroupDocs.Parser mendukung berbagai jenis kode batang termasuk kode QR, Kode 39, Kode 128, dan banyak lagi.
### Apakah GroupDocs.Parser memerlukan lisensi untuk penggunaan komersial?
 Ya, lisensi yang valid diperlukan untuk penggunaan komersial. Anda dapat memperoleh lisensi dari[Di Sini](https://purchase.groupdocs.com/buy).
### Apakah GroupDocs.Parser cocok untuk pemrosesan dokumen secara batch?
Ya, GroupDocs.Parser dapat secara efisien menangani pemrosesan batch dokumen untuk ekstraksi teks, pengambilan metadata, dan ekstraksi kode batang.
### Di mana saya dapat menemukan dukungan teknis untuk GroupDocs.Parser?
 Anda bisa mendapatkan dukungan teknis atau mengajukan pertanyaan di[Forum Grup Dokumen](https://forum.groupdocs.com/c/parser/17).