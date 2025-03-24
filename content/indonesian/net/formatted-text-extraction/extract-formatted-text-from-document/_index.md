---
title: Ekstrak Teks Terformat dari Dokumen
linktitle: Ekstrak Teks Terformat dari Dokumen
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak teks yang diformat dari dokumen menggunakan GroupDocs.Parser untuk .NET. Ekstraksi teks sederhana dan efisien untuk aplikasi Anda.
weight: 10
url: /id/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks yang diformat dari berbagai jenis dokumen. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang bekerja dengan dokumen secara sederhana dan efisien. Di akhir panduan ini, Anda akan dapat mengintegrasikan kemampuan ekstraksi teks dengan lancar ke dalam aplikasi .NET Anda.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Visual Studio: Pastikan Anda telah menginstal Visual Studio di sistem Anda.
-  GroupDocs.Parser untuk .NET: Unduh dan instal perpustakaan GroupDocs.Parser dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Sampel Dokumen: Siapkan dokumen sampel (misalnya PDF, DOCX) untuk ekstraksi teks.
## Impor Namespace
Pertama, sertakan namespace yang diperlukan dalam kode C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Mulailah dengan inisialisasi a`Parser` objek dengan jalur ke dokumen sampel Anda.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode ekstraksi teks ada di sini
}
```
 Mengganti`"YourSampleFile.pdf"` dengan jalur ke file dokumen Anda.

## Langkah 2: Ekstrak Teks yang Diformat
 Dalam`using` blok, gunakan`GetFormattedText` metode untuk mengekstrak teks yang diformat dari dokumen. Tentukan format keluaran yang diinginkan (misalnya HTML) menggunakan`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ekstrak teks yang diformat ke pembaca
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Periksa apakah ekstraksi didukung
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Membaca dan menampilkan teks yang diekstraksi
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Kesimpulan
Selamat! Anda telah mempelajari cara mengekstrak teks yang diformat dari dokumen menggunakan GroupDocs.Parser untuk .NET. Pustaka serbaguna ini membuka kemungkinan untuk pemrosesan dan analisis teks dalam aplikasi Anda.

## FAQ
### T: Bisakah GroupDocs.Parser mengekstrak teks dari dokumen yang dilindungi kata sandi?
J: Ya, GroupDocs.Parser mendukung ekstraksi teks dari dokumen yang dilindungi kata sandi.
### T: Format dokumen apa saja yang didukung oleh GroupDocs.Parser?
J: GroupDocs.Parser mendukung berbagai format termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### T: Bagaimana cara mendapatkan lisensi sementara untuk GroupDocs.Parser?
 J: Anda dapat memperoleh lisensi sementara dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### T: Apakah GroupDocs.Parser menyediakan dukungan untuk ekstraksi gambar dari dokumen?
J: Ya, GroupDocs.Parser mendukung ekstraksi gambar bersamaan dengan ekstraksi teks.
### T: Di mana saya dapat menemukan dukungan tambahan atau mengajukan pertanyaan tentang GroupDocs.Parser?
 J: Kunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)untuk dukungan dan diskusi.