---
title: Cari Teks berdasarkan Halaman
linktitle: Cari Teks berdasarkan Halaman
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mencari teks berdasarkan halaman menggunakan GroupDocs.Parser untuk .NET. Ekstrak konten tertentu secara efisien dari dokumen di aplikasi .NET Anda.
type: docs
weight: 22
url: /id/net/text-extraction/search-text-by-pages/
---
## Perkenalan
Dalam dunia pengembangan .NET, penguraian dan ekstraksi teks dari dokumen secara efisien adalah tugas yang sangat penting. GroupDocs.Parser untuk .NET menawarkan kemampuan canggih untuk bekerja dengan berbagai format dokumen, memungkinkan pengembang mencari dan mengekstrak konten tertentu dengan lancar. Tutorial ini akan memandu Anda melalui proses memanfaatkan GroupDocs.Parser untuk mencari teks demi halaman di aplikasi .NET Anda.
## Prasyarat
Sebelum mendalami tutorial ini, pastikan Anda memiliki prasyarat berikut:
- Pemahaman dasar tentang kerangka C# dan .NET
- Visual Studio diinstal pada sistem Anda
-  GroupDocs.Parser untuk perpustakaan .NET diinstal (Unduh dari[Di Sini](https://releases.groupdocs.com/parser/net/))
- Contoh file untuk menguji fungsi pencarian
## Impor Namespace
Pertama, sertakan namespace yang diperlukan dalam proyek Anda untuk mengakses fungsionalitas GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instance Kelas Parser
 Mulailah dengan membuat instance`Parser` kelas dengan jalur ke file sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kode Anda ada di sini
}
```
## Langkah 2: Cari Teks dengan Nomor Halaman
 Memanfaatkan`Search` metode untuk mencari kata kunci tertentu dalam dokumen beserta nomor halaman:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## Langkah 3: Periksa Dukungan Pencarian
Verifikasi apakah operasi pencarian didukung untuk jenis dokumen:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## Langkah 4: Ulangi Hasil Pencarian
Ulangi hasil pencarian untuk mengambil posisi yang diindeks, nomor halaman, dan teks yang ditemukan:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## Kesimpulan
Dalam tutorial ini, kita telah menjelajahi cara mengimplementasikan pencarian teks berdasarkan halaman menggunakan GroupDocs.Parser untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat secara efisien mengintegrasikan fungsi penguraian dan pencarian dokumen ke dalam aplikasi .NET Anda.

## FAQ
### Apakah GroupDocs.Parser kompatibel dengan berbagai format dokumen?
Ya, GroupDocs.Parser mendukung berbagai format dokumen termasuk DOCX, PDF, XLSX, PPTX, dan banyak lagi.
### Bisakah saya mengekstrak gambar dan metadata dari dokumen menggunakan GroupDocs.Parser?
Tentu saja, GroupDocs.Parser memungkinkan ekstraksi gambar, metadata, dan teks dari dokumen.
### Di mana saya dapat menemukan dokumentasi terperinci untuk GroupDocs.Parser?
 Anda dapat mengakses dokumentasinya[Di Sini](https://reference.groupdocs.com/parser/net/).
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat meminta lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya bisa mendapatkan dukungan atau bantuan dengan GroupDocs.Parser?
 Untuk dukungan dan diskusi, kunjungi forum GroupDocs.Parser[Di Sini](https://forum.groupdocs.com/c/parser/17).