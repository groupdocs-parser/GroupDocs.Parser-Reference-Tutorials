---
title: Ekstrak Barcode dari Dokumen yang Rusak
linktitle: Ekstrak Barcode dari Dokumen yang Rusak
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak kode batang dari dokumen yang rusak menggunakan GroupDocs.Parser untuk .NET. Tutorial komprehensif dengan petunjuk langkah demi langkah.
weight: 11
url: /id/net/barcode-extraction/extract-barcodes-from-corrupted-document/
---
## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses mengekstraksi kode batang dari dokumen yang rusak menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah API penguraian dokumen canggih yang memungkinkan pengembang mengekstrak teks, metadata, gambar, dan sekarang, kode batang dari berbagai format file. Kami akan merinci langkah-langkah yang diperlukan untuk menyelesaikan tugas ini secara efektif.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
-  GroupDocs.Parser untuk .NET: Anda dapat mengunduh perpustakaan dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Lingkungan Pengembangan: Visual Studio atau IDE pengembangan .NET lainnya.
- Contoh Dokumen yang Rusak: Siapkan contoh dokumen yang rusak (misalnya PDF, DOCX) untuk pengujian.

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan untuk proyek .NET Anda:
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Langkah 1: Inisialisasi Parser
 Pertama, inisialisasi`Parser` objek dengan jalur file sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFilePath"))
{
    // Lanjutkan dengan ekstraksi barcode...
}
```
## Langkah 2: Periksa Dukungan Ekstraksi Barcode
Sebelum melanjutkan, pastikan dokumen mendukung ekstraksi kode batang:
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcodes extraction.");
    return;
}
```
## Langkah 3: Tetapkan Opsi Ekstraksi Barcode
Tentukan opsi untuk ekstraksi kode batang. Anda dapat menentukan parameter seperti jenis kode batang, mode kualitas, dan pengaturan lainnya:
```csharp
BarcodeOptions options = new BarcodeOptions(
    null,
    QualityMode.Low,
    QualityMode.Low,
    null,
    true,
    "pdf417",
    "QR"
);
```
## Langkah 4: Ekstrak Barcode
Sekarang, ekstrak kode batang dari dokumen menggunakan opsi yang ditentukan:
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Langkah 5: Ulangi dan Proses Barcode
Ulangi kode batang yang diekstraksi dan proses masing-masing:
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
    Console.WriteLine("Confidence: " + barcode.Confidence.ToString());
}
```

## Kesimpulan
Dalam tutorial ini, kami mendemonstrasikan cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak kode batang dari dokumen yang rusak. Dengan mengikuti langkah-langkah ini, Anda dapat mengambil informasi barcode secara efisien dari berbagai format file menggunakan pendekatan yang mudah dan efektif.

## FAQ
### Bisakah GroupDocs.Parser menangani berbagai jenis kode batang?
Ya, GroupDocs.Parser mendukung berbagai jenis kode batang termasuk kode QR, PDF417, dan banyak lagi.
### Format file apa yang didukung GroupDocs.Parser untuk ekstraksi kode batang?
GroupDocs.Parser dapat mengekstrak kode batang dari format populer seperti PDF, DOCX, XLSX, dan lainnya.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat mengakses versi uji coba gratis[Di Sini](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Parser?
 Untuk dukungan dan diskusi, kunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat memperoleh lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).