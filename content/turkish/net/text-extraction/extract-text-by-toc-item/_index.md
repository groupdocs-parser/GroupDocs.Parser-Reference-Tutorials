---
title: İçindekiler Tablosu (TOC) Öğesine Göre Metni Çıkart
linktitle: İçindekiler Tablosu (TOC) Öğesine Göre Metni Çıkart
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak İçindekiler Tablosuna (TOC) göre metni çıkarın. Yapılandırılmış veri çıkarmaya yönelik etkili belge ayrıştırma tekniklerini öğrenin.
weight: 15
url: /tr/net/text-extraction/extract-text-by-toc-item/
type: docs
---
# İçindekiler Tablosu (TOC) Öğesine Göre Metni Çıkart

## giriiş
Bu öğreticide, belgelerden İçindekiler Tablosu (TOC) öğelerine dayalı olarak metin çıkarmak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, verimli belge ayrıştırma ve çıkarmaya olanak tanıyan güçlü bir araçtır.
## Önkoşullar
Bu eğitime devam etmeden önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1. Visual Studio: Sisteminize Visual Studio IDE'yi yükleyin.
2.  .NET için GroupDocs.Parser: .NET için GroupDocs.Parser'ı şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
3. İçindekiler Tablosunu İçeren Örnek Bir Belge: İçindekiler Tablosu içeren bir belge (örneğin, PDF, DOCX) hazırlayın.

## Ad Alanlarını İçe Aktarma
Öncelikle C# projenize gerekli ad alanlarını ekleyin:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Örnekleyin`Parser` örnek belgenizin yolunu içeren sınıf:
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // Sonraki adımlarla buradan devam edin...
}
```
## Adım 2: İçindekiler Tablosunu Çıkarın (TOC)
Belgedeki İçindekiler (TOC) öğelerini alın:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## 3. Adım: İçindekiler Öğeleri Üzerinde Yineleme Yapın ve Metni Çıkarın
Her TOC öğesini yineleyin ve karşılık gelen metni çıkarın:
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET kullanılarak İçindekiler Tablosu (TOC) öğelerine dayalı bir belgeden metnin nasıl çıkarılacağı gösterilmiştir. Özetlenen adımları izleyerek, belgelerinizdeki belirli içeriği programlı olarak verimli bir şekilde ayrıştırabilir ve çıkarabilirsiniz.

## SSS'ler
### GroupDocs.Parser hangi dosya formatlarını destekler?
GroupDocs.Parser, PDF, Microsoft Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) ve daha fazlası dahil olmak üzere çok çeşitli belge formatlarını destekler.
### GroupDocs.Parser'ı kullanarak tablo veya resim gibi yapılandırılmış verileri çıkarabilir miyim?
Evet, GroupDocs.Parser, çeşitli belge türlerinden tablolar, resimler ve meta veriler gibi yapılandırılmış verileri ayıklamak için API'ler sağlar.
### GroupDocs.Parser büyük belgeler için uygun mudur?
GroupDocs.Parser, büyük belgeleri verimli bir şekilde işlemek için optimize edilmiştir ve kapsamlı dosyalardan içeriğin sorunsuz bir şekilde çıkarılmasına olanak tanır.
### GroupDocs.Parser için nasıl teknik destek alabilirim?
 Şu adresten teknik destek arayabilir ve toplulukla etkileşime girebilirsiniz:[GroupDocs.Parser Forumu](https://forum.groupdocs.com/c/parser/17).
### GroupDocs değerlendirme için ücretsiz deneme sunuyor mu?
Evet, GroupDocs.Parser'ın ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).