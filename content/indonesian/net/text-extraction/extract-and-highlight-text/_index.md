---
title: Ekstrak dan Sorot Teks
linktitle: Ekstrak dan Sorot Teks
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak dan menyorot teks dari dokumen menggunakan GroupDocs.Parser untuk .NET. Langkah mudah untuk ekstraksi teks yang efisien di proyek .NET Anda.
weight: 11
url: /id/net/text-extraction/extract-and-highlight-text/
---

# Ekstrak dan Sorot Teks

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak dan menyorot teks dari dokumen. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan Anda mengurai berbagai format dokumen dan melakukan operasi ekstraksi teks tingkat lanjut.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Visual Studio: Instal Visual Studio untuk pengembangan .NET.
-  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- File Contoh: Siapkan contoh dokumen untuk ekstraksi teks.

## Mengimpor Namespace
Pertama, mulailah dengan mengimpor namespace yang diperlukan ke dalam proyek Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instans Parser
 Buat instance`Parser` kelas dengan jalur file sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Tambahkan logika ekstraksi dan penyorotan di sini
}
```
## Langkah 2: Ekstrak dan Sorot Teks
 Sekarang, di dalam`using`blok, Anda dapat mengekstrak dan menyorot teks:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ekstrak highlight pada posisi 2 dengan maksimal 3 kata
    HighlightItem highlight = parser.GetHighlight(2, true, new HighlightOptions(3));
    // Periksa apakah ekstraksi sorotan didukung
    if (highlight == null)
    {
        Console.WriteLine("Highlight extraction isn't supported");
        return;
    }
    // Cetak sorotan yang diekstraksi
    Console.WriteLine($"At {highlight.Position}: {highlight.Text}");
}
```

## Kesimpulan
Dalam tutorial ini, kami telah membahas dasar-dasar penggunaan GroupDocs.Parser untuk .NET untuk mengekstrak dan menyorot teks dari dokumen. Anda dapat menjelajahi lebih lanjut kemampuan perpustakaan ini untuk melakukan tugas ekstraksi teks lebih lanjut.

### FAQ
### Apakah GroupDocs.Parser untuk .NET kompatibel dengan berbagai format dokumen?
Ya, GroupDocs.Parser mendukung berbagai format file termasuk DOCX, PDF, TXT, dan banyak lagi.
### Bisakah saya mengekstrak bagian atau elemen tertentu dari dokumen menggunakan GroupDocs.Parser?
Tentu saja, GroupDocs.Parser memungkinkan ekstraksi teks, gambar, tabel, dan metadata secara tepat.
### Apakah GroupDocs.Parser cocok untuk dokumen berukuran besar?
Ya, GroupDocs.Parser dioptimalkan untuk menangani dokumen besar secara efisien.
### Di mana saya bisa mendapatkan dukungan untuk pertanyaan terkait GroupDocs.Parser?
 Mengunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) untuk dukungan dan diskusi komunitas.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda bisa mendapatkan[izin sementara di sini](https://purchase.groupdocs.com/temporary-license/)untuk tujuan pengujian.