---
title: Ekstrak Gambar ke File
linktitle: Ekstrak Gambar ke File
second_title: GroupDocs.Parser .NET API
description: Ekstrak gambar dengan mudah dari berbagai jenis dokumen seperti PDF dan DOCX menggunakan GroupDocs.Parser untuk .NET. Sederhanakan tugas penguraian dokumen Anda.
type: docs
weight: 13
url: /id/net/image-extraction/extract-images-to-files/
---
## Perkenalan
Dalam tutorial ini, Anda akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak gambar dari berbagai format dokumen seperti PDF, Word, Excel, dan PowerPoint. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengurai dan mengekstrak teks, metadata, gambar, dan lainnya dari dokumen dengan cara yang mudah. Panduan ini akan memandu Anda melalui proses mengekstraksi gambar dan menyimpannya sebagai file individual menggunakan C#.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki prasyarat berikut:
1. Visual Studio: Pastikan Anda telah menginstal Visual Studio di sistem Anda.
2.  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/parser/net/).
3. Contoh Dokumen: Siapkan contoh dokumen (misalnya PDF, DOCX, XLSX) yang gambarnya ingin Anda ekstrak.

## Impor Namespace
Pertama, sertakan namespace yang diperlukan dalam kode C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instans Parser
 Buat instance`Parser` kelas dengan menyediakan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode ada di sini
}
```
## Langkah 2: Ekstrak Gambar dari Dokumen
 Menggunakan`GetImages()` metode`Parser` objek untuk mengambil gambar dari dokumen.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Langkah 3: Periksa Dukungan untuk Ekstraksi Gambar
Verifikasi apakah dokumen mendukung ekstraksi gambar.
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## Langkah 4: Tetapkan Opsi Penyimpanan Gambar
Tentukan formatnya (`ImageFormat`) tempat Anda ingin menyimpan gambar yang diekstraksi (misalnya PNG).
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Langkah 5: Ulangi dan Simpan Gambar
Ulangi gambar yang diekstraksi dan simpan setiap gambar ke file.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Simpan gambar ke file PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```

## Kesimpulan
Dalam tutorial ini, Anda telah mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak gambar dari dokumen menggunakan C#. Pustaka yang kuat ini menyederhanakan proses penguraian dan mengekstraksi data dari berbagai format file, menjadikannya alat penting untuk tugas pemrosesan dokumen dalam aplikasi .NET.

## FAQ
### Bisakah saya mengekstrak gambar dari dokumen yang dilindungi kata sandi?
Ya, GroupDocs.Parser mendukung ekstraksi gambar dari dokumen yang dilindungi kata sandi jika Anda memberikan kata sandi yang benar selama penguraian.
### Format dokumen apa yang didukung untuk ekstraksi gambar?
GroupDocs.Parser mendukung berbagai format termasuk PDF, DOCX, XLSX, PPTX, EPUB, dan banyak lagi.
### Bagaimana cara menangani pengecualian selama ekstraksi gambar?
Anda dapat menerapkan penanganan kesalahan dalam kode Anda untuk menangkap dan mengelola pengecualian yang mungkin terjadi selama ekstraksi gambar.
### Apakah GroupDocs.Parser cocok untuk pemrosesan dokumen secara batch?
Ya, Anda dapat menggunakan GroupDocs.Parser untuk memproses banyak dokumen dalam satu batch, mengekstraksi gambar dan data lainnya secara efisien.
### Apakah GroupDocs.Parser menyediakan kemampuan OCR untuk dokumen yang dipindai?
GroupDocs.Parser saat ini tidak mendukung OCR (Optical Character Recognition) tetapi unggul dalam penguraian data terstruktur dari dokumen.