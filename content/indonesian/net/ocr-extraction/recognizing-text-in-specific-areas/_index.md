---
title: Mengenali Teks di Area Tertentu
linktitle: Mengenali Teks di Area Tertentu
second_title: GroupDocs.Parser .NET API
description: Pelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari area tertentu dalam dokumen dengan kemampuan OCR.
type: docs
weight: 13
url: /id/net/ocr-extraction/recognizing-text-in-specific-areas/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengenali dan mengekstrak teks dari area tertentu dalam dokumen. GroupDocs.Parser adalah pustaka penguraian dokumen canggih yang memungkinkan pengembang bekerja dengan berbagai format dokumen, termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi. Secara khusus, kami akan fokus pada pemanfaatan kemampuan OCR (Optical Character Recognition) GroupDocs.Parser untuk mengekstrak teks dari area tertentu dalam dokumen.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan prasyarat berikut:
1. Visual Studio IDE: Pastikan Anda telah menginstal Visual Studio di mesin Anda.
2.  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser untuk .NET dari[tautan unduhan](https://releases.groupdocs.com/parser/net/).
3. Sampel Dokumen: Siapkan file sampel (misalnya PDF, DOCX) yang teksnya ingin Anda ekstrak.

## Impor Namespace
Untuk memulai, impor namespace yang diperlukan ke dalam proyek Anda:
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

Mari kita bagi prosesnya menjadi langkah-langkah mendetail menggunakan GroupDocs.Parser untuk .NET:
## Langkah 1: Buat Pengaturan Parser dengan Konektor OCR
 Pertama, buat sebuah instance dari`ParserSettings`kelas dan inisialisasi dengan konektor OCR, seperti`AsposeOcrOnPremise`:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Langkah 2: Buat Instansiasi Parser dengan Pengaturan
 Selanjutnya, buat sebuah instance dari`Parser` kelas dengan melewati yang dibuat sebelumnya`ParserSettings`:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Cuplikan kode berlanjut...
}
```
 Mengganti`"YourSampleFile.pdf"` dengan jalur ke dokumen target Anda.
## Langkah 3: Konfigurasikan Opsi Ekstraksi Area Teks
 Buat sebuah contoh dari`PageTextAreaOptions` untuk mengaktifkan ekstraksi teks berbasis OCR:
```csharp
PageTextAreaOptions options = new PageTextAreaOptions(true);
```
 Mengatur`true` untuk mengaktifkan OCR untuk pengenalan teks yang lebih baik.
## Langkah 4: Ekstrak Area Teks
 Memohon`parser.GetTextAreas(options)` untuk mengekstrak area teks dari dokumen:
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Langkah 5: Proses Area Teks yang Diekstraksi
Ulangi area teks yang diekstraksi dan ambil informasi teks, posisi, dan ukuran:
```csharp
foreach (PageTextArea area in areas)
{
    Console.WriteLine(area.Text);
    Console.WriteLine($"\tPosition: ({area.Rectangle.Left}; {area.Rectangle.Top})");
    Console.WriteLine($"\tSize: ({area.Rectangle.Size.Width}; {area.Rectangle.Size.Height})");
}
```

## Kesimpulan
Dalam tutorial ini, kami telah membahas proses mengekstraksi teks dari area tertentu dalam dokumen menggunakan GroupDocs.Parser untuk .NET dengan kemampuan OCR. Dengan mengikuti langkah-langkah ini, Anda dapat secara efektif memanfaatkan fungsi penguraian GroupDocs.Parser untuk menangani tugas ekstraksi teks secara terprogram.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak teks dari dokumen yang dipindai?
Ya, GroupDocs.Parser mendukung OCR untuk mengekstraksi teks dari gambar yang dipindai di dalam dokumen.
### Format dokumen apa yang didukung oleh GroupDocs.Parser?
GroupDocs.Parser mendukung berbagai format, termasuk PDF, DOCX, XLSX, PPTX, TXT, dan banyak lagi.
### Apakah GroupDocs.Parser cocok untuk pemrosesan dokumen secara batch?
Ya, GroupDocs.Parser dapat secara efisien menangani tugas pemrosesan batch untuk penguraian dan ekstraksi dokumen.
### Bisakah saya menyesuaikan opsi ekstraksi teks dengan GroupDocs.Parser?
Ya, GroupDocs.Parser menawarkan berbagai opsi untuk menyesuaikan ekstraksi teks berdasarkan kebutuhan spesifik.
### Apakah GroupDocs.Parser menyediakan dukungan untuk mengekstraksi metadata dari dokumen?
Ya, GroupDocs.Parser memungkinkan ekstraksi metadata seperti penulis, tanggal pembuatan, dan lainnya dari format dokumen yang didukung.