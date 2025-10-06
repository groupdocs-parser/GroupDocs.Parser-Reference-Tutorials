---
title: Muat Dokumen dari Disk Lokal
linktitle: Muat Dokumen dari Disk Lokal
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak teks dari berbagai format dokumen menggunakan GroupDocs.Parser untuk .NET. Ekstraksi teks yang mudah dan efisien dengan C#.
weight: 11
url: /id/net/document-loading/load-document-from-local-disk/
type: docs
---
# Muat Dokumen dari Disk Lokal

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak teks dari dokumen. GroupDocs.Parser adalah perpustakaan canggih yang memungkinkan pengembang mengurai berbagai format dokumen dan mengekstrak konten teks secara terprogram. Kami akan membahas langkah-langkah yang diperlukan untuk memulai ekstraksi teks menggunakan perpustakaan ini.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menginstal prasyarat berikut:
- Visual Studio diinstal pada sistem Anda.
- Pengetahuan dasar bahasa pemrograman C#.
-  GroupDocs.Parser untuk perpustakaan .NET diinstal (unduh[Di Sini](https://releases.groupdocs.com/parser/net/)).

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Langkah 1: Muat Dokumen dari Disk Lokal
 Mulailah dengan memuat dokumen dari disk lokal Anda. Mengganti`"Your Sample File"` dengan jalur ke dokumen target Anda.
```csharp
// Atur jalur file
string filePath = "Your Sample File";
// Buat instance kelas Parser dengan filePath
using (Parser parser = new Parser(filePath))
{
    // Ekstrak teks ke pembaca
    using (TextReader reader = parser.GetText())
    {
        //Cetak teks yang diekstraksi dari dokumen
        // Jika ekstraksi teks tidak didukung, pembaca akan menjadi nol
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Penjelasan Langkah-Langkahnya
1. Mengatur Jalur File: Mulailah dengan menentukan jalur ke dokumen yang teksnya ingin Anda ekstrak (`filePath` variabel).
2.  Membuat Instance Parser: Buat instance`Parser` kelas dengan melewati`filePath`.
3.  Mengekstrak Teks: Gunakan`GetText()` metode`Parser` misalnya untuk mendapatkan a`TextReader` objek yang berisi teks yang diekstraksi dari dokumen.
4.  Membaca Teks yang Diekstraksi: Memanfaatkan`ReadToEnd()` metode`TextReader` untuk mengambil seluruh konten teks yang diekstraksi dari dokumen.
5.  Menangani Format yang Tidak Didukung: Jika format dokumen tidak mendukung ekstraksi teks, file`reader` objek akan menjadi`null`, dan Anda dapat menangani skenario ini dengan tepat.

## Kesimpulan
Dalam tutorial ini, kami telah membahas langkah-langkah awal untuk mengekstrak teks dari dokumen menggunakan GroupDocs.Parser untuk .NET. Pustaka ini menawarkan fitur ekstensif untuk penguraian dokumen, memungkinkan pengembang bekerja secara efisien dengan berbagai format file dalam aplikasi mereka.

## FAQ
### Apakah GroupDocs.Parser kompatibel dengan semua format dokumen?
GroupDocs.Parser mendukung berbagai format termasuk PDF, dokumen Microsoft Office (Word, Excel, PowerPoint), dan banyak lagi.
### Bisakah saya mengekstrak metadata beserta teks menggunakan GroupDocs.Parser?
Ya, GroupDocs.Parser memungkinkan ekstraksi konten teks dan metadata dari format dokumen yang didukung.
### Di mana saya dapat menemukan lebih banyak sumber daya dan dukungan untuk GroupDocs.Parser?
 Mengunjungi[Dokumentasi GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) untuk referensi API terperinci dan jelajahi[Forum Grup Dokumen](https://forum.groupdocs.com/c/parser/17) untuk dukungan masyarakat.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Parser?
 Anda dapat meminta a[izin sementara](https://purchase.groupdocs.com/temporary-license/) untuk tujuan evaluasi dan pengujian.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Parser?
 Ya, Anda dapat mengunduh a[uji coba gratis](https://releases.groupdocs.com/) versi GroupDocs.Parser.