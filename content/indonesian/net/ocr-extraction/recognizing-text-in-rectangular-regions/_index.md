---
title: Mengenali Teks pada Daerah Persegi Panjang
linktitle: Mengenali Teks pada Daerah Persegi Panjang
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengenali teks di wilayah dokumen tertentu menggunakan GroupDocs.Parser untuk .NET dengan kemampuan OCR.
weight: 14
url: /id/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---

# Mengenali Teks pada Daerah Persegi Panjang

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengenali teks dalam wilayah persegi panjang tertentu pada dokumen. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengekstrak teks, metadata, dan lainnya dari berbagai format file, termasuk PDF, Word, Excel, dan PowerPoint.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan yang berikut:
-  GroupDocs.Parser untuk .NET: Unduh dan instal perpustakaan dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Lingkungan Pengembangan: Visual Studio atau .NET IDE lainnya.
- Contoh Dokumen: Miliki contoh file (misalnya PDF, DOCX) yang berisi teks untuk dikenali.

## Impor Namespace
Pertama, Anda harus mengimpor namespace yang diperlukan ke dalam kode C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Inisialisasi Pengaturan Parser
 Mulailah dengan menyiapkan`ParserSettings` dengan konektor OCR. Di sini, kita akan menggunakan konektor lokal Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Langkah 2: Buat Instans Parser
 Selanjutnya, buat instance`Parser` kelas dengan pengaturan yang ditentukan sebelumnya:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Kode berlanjut di sini
}
```
 Mengganti`"YourSampleFile.pdf"` dengan jalur ke dokumen Anda.
## Langkah 3: Tentukan Persegi Panjang OCR
 Tentukan persegi panjang di dalam dokumen tempat pengenalan teks akan dilakukan. Misalnya persegi panjang yang dimulai dari`(0, 0)` dengan lebar`400` dan tinggi badan`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Langkah 4: Konfigurasikan Opsi Pengenalan Teks
 Membuat`TextOptions` untuk menentukan penggunaan OCR bersama dengan persegi panjang yang ditentukan:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Langkah 5: Ekstrak Teks menggunakan OCR
 Menggunakan`GetText` metode`Parser` contoh dengan yang dikonfigurasi`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Baca teks yang diekstraksi atau tangani kasus 'tidak didukung'
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Kesimpulan
Dalam tutorial ini, kami telah menunjukkan cara memanfaatkan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari wilayah persegi panjang tertentu dalam dokumen menggunakan OCR. Proses ini selanjutnya dapat disesuaikan dan diintegrasikan ke dalam berbagai aplikasi untuk tugas ekstraksi teks otomatis.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak teks dari dokumen yang dipindai?
Ya, GroupDocs.Parser mendukung OCR (Optical Character Recognition) untuk mengekstrak teks dari dokumen yang dipindai.
### Format file apa yang didukung GroupDocs.Parser?
GroupDocs.Parser mendukung berbagai format file, termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### Bagaimana cara menangani dokumen yang tidak didukung untuk ekstraksi teks?
 Anda dapat memeriksa apakah ekstraksi teks didukung menggunakan`TextReader` contoh dikembalikan oleh`parser.GetText(options)`.
### Apakah GroupDocs.Parser cocok untuk tugas ekstraksi teks skala besar?
Ya, GroupDocs.Parser dirancang untuk menangani tugas ekstraksi teks skala besar secara efisien.
### Di mana saya bisa mendapatkan dukungan untuk masalah terkait GroupDocs.Parser?
 Untuk dukungan dan diskusi, kunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).