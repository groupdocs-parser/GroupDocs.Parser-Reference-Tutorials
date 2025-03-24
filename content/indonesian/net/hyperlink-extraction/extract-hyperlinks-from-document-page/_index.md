---
title: Ekstrak Hyperlink dari Halaman Dokumen
linktitle: Ekstrak Hyperlink dari Halaman Dokumen
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak hyperlink dari dokumen menggunakan GroupDocs.Parser untuk .NET. Panduan langkah demi langkah untuk ekstraksi hyperlink di C#.
weight: 11
url: /id/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---

# Ekstrak Hyperlink dari Halaman Dokumen

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak hyperlink dari dokumen langkah demi langkah. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengurai berbagai format dokumen dan mengekstrak teks, metadata, dan elemen lainnya.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Visual Studio: Instal Visual Studio di mesin pengembangan Anda.
-  Perpustakaan GroupDocs.Parser: Unduh dan rujuk perpustakaan GroupDocs.Parser. Anda bisa mendapatkannya dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Contoh Dokumen: Siapkan contoh dokumen (misalnya DOCX, PDF) yang berisi hyperlink untuk pengujian.

## Impor Namespace
Pertama, sertakan namespace yang diperlukan untuk menggunakan fungsi GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instans Parser
 Buat instance`Parser` kelas dengan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode ada di sini...
}
```
## Langkah 2: Periksa Dukungan Ekstraksi Hyperlink
Pastikan dokumen mendukung ekstraksi hyperlink sebelum melanjutkan.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Langkah 3: Ambil Informasi Dokumen
Dapatkan informasi dasar tentang dokumen dan periksa apakah dokumen tersebut berisi halaman.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Langkah 4: Ulangi Halaman Dokumen
Ulangi setiap halaman dokumen.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Ekstrak hyperlink dari halaman saat ini
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Ulangi hyperlink yang diekstraksi
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Baris kosong agar mudah dibaca
    }
}
```

## Kesimpulan
Dalam tutorial ini, kami telah membahas dasar-dasar penggunaan GroupDocs.Parser untuk .NET untuk mengekstrak hyperlink dari dokumen. Anda mempelajari cara menginisialisasi parser, memeriksa dukungan hyperlink, mengambil informasi dokumen, dan melakukan iterasi melalui halaman dokumen untuk mengekstrak hyperlink secara efisien.

## FAQ
### Bisakah saya mengekstrak hyperlink dari format dokumen berbeda?
Ya, GroupDocs.Parser mendukung berbagai format seperti DOCX, PDF, PPTX, dll., untuk ekstraksi hyperlink.
### Apakah GroupDocs.Parser mudah diintegrasikan ke dalam aplikasi .NET yang ada?
Tentu saja, GroupDocs.Parser dirancang agar mudah dan dapat dengan mudah diintegrasikan ke dalam proyek .NET Anda.
### Bisakah saya mengekstrak metadata lain beserta hyperlink menggunakan GroupDocs.Parser?
Ya, selain hyperlink, Anda dapat mengekstrak teks, gambar, dan metadata dari dokumen menggunakan perpustakaan ini.
### Apakah GroupDocs.Parser menangani dokumen terenkripsi atau dilindungi kata sandi?
GroupDocs.Parser dapat mengurai dokumen yang dilindungi kata sandi jika kata sandi diberikan.
### Apakah ada versi uji coba yang tersedia untuk diuji sebelum membeli?
 Ya, Anda dapat mengunduh versi uji coba gratis[Di Sini](https://releases.groupdocs.com/).