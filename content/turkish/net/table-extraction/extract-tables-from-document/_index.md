---
title: Belgeden Tabloları Çıkart
linktitle: Belgeden Tabloları Çıkart
second_title: GroupDocs.Parser .NET API'si
description: Groupdocs.Parser for .NET'i kullanarak belgelerden tabloları nasıl çıkaracağınızı öğrenin. Bu işlevselliği entegre etmeye ilişkin ayrıntılı bir kılavuz için takip edin.
weight: 10
url: /tr/net/table-extraction/extract-tables-from-document/
---

# Belgeden Tabloları Çıkart

## giriiş
Groupdocs.Parser for .NET, belge ayrıştırmayı kolaylaştıran, belgelerden tablolar, metin, meta veriler ve daha fazlası gibi değerli bilgileri çıkarmanıza olanak tanıyan kapsamlı bir kitaplıktır. Bu öğreticide özellikle Groupdocs.Parser API'sini kullanarak belgelerden tablo çıkarmaya odaklanıyoruz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Sisteminizde Visual Studio yüklü.
- .NET Framework veya .NET Core yüklü.
- Temel C# programlama bilgisi.

## Ad Alanlarını İçe Aktar
Groupdocs.Parser sınıflarına ve yöntemlerine erişmek için öncelikle gerekli ad alanlarını içe aktarmanız gerekir.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Yeni bir örneğini başlat`Parser` örnek belgenizin yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: Tablo Çıkarma Desteğini Kontrol Edin
 Belgenin tablo çıkarmayı destekleyip desteklemediğini doğrulamak için`Features` mülkiyeti`Parser` sınıf.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Adım 3: Tablo Düzenini Tanımlayın
Çıkarmak istediğiniz tabloların düzenini kullanarak tanımlayın.`TemplateTableLayout`. Belgenizin yapısına göre sütun genişliklerini ve satır yüksekliklerini belirtin.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Adım 4: Tablo Çıkarma Seçeneklerini Ayarlayın
 Yaratmak`PageTableAreaOptions` tabloların nasıl çıkarılması gerektiğini belirtmek için tanımlanmış düzen ile.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Adım 5: Tabloları Çıkarın
 Kullanın`GetTables` yöntemi`Parser` belirtilen seçeneklere göre belgeden tablo çıkarmak için sınıf.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Adım 6: Yineleyin ve Tablo Verilerine Erişin
Hücre verilerine erişmek için çıkarılan tabloları ve bunların ilgili satırlarını ve sütunlarını yineleyin.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Çözüm
Bu öğreticide, belgelerden tabloları verimli bir şekilde çıkarmak için Groupdocs.Parser for .NET'in nasıl kullanılacağını ele aldık. Bu kitaplığın yeteneklerinden yararlanarak tablo ayıklamayı .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilirsiniz.

## SSS'ler
### Groupdocs.Parser farklı belge formatlarını işleyebilir mi?
Evet, Groupdocs.Parser, DOCX, PDF, XLSX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Groupdocs.Parser for .NET'in deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### Groupdocs.Parser ile ilgili sorgular için nasıl destek alabilirim?
 Ziyaret edebilirsiniz[Groupdocs.Parser forumu](https://forum.groupdocs.com/c/parser/17) yardım için.
### Groupdocs.Parser lisansını nereden satın alabilirim?
 adresinden lisans satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy).
### Değerlendirme amacıyla nasıl geçici lisans alabilirim?
 Geçici lisans alabilirsiniz[Burada](https://purchase.groupdocs.com/temporary-license/).