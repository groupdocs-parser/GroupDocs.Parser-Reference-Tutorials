---
title: Bekerja dengan Tabel dalam Data yang Diekstraksi
linktitle: Bekerja dengan Tabel dalam Data yang Diekstraksi
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak data tabel dari dokumen menggunakan GroupDocs.Parser untuk .NET. Parsing konten terstruktur secara efisien dengan templat yang telah ditentukan sebelumnya.
type: docs
weight: 12
url: /id/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak data dari tabel di dokumen. GroupDocs.Parser adalah alat canggih yang memungkinkan pengembang mengurai dan mengekstrak teks, metadata, dan konten terstruktur dari berbagai format file seperti PDF, DOCX, XLSX, dan banyak lagi. Secara khusus, kami akan fokus pada mengekstraksi data tabel secara efisien menggunakan templat yang telah ditentukan sebelumnya.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
- Visual Studio diinstal pada mesin Anda.
- Pemahaman dasar tentang kerangka C# dan .NET.
- Pustaka GroupDocs.Parser diinstal melalui manajer paket NuGet.

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan untuk bekerja dengan GroupDocs.Parser dan fungsi terkait.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Langkah 1: Buat Templat Tabel
Untuk mengekstrak data dari tabel, pertama-tama tentukan templat yang mewakili struktur tabel yang ingin Anda ekstrak. Tentukan lokasi dan dimensi tabel dalam dokumen.
```csharp
// Tentukan parameter tabel (lokasi dan ukuran)
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// Buat templat tabel dengan parameter
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## Langkah 2: Tentukan Templat
Buat templat yang menyertakan templat tabel yang Anda tentukan. Templat ini akan memandu parser tentang apa yang harus dicari saat mengekstraksi data tabel.
```csharp
// Buat templat dengan tabel
Template template = new Template(new TemplateItem[] { table });
```
## Langkah 3: Parsing Dokumen dan Ekstrak Data Tabel
Manfaatkan kelas Parser dari GroupDocs.Parser untuk mengurai dokumen tertentu menggunakan templat yang Anda tentukan.
```csharp
// Tentukan jalur ke file sampel Anda
string filePath = "YourSampleFile.pdf";
// Buat instance kelas Parser
using (Parser parser = new Parser(filePath))
{
    // Parsing dokumen berdasarkan templat
    DocumentData data = parser.ParseByTemplate(template);
    // Ulangi semua data yang diekstraksi
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // Periksa apakah bidang yang diekstraksi adalah tabel
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // Ulangi baris tabel
        for (int row = 0; row < area.RowCount; row++)
        {
            // Ulangi kolom tabel
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // Dapatkan nilai sel
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // Cetak nilai sel (atau string kosong jika nol)
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // Cetak ruang tab antar kolom
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            // Pindah ke baris berikutnya setelah mencetak setiap baris
            Console.WriteLine();
        }
    }
}
```

## Kesimpulan
Dalam tutorial ini, kita telah menjelajahi cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak data tabel dari dokumen. Dengan menentukan template dan memanfaatkan metode parsing, pengembang dapat secara efisien mengekstrak data terstruktur seperti tabel dari berbagai format file.

## FAQ
### Apakah GroupDocs.Parser kompatibel dengan semua format dokumen?
Ya, GroupDocs.Parser mendukung berbagai format file termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### Bisakah saya mengekstrak data dari wilayah tertentu dalam dokumen?
Tentu saja, Anda dapat menentukan templat yang menargetkan area tertentu (seperti tabel) dalam dokumen untuk diekstraksi.
### Apakah GroupDocs.Parser cocok untuk dokumen berukuran besar?
Ya, GroupDocs.Parser dioptimalkan untuk menangani dokumen besar secara efisien, memungkinkan pengembang mengekstrak data dengan lancar.
### Apakah GroupDocs.Parser mendukung ekstraksi teks bersama dengan data terstruktur?
Ya, selain ekstraksi data terstruktur (seperti tabel), GroupDocs.Parser dapat mengekstrak teks biasa dan metadata dari dokumen.
### Bagaimana saya bisa mendapatkan dukungan atau bantuan dengan integrasi GroupDocs.Parser?
 Untuk dukungan dan diskusi, kunjungi forum komunitas GroupDocs[Di Sini](https://forum.groupdocs.com/c/parser/17).