---
title: Bekerja dengan Bidang pada Posisi Tetap di Templat
linktitle: Bekerja dengan Bidang pada Posisi Tetap di Templat
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak data dari dokumen menggunakan GroupDocs.Parser untuk .NET. Tutorial komprehensif dengan contoh kode.
weight: 11
url: /id/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---

# Bekerja dengan Bidang pada Posisi Tetap di Templat

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara bekerja dengan bidang pada posisi tetap dalam templat menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah pustaka penguraian dokumen canggih yang memungkinkan pengembang mengekstrak data dari berbagai format dokumen seperti PDF, Word, Excel, dan banyak lagi. Secara khusus, kami akan fokus pada pendefinisian dan pemanfaatan bidang templat untuk mengekstrak informasi yang ditargetkan berdasarkan posisi tetapnya.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Pemahaman dasar tentang pengembangan C# dan .NET.
- Visual Studio diinstal pada sistem Anda.
- GroupDocs.Parser untuk perpustakaan .NET diinstal. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Contoh file dokumen untuk pengujian.

## Impor Namespace
Mulailah dengan memasukkan namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Langkah 1: Tentukan Bidang Templat
Pertama, tentukan bidang dengan posisi tetap dalam templat. Bidang ini mewakili area dari mana data akan diambil.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Di Sini:
- `Rectangle` menentukan posisi dan ukuran lapangan.
- `Point(35, 135)` mewakili koordinat sudut kiri atas.
- `Size(100, 10)` mendefinisikan lebar dan tinggi lapangan.
- `"FromCompany"` adalah nama yang diberikan untuk bidang ini.
## Langkah 2: Buat Templat
Buat templat menggunakan bidang yang ditentukan.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 Itu`Template` objek memegang bidang yang ditentukan.
## Langkah 3: Parsing Dokumen Menggunakan Templat
 Buat instance`Parser` kelas dengan jalur dokumen target dan kemudian parsing dokumen menggunakan templat yang dibuat.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Iterasi melalui data yang diekstraksi
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Di Sini:
- `Parser` diinisialisasi dengan jalur file dokumen sampel.
- `ParseByTemplate` Metode ini digunakan untuk mengekstrak data berdasarkan template yang disediakan.
-  Data yang diekstraksi diakses menggunakan`DocumentData`di mana setiap item berhubungan dengan bidang yang ditentukan.

## Kesimpulan
Dalam tutorial ini, kami membahas proses bekerja dengan bidang pada posisi tetap di templat menggunakan GroupDocs.Parser untuk .NET. Dengan menentukan templat dengan posisi bidang tertentu, pengembang dapat secara akurat mengekstrak data yang ditargetkan dari berbagai format dokumen.

## FAQ
### Apakah GroupDocs.Parser kompatibel dengan semua format dokumen?
 GroupDocs.Parser mendukung berbagai format file, termasuk PDF, Microsoft Word, Excel, PowerPoint, dan banyak lagi. Mengacu kepada[dokumentasi](https://tutorials.groupdocs.com/parser/net/) untuk daftar rinci.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda bisa mendapatkan lisensi sementara untuk tujuan pengujian dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya dapat menemukan dukungan untuk GroupDocs.Parser?
 Untuk bantuan teknis dan diskusi, kunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Bisakah saya mencoba GroupDocs.Parser sebelum membeli?
 Ya, Anda dapat menjelajahi perpustakaan dengan tersedia uji coba gratis[Di Sini](https://releases.groupdocs.com/).
### Bagaimana cara membeli lisensi untuk GroupDocs.Parser?
 Untuk membeli lisensi, kunjungi[halaman pembelian](https://purchase.groupdocs.com/buy).