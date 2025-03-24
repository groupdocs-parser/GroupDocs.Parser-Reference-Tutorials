---
title: Cari Teks dengan Ekspresi Reguler (Regex)
linktitle: Cari Teks dengan Ekspresi Reguler (Regex)
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mencari teks menggunakan ekspresi reguler dalam dokumen menggunakan GroupDocs.Parser untuk .NET. Ekstrak konten tertentu dengan mudah.
weight: 23
url: /id/net/text-extraction/search-text-by-regex/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari penggunaan GroupDocs.Parser untuk .NET untuk mencari teks dengan ekspresi reguler (Regex) dalam dokumen. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengekstrak teks dan metadata dari berbagai format file seperti PDF, DOCX, XLSX, dan banyak lagi. Mencari teks menggunakan ekspresi reguler sangat berguna untuk menemukan pola atau konten tertentu dalam dokumen secara efisien.
## Prasyarat
Sebelum mendalami tutorial ini, pastikan Anda memiliki hal berikut:
1. Visual Studio: Instal Visual Studio IDE untuk pengembangan .NET.
2.  GroupDocs.Parser untuk .NET: Unduh dan instal GroupDocs.Parser untuk .NET dari[Di Sini](https://releases.groupdocs.com/parser/net/).
3. File Contoh: Siapkan contoh dokumen (PDF, DOCX, dll.) untuk menguji fungsi pencarian.

## Impor Namespace
Pertama, mulailah dengan memasukkan namespace yang diperlukan dalam kode C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Buat instance`Parser` kelas dengan memberikan jalur ke file sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode ada di sini
}
```
 Mengganti`"YourSampleFile.pdf"` dengan jalur ke file Anda yang sebenarnya.
## Langkah 2: Cari Menggunakan Ekspresi Reguler
Tentukan dan jalankan pencarian menggunakan pola ekspresi reguler. Misalnya, untuk menemukan urutan numerik (misalnya bilangan bulat) dalam dokumen:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 Dalam contoh ini,`[0-9]+` adalah pola ekspresi reguler yang cocok dengan satu atau lebih digit.
## Langkah 3: Periksa Dukungan Pencarian
Verifikasi apakah operasi pencarian didukung untuk jenis dokumen:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Langkah 4: Ulangi Hasil Pencarian
Ulangi hasil pencarian dan proses setiap kecocokan:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Loop ini akan mencetak posisi dan teks yang cocok ditemukan dalam dokumen.

## Kesimpulan
Kesimpulannya, memanfaatkan GroupDocs.Parser untuk .NET memungkinkan pencarian teks yang efisien menggunakan ekspresi reguler di berbagai format dokumen. Dengan mengikuti panduan ini, pengembang dapat dengan mudah mengintegrasikan penguraian dokumen dan ekstraksi teks berbasis regex ke dalam aplikasi .NET mereka.

## FAQ
### Bisakah GroupDocs.Parser mencari dalam dokumen terenkripsi?
Tidak, GroupDocs.Parser tidak dapat mencari di dalam dokumen terenkripsi atau dilindungi kata sandi.
### Apakah GroupDocs.Parser mendukung OCR (Pengenalan Karakter Optik)?
Tidak, GroupDocs.Parser tidak menjalankan OCR. Itu bergantung pada ekstraksi teks dari struktur internal dokumen.
### Bisakah saya mencari pola kompleks menggunakan ekspresi reguler?
Ya, GroupDocs.Parser mendukung ekspresi reguler lengkap, memungkinkan pencocokan pola kompleks dalam dokumen.
### Format dokumen apa yang didukung untuk ekstraksi teks?
GroupDocs.Parser mendukung berbagai format, termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### Apakah GroupDocs.Parser kompatibel dengan .NET Core?
Ya, GroupDocs.Parser kompatibel dengan .NET Core untuk pengembangan lintas platform.