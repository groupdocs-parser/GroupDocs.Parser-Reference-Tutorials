---
title: Ekstrak Teks dari Dokumen Excel sebagai HTML
linktitle: Ekstrak Teks dari Dokumen Excel sebagai HTML
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak teks dari dokumen Excel dan mengubahnya menjadi HTML menggunakan GroupDocs.Parser untuk .NET.
type: docs
weight: 13
url: /id/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari dokumen Excel dan mengubahnya menjadi format HTML. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang bekerja dengan berbagai format dokumen, mengekstraksi teks dan metadata secara efisien.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan yang berikut:
- Visual Studio diinstal pada sistem Anda.
- Pemahaman dasar pemrograman C#.
-  Pustaka GroupDocs.Parser untuk .NET. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/parser/net/).
## Impor Namespace
Mulailah dengan memasukkan namespace yang diperlukan dalam proyek C# Anda untuk mengakses fungsionalitas GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Pertama, buat contoh`Parser` kelas dengan menyediakan jalur ke dokumen Excel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Kode selanjutnya akan ditempatkan di sini
}
```
 Mengganti`"YourSampleFile.xlsx"` dengan jalur ke file Excel Anda.
## Langkah 2: Ekstrak Teks sebagai HTML
 Dalam`using` blok dari`Parser` Misalnya, gunakan`GetFormattedText` metode untuk mengekstrak teks yang diformat dalam mode HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Kode selanjutnya akan ditempatkan di sini
    }
}
```
## Langkah 3: Baca dan Cetak Teks HTML yang Diekstraksi
 Selanjutnya, baca teks HTML yang diekstrak dari`TextReader` dan mencetaknya ke konsol.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Setelah dijalankan, kode ini akan mengekstrak teks dari dokumen Excel dan menampilkannya sebagai format HTML di konsol.
## Kesimpulan
Dalam tutorial ini, kita mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari dokumen Excel dan mengubahnya menjadi format HTML. Pustaka ini menyediakan cara mudah untuk bekerja dengan berbagai format dokumen, memungkinkan pengembang menangani tugas ekstraksi teks secara efisien dalam aplikasi mereka.

## FAQ
### Bisakah GroupDocs.Parser menangani format dokumen lain selain Excel?
Ya, GroupDocs.Parser mendukung berbagai format file termasuk PDF, Word, PowerPoint, dan banyak lagi.
### Apakah GroupDocs.Parser kompatibel dengan .NET Core?
Ya, GroupDocs.Parser kompatibel dengan .NET Framework dan .NET Core.
### Apakah GroupDocs.Parser mempertahankan pemformatan selama ekstraksi teks?
Ya, GroupDocs.Parser dapat mempertahankan pemformatan seperti font, gaya, dan tata letak selama ekstraksi teks.
### Bisakah saya mengekstrak metadata dari dokumen menggunakan GroupDocs.Parser?
Ya, GroupDocs.Parser memungkinkan ekstraksi metadata seperti penulis, tanggal pembuatan, dan lainnya dari jenis dokumen yang didukung.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat mengunduh uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).