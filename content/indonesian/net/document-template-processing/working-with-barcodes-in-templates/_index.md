---
title: Bekerja dengan Barcode di Templat
linktitle: Bekerja dengan Barcode di Templat
second_title: GroupDocs.Parser .NET API
description: Pelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak data terstruktur dari dokumen menggunakan templat. Sederhanakan ekstraksi data dengan bidang barcode.
weight: 10
url: /id/net/document-template-processing/working-with-barcodes-in-templates/
---

# Bekerja dengan Barcode di Templat

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara mengekstrak data dari dokumen secara efisien menggunakan templat dengan GroupDocs.Parser untuk .NET. GroupDocs.Parser menyederhanakan proses ekstraksi data dengan memungkinkan Anda menentukan templat untuk tipe data tertentu, seperti kode batang, lalu mengurai dokumen sesuai dengan templat tersebut.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan yang berikut:
-  GroupDocs.Parser untuk .NET: Anda dapat mengunduh perpustakaan dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Contoh Dokumen: Siapkan file contoh (misalnya PDF, DOCX) yang berisi data yang ingin Anda ekstrak.

## Impor Namespace
Pertama, sertakan namespace yang diperlukan dalam kode C# Anda:
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
using System;
```
## Langkah 1: Tentukan Bidang Barcode
Tentukan bidang kode batang dalam templat. Contoh ini menyiapkan bidang kode QR:
```csharp
TemplateBarcode barcode = new TemplateBarcode(
    new Rectangle(new Point(590, 80), new Size(150, 150)),
    "QR");
```
 Di Sini,`Rectangle` mendefinisikan posisi dan ukuran bidang barcode pada dokumen.
## Langkah 2: Buat Templat
Buat templat dan tambahkan bidang kode batang ke dalamnya:
```csharp
Template template = new Template(new TemplateItem[] { barcode });
```
## Langkah 3: Parsing Dokumen Menggunakan Templat
 Buat instance`Parser` kelas dengan jalur file dokumen Anda dan parsing dokumen menggunakan templat yang ditentukan:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Cetak data yang diekstraksi
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageBarcodeArea area = data[i].PageArea as PageBarcodeArea;
        Console.WriteLine(area == null ? "Not a template barcode field" : area.Value);
    }
}
```
Cuplikan kode ini membuka dokumen, menerapkan templat, dan mengekstrak data berdasarkan bidang kode batang yang ditentukan. Kemudian mencetak data yang diekstraksi.

## Kesimpulan
Menggunakan GroupDocs.Parser untuk .NET dengan templat menyederhanakan ekstraksi data terstruktur dari dokumen, terutama saat menangani tipe data tertentu seperti kode batang. Dengan mengikuti panduan ini, Anda dapat secara efisien mengintegrasikan kemampuan penguraian dokumen ke dalam aplikasi .NET Anda.

## FAQ
### T: Bisakah saya mengekstrak beberapa kolom kode batang dari satu dokumen?
J: Ya, Anda dapat menentukan beberapa bidang kode batang dalam templat dan mengekstrak data terkait dari dokumen.
### T: Format dokumen apa yang didukung untuk penguraian?
J: GroupDocs.Parser mendukung berbagai format dokumen, termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### T: Apakah tersedia versi uji coba?
 J: Ya, Anda bisa mendapatkan uji coba gratis GroupDocs.Parser dari[Di Sini](https://releases.groupdocs.com/).
### T: Bagaimana saya bisa mendapatkan dukungan teknis?
 J: Untuk bantuan teknis, kunjungi[Forum Grup Dokumen](https://forum.groupdocs.com/c/parser/17).
### Q: Dimana saya bisa membeli lisensinya?
 J: Anda dapat membeli lisensi untuk GroupDocs.Parser dari[Di Sini](https://purchase.groupdocs.com/buy).