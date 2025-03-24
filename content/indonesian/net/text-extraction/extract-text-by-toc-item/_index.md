---
title: Ekstrak Teks berdasarkan Item Daftar Isi (TOC).
linktitle: Ekstrak Teks berdasarkan Item Daftar Isi (TOC).
second_title: GroupDocs.Parser .NET API
description: Ekstrak teks berdasarkan Daftar Isi (TOC) menggunakan GroupDocs.Parser untuk .NET. Pelajari teknik penguraian dokumen yang efisien untuk ekstraksi data terstruktur.
weight: 15
url: /id/net/text-extraction/extract-text-by-toc-item/
---

# Ekstrak Teks berdasarkan Item Daftar Isi (TOC).

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara memanfaatkan GroupDocs.Parser untuk .NET untuk mengekstrak teks berdasarkan item Daftar Isi (TOC) dari dokumen. GroupDocs.Parser adalah alat canggih yang memungkinkan penguraian dan ekstraksi dokumen secara efisien.
## Prasyarat
Sebelum melanjutkan tutorial ini, pastikan Anda memiliki prasyarat berikut:
1. Visual Studio: Instal Visual Studio IDE di sistem Anda.
2.  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/parser/net/).
3. Contoh Dokumen dengan TOC: Siapkan dokumen (misalnya PDF, DOCX) yang berisi Daftar Isi.

## Mengimpor Namespace
Pertama, sertakan namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Langkah 1: Buat Instance Kelas Parser
 Buat instance`Parser` kelas dengan jalur ke dokumen sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // Lanjutkan dengan langkah selanjutnya di sini...
}
```
## Langkah 2: Ekstrak Daftar Isi (TOC)
Dapatkan item Daftar Isi (TOC) dari dokumen:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## Langkah 3: Ulangi Item TOC dan Ekstrak Teks
Ulangi setiap item TOC dan ekstrak teks yang sesuai:
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Kesimpulan
Tutorial ini telah menunjukkan cara mengekstrak teks dari dokumen berdasarkan item Daftar Isi (TOC) menggunakan GroupDocs.Parser untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan, Anda dapat secara efisien mengurai dan mengekstrak konten tertentu dari dokumen Anda secara terprogram.

## FAQ
### Format file apa yang didukung GroupDocs.Parser?
GroupDocs.Parser mendukung berbagai format dokumen, termasuk PDF, Microsoft Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), dan banyak lagi.
### Bisakah saya mengekstrak data terstruktur seperti tabel atau gambar menggunakan GroupDocs.Parser?
Ya, GroupDocs.Parser menyediakan API untuk mengekstrak data terstruktur seperti tabel, gambar, dan metadata dari berbagai jenis dokumen.
### Apakah GroupDocs.Parser cocok untuk dokumen berukuran besar?
GroupDocs.Parser dioptimalkan untuk menangani dokumen besar secara efisien, memungkinkan ekstraksi konten tanpa hambatan dari file besar.
### Bagaimana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Parser?
 Anda dapat mencari dukungan teknis dan berinteraksi dengan komunitas di[GroupDocs.Forum Parser](https://forum.groupdocs.com/c/parser/17).
### Apakah GroupDocs menawarkan uji coba gratis untuk evaluasi?
Ya, Anda dapat mengunduh GroupDocs.Parser versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).