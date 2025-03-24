---
title: Ekstrak Tabel dari Halaman Dokumen
linktitle: Ekstrak Tabel dari Halaman Dokumen
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak tabel dari dokumen secara terprogram menggunakan GroupDocs.Parser untuk .NET. Tutorial komprehensif ini memberikan panduan langkah demi langkah.
weight: 11
url: /id/net/table-extraction/extract-tables-from-document-page/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara mengekstrak tabel dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang bekerja dengan berbagai format dokumen seperti PDF, DOCX, XLSX, dan banyak lagi. Dengan memanfaatkan fitur-fiturnya, kami dapat secara efisien mengekstrak data terstruktur seperti tabel dari dokumen-dokumen ini, sehingga memungkinkan kami memanipulasi dan menganalisis informasi secara terprogram.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
- Visual Studio diinstal pada mesin Anda.
- Pemahaman dasar tentang pengembangan C# dan .NET.
-  GroupDocs.Parser untuk perpustakaan .NET. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Akses ke contoh dokumen (PDF, DOCX, dll.) yang berisi tabel untuk ekstraksi.

## Impor Namespace
Pertama, mulailah dengan mengimpor namespace yang diperlukan dalam proyek C# Anda:
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
 Buat instance`Parser` kelas dengan memberikan jalur ke dokumen sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Kode Anda berlanjut di sini...
}
```
## Langkah 2: Periksa Dukungan Ekstraksi Tabel Dokumen
Sebelum melanjutkan, verifikasi apakah dokumen mendukung ekstraksi tabel:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Langkah 3: Tentukan Tata Letak Tabel
Tentukan tata letak tabel yang akan diekstraksi dari dokumen. Tentukan lebar kolom dan tinggi baris sesuai struktur dokumen Anda:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Lebar kolom
    new double[] { 325, 340, 365, 395 });         // Ketinggian baris
```
## Langkah 4: Konfigurasikan Opsi Ekstraksi Tabel
Buat opsi untuk ekstraksi tabel menggunakan tata letak yang ditentukan:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Langkah 5: Ambil Informasi Dokumen
Ambil informasi tentang dokumen, termasuk jumlah halaman:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Langkah 6: Ulangi Halaman Dokumen
Ulangi setiap halaman dokumen untuk mengekstrak tabel:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Ekstrak tabel dari halaman saat ini
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Ulangi tabel yang diekstraksi
    foreach (PageTableArea table in tables)
    {
        // Ulangi baris tabel
        for (int row = 0; row < table.RowCount; row++)
        {
            // Ulangi kolom tabel
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Dapatkan sel tabel
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Cetak teks sel tabel
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Kesimpulan
Dalam tutorial ini, kami membahas proses mengekstraksi tabel dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. Dengan mengikuti langkah-langkah yang disediakan, Anda dapat dengan mudah mengintegrasikan fungsionalitas ekstraksi tabel ke dalam aplikasi .NET Anda, memungkinkan penanganan dan manipulasi data terstruktur dalam dokumen secara efisien.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak tabel dari semua jenis dokumen?
GroupDocs.Parser mendukung berbagai format dokumen seperti PDF, DOCX, XLSX, dan lainnya, memungkinkan ekstraksi tabel dari jenis file yang kompatibel.
### Apakah GroupDocs.Parser untuk .NET cocok untuk pemrosesan dokumen skala besar?
Ya, GroupDocs.Parser dirancang untuk menangani dokumen besar secara efisien, sehingga cocok untuk memproses kumpulan data yang luas.
### Apakah GroupDocs.Parser mempertahankan pemformatan selama ekstraksi tabel?
Ya, GroupDocs.Parser mempertahankan detail pemformatan seperti batas sel, gaya teks, dan perataan selama ekstraksi tabel.
### Bisakah saya mengekstrak tabel tertentu berdasarkan kriteria konten?
GroupDocs.Parser menawarkan opsi fleksibel untuk menargetkan tabel tertentu berdasarkan templat tata letak atau kondisi konten untuk ekstraksi.
### Apakah GroupDocs.Parser kompatibel dengan .NET Core?
Ya, GroupDocs.Parser kompatibel dengan lingkungan .NET Framework dan .NET Core.