---
title: Ekstrak Teks dari Dokumen Word sebagai HTML
linktitle: Ekstrak Teks dari Dokumen Word sebagai HTML
second_title: GroupDocs.Parser .NET API
description: Pelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari dokumen Word dan menyimpannya sebagai HTML. Tutorial langkah demi langkah dengan contoh kode.
weight: 16
url: /id/net/word-document-processing/extract-text-from-word-document-as-html/
---

# Ekstrak Teks dari Dokumen Word sebagai HTML

## Perkenalan
GroupDocs.Parser untuk .NET adalah pustaka penguraian dokumen canggih yang memungkinkan pengembang mengekstrak teks dan metadata dari berbagai format file dengan mulus. Dalam tutorial ini, kita akan fokus memanfaatkan GroupDocs.Parser untuk mengekstrak teks dari dokumen Word dan menyimpannya sebagai HTML. Proses ini penting untuk tugas-tugas seperti analisis konten, pengindeksan, atau mengonversi dokumen ke format ramah web. Di akhir panduan ini, Anda akan memiliki pemahaman yang jelas tentang cara menggunakan GroupDocs.Parser secara efisien di aplikasi .NET Anda.
## Prasyarat
Sebelum mendalami tutorial ini, pastikan Anda memiliki prasyarat berikut:
- Pengetahuan dasar tentang pemrograman C#.
- Visual Studio diinstal pada mesin pengembangan Anda.
-  GroupDocs.Parser untuk perpustakaan .NET. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Akses ke contoh dokumen Word untuk tujuan pengujian.
## Impor Namespace
Untuk memulai, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Ikuti langkah-langkah mendetail berikut untuk mengekstrak teks dari dokumen Word dan menyimpannya sebagai HTML menggunakan GroupDocs.Parser untuk .NET:
## Langkah 1: Buat Instance Kelas Parser
 Pertama, buat sebuah instance dari`Parser` kelas dengan menyediakan jalur ke contoh dokumen Word Anda:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Lanjutkan ke Langkah 2...
}
```
 Mengganti`"YourSampleFile.docx"`dengan jalur ke dokumen Word Anda.
## Langkah 2: Ekstrak Teks Terformat sebagai HTML
 Selanjutnya, gunakan`GetFormattedText` metode bersama dengan`FormattedTextOptions`untuk mengekstrak teks dalam format HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ekstrak teks yang diformat ke pembaca
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Lanjutkan ke Langkah 3...
    }
}
```
## Langkah 3: Baca dan Keluarkan HTML yang Diekstraksi
 Terakhir, baca konten HTML yang diekstrak dari`TextReader` dan mencetaknya ke konsol:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ekstrak teks yang diformat ke pembaca
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Cetak teks yang diformat sebagai HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Kesimpulan
Dalam tutorial ini, kita telah menjelajahi cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari dokumen Word dan menyimpannya sebagai HTML. Pustaka ini menawarkan cara yang mudah dan efisien untuk mengurai konten dokumen, menjadikannya alat yang sangat berharga untuk tugas pemrosesan dokumen dalam aplikasi .NET.

## FAQ
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat meminta lisensi sementara dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya dapat menemukan lebih banyak dokumentasi untuk GroupDocs.Parser?
 Dokumentasi terperinci tersedia[Di Sini](https://tutorials.groupdocs.com/parser/net/).
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat mengakses versi uji coba gratis[Di Sini](https://releases.groupdocs.com/).
### Bagaimana cara mendapatkan dukungan untuk GroupDocs.Parser?
 Kunjungi forum dukungan[Di Sini](https://forum.groupdocs.com/c/parser/17).
### Jenis dokumen apa yang didukung GroupDocs.Parser?
GroupDocs.Parser mendukung berbagai format dokumen termasuk Word, PDF, Excel, PowerPoint, dan banyak lagi.