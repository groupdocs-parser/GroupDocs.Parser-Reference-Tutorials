---
title: Belge Sayfasından Tabloları Çıkart
linktitle: Belge Sayfasından Tabloları Çıkart
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerden tabloları program aracılığıyla nasıl ayıklayacağınızı öğrenin. Bu kapsamlı eğitim, adım adım rehberlik sağlar.
type: docs
weight: 11
url: /tr/net/table-extraction/extract-tables-from-document-page/
---
## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir belge sayfasından tabloların nasıl çıkarılacağını inceleyeceğiz. GroupDocs.Parser, geliştiricilerin PDF, DOCX, XLSX ve daha fazlası gibi çeşitli belge formatlarıyla çalışmasına olanak tanıyan güçlü bir kitaplıktır. Özelliklerinden yararlanarak, bu belgelerden tablolar gibi yapılandırılmış verileri verimli bir şekilde çıkarabilir, bilgileri programlı olarak işlememize ve analiz etmemize olanak tanır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Makinenizde Visual Studio yüklü.
- C# ve .NET geliştirmenin temel anlayışı.
-  .NET kitaplığı için GroupDocs.Parser. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/parser/net/).
- Çıkarılacak tabloları içeren örnek bir belgeye (PDF, DOCX, vb.) erişim.

## Ad Alanlarını İçe Aktar
Öncelikle C# projenize gerekli ad alanlarını içe aktararak başlayın:
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
 Örnekleyin`Parser` örnek belgenizin yolunu sağlayarak sınıf:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Kodunuz burada devam ediyor...
}
```
## Adım 2: Belge Tablosu Çıkarma Desteğini Kontrol Edin
Devam etmeden önce belgenin tablo çıkarmayı destekleyip desteklemediğini doğrulayın:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Adım 3: Tablo Düzenini Tanımlayın
Belgeden çıkarılacak tabloların düzenini tanımlayın. Belgenizin yapısına göre sütun genişliklerini ve satır yüksekliklerini belirtin:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Sütun genişlikleri
    new double[] { 325, 340, 365, 395 });         // Satır yükseklikleri
```
## Adım 4: Tablo Çıkarma Seçeneklerini Yapılandırın
Belirtilen düzeni kullanarak tablo çıkarma seçenekleri oluşturun:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Adım 5: Belge Bilgilerini Alın
Sayfa sayısı da dahil olmak üzere belgeyle ilgili bilgileri getirin:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Adım 6: Belge Sayfaları Üzerinde Yineleme Yapın
Tabloları çıkarmak için belgenin her sayfasını yineleyin:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Geçerli sayfadaki tabloları çıkarın
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Çıkarılan tablolar üzerinde yineleme
    foreach (PageTableArea table in tables)
    {
        // Tablonun satırları üzerinde yineleme
        for (int row = 0; row < table.RowCount; row++)
        {
            // Tablonun sütunları üzerinde yineleme
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Tablo hücresini alın
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Tablo hücresinin metnini yazdır
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak belge sayfalarından tablo çıkarma işlemini ele aldık. Sağlanan adımları izleyerek, tablo çıkarma işlevini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilir, belgeler içindeki yapılandırılmış verilerin verimli bir şekilde işlenmesini ve değiştirilmesini sağlayabilirsiniz.

## SSS'ler
### GroupDocs.Parser her tür belgeden tablo çıkarabilir mi?
GroupDocs.Parser, PDF, DOCX, XLSX ve daha fazlası gibi çeşitli belge formatlarını destekleyerek uyumlu dosya türlerinden tablo çıkarmayı mümkün kılar.
### GroupDocs.Parser for .NET büyük ölçekli belge işlemeye uygun mu?
Evet, GroupDocs.Parser büyük belgeleri verimli bir şekilde işlemek üzere tasarlanmıştır ve bu da onu kapsamlı veri kümelerinin işlenmesi için uygun hale getirir.
### GroupDocs.Parser tablo çıkarma sırasında biçimlendirmeyi koruyor mu?
Evet, GroupDocs.Parser, tablo ayıklama sırasında hücre sınırları, metin stilleri ve hizalamalar gibi biçimlendirme ayrıntılarını korur.
### İçerik kriterlerine göre belirli tabloları çıkarabilir miyim?
GroupDocs.Parser, çıkarma için düzen şablonlarına veya içerik koşullarına göre belirli tabloları hedeflemek için esnek seçenekler sunar.
### GroupDocs.Parser .NET Core ile uyumlu mu?
Evet, GroupDocs.Parser hem .NET Framework hem de .NET Core ortamlarıyla uyumludur.