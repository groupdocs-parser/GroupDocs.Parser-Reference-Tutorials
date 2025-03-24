---
title: Ekstrak Teks dari Halaman dalam PDF dalam Mode Mentah
linktitle: Ekstrak Teks dari Halaman dalam PDF dalam Mode Mentah
second_title: GroupDocs.Parser .NET API
description: Ekstrak teks dari PDF menggunakan GroupDocs.Parser di C#. Pelajari ekstraksi teks PDF yang efisien dengan perpustakaan .NET yang kuat ini.
weight: 16
url: /id/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# Ekstrak Teks dari Halaman dalam PDF dalam Mode Mentah

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari halaman dalam dokumen PDF menggunakan mode mentah. GroupDocs.Parser adalah alat canggih yang memungkinkan pengembang bekerja dengan berbagai format dokumen secara terprogram.
## Prasyarat
Sebelum memulai tutorial ini, pastikan Anda memiliki hal berikut:
- Visual Studio diinstal pada mesin Anda.
- Pengetahuan dasar tentang pemrograman C#.
- GroupDocs.Parser untuk perpustakaan .NET, yang Anda bisa[Unduh disini](https://releases.groupdocs.com/parser/net/).
- Contoh file PDF untuk tujuan pengujian.

## Impor Namespace
Pertama, pastikan untuk mengimpor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Untuk memulai, buat instance`Parser`kelas dengan memberikan jalur ke contoh file PDF Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode Anda ada di sini
}
```
## Langkah 2: Dapatkan Info Dokumen dan Ulangi Halaman
Selanjutnya, ambil informasi dokumen dan ulangi setiap halaman untuk mengekstrak teks.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Kode Anda untuk ekstraksi teks ada di sini
}
```
## Langkah 3: Ekstrak Teks dari Setiap Halaman
 Di dalam loop, gunakan`GetText` metode untuk mengekstrak teks dari setiap halaman dan mencetaknya.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Kesimpulan
 Dalam tutorial ini, kita telah mempelajari cara mengekstrak teks dari halaman PDF dalam mode mentah menggunakan GroupDocs.Parser untuk .NET. Proses ini melibatkan pembuatan a`Parser` Misalnya, memperoleh informasi dokumen, mengulangi setiap halaman, dan mengekstraksi teks menggunakan`GetText` metode.

## FAQ
### Apa itu GroupDocs.Parser untuk .NET?
GroupDocs.Parser untuk .NET adalah API penguraian dokumen yang memungkinkan pengembang mengekstrak teks, metadata, dan informasi lainnya dari berbagai format file secara terprogram.
### Bagaimana cara mengunduh GroupDocs.Parser untuk .NET?
 Anda dapat mengunduh perpustakaan dari[Situs web GroupDocs](https://releases.groupdocs.com/parser/net/).
### Apakah ada uji coba gratis yang tersedia?
 Ya, Anda dapat mengakses uji coba gratis GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dukungan untuk GroupDocs.Parser untuk .NET?
 Untuk bantuan teknis dan dukungan komunitas, kunjungi[Forum Grup Dokumen](https://forum.groupdocs.com/c/parser/17).
### Bagaimana cara membeli lisensi GroupDocs.Parser untuk .NET?
 Anda dapat membeli lisensi dari[halaman pembelian](https://purchase.groupdocs.com/buy) atau memperoleh lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).