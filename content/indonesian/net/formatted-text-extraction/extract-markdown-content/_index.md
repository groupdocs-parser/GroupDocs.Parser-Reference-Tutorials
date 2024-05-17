---
title: Ekstrak Konten Penurunan Harga
linktitle: Ekstrak Konten Penurunan Harga
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak konten Markdown dari dokumen menggunakan GroupDocs.Parser untuk .NET. Tutorial ini memberikan petunjuk langkah demi langkah untuk ekstraksi teks yang lancar.
type: docs
weight: 13
url: /id/net/formatted-text-extraction/extract-markdown-content/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak konten Markdown dari dokumen. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengurai dan mengekstrak teks dari berbagai format file dengan mulus.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
- Visual Studio: Instal Visual Studio di sistem Anda.
-  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser dari[Di Sini](https://releases.groupdocs.com/parser/net/).
- Pemahaman dasar C#: Keakraban dengan bahasa pemrograman C#.

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Buat instance`Parser` kelas dengan jalur ke file sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode ada di sini...
}
```
## Langkah 2: Ekstrak Teks Berformat Penurunan Harga
 Di dalam`using`blok, gunakan`GetFormattedText` metode untuk mengekstrak teks yang diformat sebagai Markdown:
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Markdown)))
{
    // Kode ada di sini...
}
```
## Langkah 3: Baca dan Keluarkan Konten yang Diekstraksi
 Baca konten Markdown yang diekstrak dari`TextReader`:
```csharp
string markdownContent = reader == null ? "Formatted text extraction isn't supported" : reader.ReadToEnd();
Console.WriteLine(markdownContent);
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara mengekstrak konten Markdown dari dokumen menggunakan GroupDocs.Parser untuk .NET. Pustaka canggih ini menyederhanakan proses penguraian dan ekstraksi teks, memungkinkan pengembang bekerja secara efisien dengan berbagai format file.
## FAQ
### Bisakah GroupDocs.Parser menangani format file yang berbeda?
Ya, GroupDocs.Parser mendukung berbagai format file termasuk DOCX, PDF, PPTX, XLSX, dan banyak lagi.
### Apakah GroupDocs.Parser kompatibel dengan .NET Core?
Ya, GroupDocs.Parser mendukung .NET Framework dan .NET Core.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Apakah GroupDocs.Parser menyediakan dukungan untuk pengembang?
 Ya, Anda bisa mendapatkan dukungan pengembang di[Forum Grup Dokumen](https://forum.groupdocs.com/c/parser/17).
### Di mana saya dapat membeli lisensi untuk GroupDocs.Parser?
 Anda dapat membeli lisensi[Di Sini](https://purchase.groupdocs.com/buy).