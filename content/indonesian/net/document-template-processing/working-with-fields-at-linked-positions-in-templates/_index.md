---
title: Bekerja dengan Bidang pada Posisi Tertaut di Templat
linktitle: Bekerja dengan Bidang pada Posisi Tertaut di Templat
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak data secara efisien dari dokumen menggunakan GroupDocs.Parser untuk .NET. Tutorial langkah demi langkah dengan contoh kode.
weight: 12
url: /id/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
type: docs
---
# Bekerja dengan Bidang pada Posisi Tertaut di Templat

## Perkenalan
GroupDocs.Parser untuk .NET adalah perpustakaan tangguh yang dirancang untuk memfasilitasi tugas penguraian dokumen dan ekstraksi data. Ini mendukung berbagai format file, termasuk PDF, DOCX, XLSX, dan banyak lagi. Salah satu fitur utamanya adalah ekstraksi data berbasis templat, yang memungkinkan Anda menentukan bidang dalam dokumen dan mengekstrak data tertentu berdasarkan templat yang telah ditentukan sebelumnya.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Pemahaman dasar pemrograman C#
- Visual Studio diinstal pada sistem Anda
-  GroupDocs.Parser untuk perpustakaan .NET (unduh dari[Di Sini](https://releases.groupdocs.com/parser/net/))
- Contoh file dokumen untuk dikerjakan

## Mengimpor Namespace
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
Pertama, tentukan bidang templat menggunakan ekspresi reguler dan posisi tertaut:
```csharp
// Tentukan bidang dengan ekspresi reguler
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Tentukan bidang tertaut dengan pengaturan posisi tertentu
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Langkah 2: Buat Templat
Selanjutnya, buat templat yang berisi bidang yang ditentukan:
```csharp
// Buat templat dengan bidang yang ditentukan
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Langkah 3: Parsing Dokumen dengan Templat
 Sekarang, inisialisasi`Parser` kelas dan parsing dokumen menggunakan templat:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Parsing dokumen berdasarkan templat
    DocumentData data = parser.ParseByTemplate(template);
    // Iterasi melalui data yang diekstraksi dan hasil cetak
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Kesimpulan
GroupDocs.Parser untuk .NET menyederhanakan proses mengekstraksi data terstruktur dari dokumen menggunakan templat. Dengan menentukan bidang dan menerapkan templat, Anda dapat mengekstrak informasi relevan secara efisien, meningkatkan otomatisasi dan produktivitas dalam tugas pemrosesan dokumen.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak data dari file PDF terenkripsi?
Ya, GroupDocs.Parser mendukung penguraian file PDF terenkripsi dengan memberikan kata sandi selama penguraian.
### Format file apa yang didukung untuk ekstraksi berbasis templat?
GroupDocs.Parser mendukung berbagai format file termasuk PDF, DOCX, XLSX, PPTX, TXT, dan banyak lagi.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bisakah saya menggunakan GroupDocs.Parser untuk pemrosesan dokumen secara batch?
Ya, GroupDocs.Parser memungkinkan pemrosesan batch untuk mengurai beberapa dokumen secara bersamaan.
### Di mana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Parser?
 Anda dapat mencari dukungan teknis dan terlibat dengan komunitas di[Forum Grup Dokumen](https://forum.groupdocs.com/c/parser/17).