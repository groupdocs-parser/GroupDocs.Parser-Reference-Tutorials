---
title: Iterasi Melalui Bidang
linktitle: Iterasi Melalui Bidang
second_title: GroupDocs.Parser .NET API
description: Pelajari cara mengekstrak data terstruktur dari dokumen menggunakan GroupDocs.Parser untuk .NET. Tingkatkan aplikasi .NET Anda dengan kemampuan ekstraksi data dokumen.
type: docs
weight: 11
url: /id/net/data-extraction-from-templates/iterate-through-fields/
---
## Perkenalan
GroupDocs.Parser untuk .NET adalah perpustakaan canggih yang memungkinkan pengembang mengekstrak data dari berbagai format dokumen seperti PDF, Microsoft Word, Excel, dan PowerPoint. Tutorial ini akan memandu Anda melalui proses penggunaan GroupDocs.Parser untuk melakukan iterasi melalui bidang dokumen dan mengekstrak data tertentu menggunakan templat. Di akhir tutorial ini, Anda akan dapat mengekstrak data terstruktur secara efisien dari dokumen di aplikasi .NET Anda.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan prasyarat berikut:
- Pengetahuan dasar tentang pemrograman C#.
- Visual Studio diinstal pada mesin Anda.
- GroupDocs.Parser untuk perpustakaan .NET diinstal dan direferensikan dalam proyek Anda.

## Impor Namespace
Untuk memulai, tambahkan namespace yang diperlukan ke file C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Mari kita bagi prosesnya menjadi petunjuk langkah demi langkah.
## Langkah 1: Tentukan Bidang Templat
Pertama, tentukan bidang yang ingin Anda ekstrak dari dokumen menggunakan ekspresi reguler.
```csharp
// Tentukan bidang "harga".
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Tentukan bidang "email".
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Buat templat dengan bidang yang ditentukan
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
Pada langkah ini, kami telah menetapkan dua bidang: satu untuk mengekstraksi harga (diidentifikasi dengan tanda dolar dan angka) dan satu lagi untuk mengekstrak alamat email.
## Langkah 2: Parsing Dokumen
 Selanjutnya, gunakan`Parser` kelas untuk mengurai dokumen menggunakan templat yang ditentukan.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Parsing dokumen berdasarkan templat
    DocumentData data = parser.ParseByTemplate(template);
    // Iterasi melalui data yang diekstraksi
    for (int i = 0; i < data.Count; i++)
    {
        // Cetak nama bidang
        Console.Write(data[i].Name + ": ");
        // Periksa apakah area yang diekstraksi adalah teks
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Di sini, kami menginisialisasi`Parser` dengan jalur ke dokumen sampel Anda, lalu parsing dokumen tersebut menggunakan templat yang ditentukan. Kami kemudian mengulangi data yang diekstraksi dan mencetak nama bidang bersama dengan teks yang diekstraksi.
## Kesimpulan
Dalam tutorial ini, kita telah menjelajahi cara menggunakan GroupDocs.Parser untuk .NET untuk mengekstrak data tertentu dari dokumen menggunakan templat. Dengan memanfaatkan ekspresi reguler dan templat, Anda dapat mengekstrak informasi terstruktur secara efisien dari berbagai format dokumen. Bereksperimenlah dengan berbagai templat dan tipe dokumen untuk memenuhi kebutuhan ekstraksi spesifik Anda.

## FAQ
### Bisakah GroupDocs.Parser mengekstrak data dari dokumen yang dipindai?
Ya, GroupDocs.Parser dapat mengekstrak teks dan metadata dari dokumen PDF yang dipindai dan dapat dicari.
### Apakah GroupDocs.Parser kompatibel dengan aplikasi .NET Core?
Ya, GroupDocs.Parser mendukung .NET Core bersama dengan .NET Framework.
### Format dokumen apa yang didukung GroupDocs.Parser?
GroupDocs.Parser mendukung berbagai format termasuk PDF, Microsoft Word, Excel, PowerPoint, dan banyak lagi.
### Bagaimana cara menangani dokumen besar dengan GroupDocs.Parser?
GroupDocs.Parser menyediakan opsi untuk mengekstrak data dari halaman atau bagian tertentu dari dokumen besar, memastikan pemrosesan yang efisien.
### Bisakah saya menggunakan GroupDocs.Parser hanya untuk ekstraksi teks?
Ya, Anda dapat mengekstrak konten teks biasa dari dokumen menggunakan GroupDocs.Parser tanpa memerlukan pemformatan yang rumit.