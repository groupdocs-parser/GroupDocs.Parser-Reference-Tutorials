---
title: Ekstrak Teks Terformat dari Halaman Dokumen
linktitle: Ekstrak Teks Terformat dari Halaman Dokumen
second_title: GroupDocs.Parser .NET API
description: Ekstrak teks yang diformat dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. Solusi ekstraksi teks yang efisien dan andal.
type: docs
weight: 11
url: /id/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses mengekstraksi teks yang diformat dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. Pustaka ini memungkinkan Anda mengurai dan mengekstrak teks secara efisien dari berbagai format dokumen seperti PDF, Word, Excel, dan lainnya.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Visual Studio diinstal pada sistem Anda.
- Pengetahuan dasar tentang pemrograman C#.
-  GroupDocs.Parser untuk perpustakaan .NET. Anda dapat mengunduhnya[Di Sini](https://releases.groupdocs.com/parser/net/).

## Impor Namespace
Pertama, mulailah dengan mengimpor namespace yang diperlukan ke proyek C# Anda.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Mulailah dengan membuat sebuah instance dari`Parser` kelas dengan menyediakan jalur ke file sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode akan ditempatkan di sini
}
```
## Langkah 2: Periksa apakah Ekstraksi Teks Terformat Didukung
Sebelum melanjutkan ekstraksi teks, verifikasi apakah dokumen mendukung ekstraksi teks berformat.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Langkah 3: Dapatkan Informasi Dokumen
Ambil informasi tentang dokumen, seperti jumlah halaman.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Langkah 4: Ulangi Halaman Dokumen dan Ekstrak Teks yang Diformat
Ulangi setiap halaman dokumen dan ekstrak teks yang diformat menggunakan opsi tertentu (misalnya, format penurunan harga).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Kesimpulan
Sekarang Anda tahu cara mengekstrak teks yang diformat dari halaman dokumen menggunakan GroupDocs.Parser untuk .NET. Pustaka ini menyediakan solusi yang kuat dan mudah digunakan untuk ekstraksi teks dari berbagai format file.

## FAQ
### Bisakah GroupDocs.Parser menangani format file yang berbeda?
Ya, GroupDocs.Parser mendukung berbagai format dokumen, termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### Apakah GroupDocs.Parser kompatibel dengan .NET Core?
Ya, GroupDocs.Parser mendukung .NET Core dan .NET Framework.
### Apakah GroupDocs.Parser mempertahankan format teks selama ekstraksi?
Ya, GroupDocs.Parser dapat mempertahankan pemformatan seperti gaya dan font saat mengekstraksi teks.
### Bisakah saya mengekstrak gambar dan metadata menggunakan GroupDocs.Parser?
Ya, GroupDocs.Parser memungkinkan ekstraksi gambar, metadata, dan teks dari dokumen.
### Bagaimana saya bisa mendapatkan dukungan untuk GroupDocs.Parser?
 Anda bisa mendapatkan dukungan dari[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).