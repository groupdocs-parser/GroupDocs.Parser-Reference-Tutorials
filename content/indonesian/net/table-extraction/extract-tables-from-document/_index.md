---
title: Ekstrak Tabel dari Dokumen
linktitle: Ekstrak Tabel dari Dokumen
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak tabel dari dokumen menggunakan Groupdocs.Parser untuk .NET. Ikuti panduan terperinci tentang cara mengintegrasikan fungsi ini.
weight: 10
url: /id/net/table-extraction/extract-tables-from-document/
---

# Ekstrak Tabel dari Dokumen

## Perkenalan
Groupdocs.Parser untuk .NET adalah perpustakaan komprehensif yang memfasilitasi penguraian dokumen, memungkinkan Anda mengekstrak informasi berharga seperti tabel, teks, metadata, dan lainnya dari dokumen. Dalam tutorial ini, kami fokus secara khusus pada mengekstraksi tabel dari dokumen menggunakan Groupdocs.Parser API.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Visual Studio diinstal pada sistem Anda.
- .NET Framework atau .NET Core diinstal.
- Pengetahuan dasar tentang pemrograman C#.

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan untuk mengakses kelas dan metode Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Langkah 1: Buat Instance Kelas Parser
 Inisialisasi instance baru dari`Parser` kelas dengan menyediakan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode Anda ada di sini
}
```
## Langkah 2: Periksa Dukungan Ekstraksi Tabel
 Verifikasi apakah dokumen mendukung ekstraksi tabel menggunakan`Features` properti dari`Parser` kelas.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Langkah 3: Tentukan Tata Letak Tabel
Tentukan tata letak tabel yang ingin Anda ekstrak menggunakan`TemplateTableLayout`. Tentukan lebar kolom dan tinggi baris berdasarkan struktur dokumen Anda.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Langkah 4: Tetapkan Opsi Ekstraksi Tabel
 Membuat`PageTableAreaOptions` dengan tata letak yang ditentukan untuk menentukan bagaimana tabel harus diekstraksi.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Langkah 5: Ekstrak Tabel
 Memanfaatkan`GetTables` metode`Parser` kelas untuk mengekstrak tabel dari dokumen berdasarkan opsi yang ditentukan.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Langkah 6: Iterasi dan Akses Data Tabel
Ulangi tabel yang diekstraksi serta baris dan kolomnya masing-masing untuk mengakses data sel.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Kesimpulan
Dalam tutorial ini, kami telah membahas cara menggunakan Groupdocs.Parser untuk .NET untuk mengekstrak tabel dari dokumen secara efisien. Memanfaatkan kemampuan perpustakaan ini, Anda dapat mengintegrasikan ekstraksi tabel ke dalam aplikasi .NET Anda dengan lancar.

## FAQ
### Bisakah Groupdocs.Parser menangani format dokumen yang berbeda?
Ya, Groupdocs.Parser mendukung berbagai format dokumen termasuk DOCX, PDF, XLSX, dan banyak lagi.
### Apakah ada versi uji coba yang tersedia untuk Groupdocs.Parser untuk .NET?
 Ya, Anda dapat mengunduh uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk pertanyaan terkait Groupdocs.Parser?
 Anda dapat mengunjungi[Forum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) untuk bantuan.
### Di mana saya dapat membeli lisensi untuk Groupdocs.Parser?
 Anda dapat membeli lisensi dari[Di Sini](https://purchase.groupdocs.com/buy).
### Bagaimana saya bisa mendapatkan izin sementara untuk tujuan evaluasi?
 Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).