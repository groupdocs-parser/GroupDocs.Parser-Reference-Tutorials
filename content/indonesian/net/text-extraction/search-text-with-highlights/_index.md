---
title: Cari Teks dengan Sorotan
linktitle: Cari Teks dengan Sorotan
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mencari dan menyorot teks dalam dokumen menggunakan GroupDocs.Parser untuk .NET. Ekstrak wawasan berharga secara efisien.
type: docs
weight: 24
url: /id/net/text-extraction/search-text-with-highlights/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mencari teks dalam dokumen dan menyorot hasil pencarian. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan Anda bekerja dengan berbagai format dokumen dan mengekstrak teks, metadata, dan banyak lagi.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1.  GroupDocs.Parser untuk .NET: Unduh dan instal perpustakaan dari[Di Sini](https://releases.groupdocs.com/parser/net/).
2. IDE: Gunakan Visual Studio atau IDE pilihan lainnya untuk pengembangan .NET.
3. File Contoh: Siapkan contoh dokumen (misalnya PDF, DOCX) untuk pencarian teks.

## Impor Namespace
Pertama, mulailah dengan mengimpor namespace yang diperlukan dalam proyek .NET Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Langkah 1: Buat Instans Parser
 Mulailah dengan membuat instance`Parser` kelas dengan jalur ke file sampel Anda:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kode Anda di sini
}
```
## Langkah 2: Tentukan Opsi Sorotan
 Tentukan`HighlightOptions` untuk mengonfigurasi cara hasil penelusuran harus disorot. Misalnya, menyetel jendela konteks 15 karakter:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Langkah 3: Cari Teks
Sekarang, lakukan pencarian teks di dalam dokumen. Berikan kata kunci yang ingin Anda cari (misalnya, "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Langkah 4: Proses Hasil Pencarian
Ulangi hasil pencarian dan tampilkan teks yang ditemukan bersama dengan sorotan:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Kesimpulan
Dalam tutorial ini, Anda mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mencari teks dalam dokumen dan menyorot hasil pencarian. Fungsionalitas ini bisa sangat berguna untuk ekstraksi dan analisis teks di aplikasi .NET Anda.

## FAQ
### Apakah GroupDocs.Parser cocok untuk memproses berbagai format dokumen?
Ya, GroupDocs.Parser mendukung berbagai format dokumen termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.
### Bisakah saya menggunakan GroupDocs.Parser untuk mengekstrak metadata dari dokumen?
Sangat! GroupDocs.Parser memungkinkan Anda mengekstrak metadata, teks, dan data terstruktur dari dokumen.
### Di mana saya dapat menemukan dukungan atau mengajukan pertanyaan tentang GroupDocs.Parser?
 Anda dapat mengunjungi[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) untuk pertanyaan terkait dukungan apa pun.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat mengakses a[uji coba gratis](https://releases.groupdocs.com/) dari GroupDocs.Parser untuk mengevaluasi fitur-fiturnya.
### Bagaimana cara membeli lisensi untuk GroupDocs.Parser?
 Anda dapat membeli lisensi dari[Di Sini](https://purchase.groupdocs.com/buy) dan juga mendapatkan izin sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).