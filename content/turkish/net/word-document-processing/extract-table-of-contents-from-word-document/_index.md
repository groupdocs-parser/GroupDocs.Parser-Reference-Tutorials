---
title: Word Belgesinden İçindekiler Tablosunu Çıkarma
linktitle: Word Belgesinden İçindekiler Tablosunu Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak Word belgelerinden İçindekiler Tablosunu (TOC) program aracılığıyla nasıl ayıklayacağınızı öğrenin.
weight: 13
url: /tr/net/word-document-processing/extract-table-of-contents-from-word-document/
---

# Word Belgesinden İçindekiler Tablosunu Çıkarma

## giriiş
Bu öğreticide, bir Word belgesinden İçindekiler Tablosunu (TOC) çıkarmak için GroupDocs.Parser for .NET'i adım adım nasıl kullanacağınızı öğreneceksiniz. GroupDocs.Parser, çeşitli belge formatlarıyla programlı olarak çalışmanıza olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
1. Visual Studio: Sisteminize Visual Studio IDE'yi yükleyin.
2.  GroupDocs.Parser for .NET: GroupDocs.Parser for .NET'i şu adresten indirip yükleyin:[indirme sayfası](https://releases.groupdocs.com/parser/net/).
3. Temel C# Bilgisi: C# programlama diline aşinalık.

## Ad Alanlarını İçe Aktar
Öncelikle GroupDocs.Parser'ı kullanmak için C# projenize gerekli ad alanlarını içe aktarın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
Örnek Word belgenizin yolunu sağlayarak Ayrıştırıcı sınıfını başlatın:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: İçindekiler Tablosunu (TOC) Alın
 Kullan`GetToc()` yöntemi`Parser` İçindekiler tablosunu çıkarmak için nesne:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
```
## Adım 3: İçindekiler Öğelerini Yineleyin
Her bölüme veya kısma erişmek için önceki adımda elde edilen İçindekiler maddeleri arasında dolaşın:
```csharp
foreach (TocItem tocItem in tocItems)
{
    // Kodunuz buraya gelecek
}
```
## Adım 4: İçindekiler Öğelerinden Metni Çıkarın
 Her bir İçindekiler öğesinin (bölüm) metin içeriğini ayıklayın ve yazdırın.`TextReader`:
```csharp
using (TextReader reader = tocItem.ExtractText())
{
    Console.WriteLine("----");
    Console.WriteLine(reader.ReadToEnd());
}
```

## Çözüm
Bu adımları izleyerek, GroupDocs.Parser for .NET'i kullanarak İçindekiler Tablosunu bir Word belgesinden kolayca çıkarabilirsiniz. Bu kitaplık, belge yapılarıyla programlı olarak çalışmanın basit bir yolunu sağlayarak çeşitli belge işleme görevlerini verimli bir şekilde otomatikleştirmenize olanak tanır.

## SSS'ler
### GroupDocs.Parser, TOC'yi PDF veya EPUB gibi diğer belge formatlarından çıkarabilir mi?
Evet, GroupDocs.Parser, PDF, EPUB, Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Parser büyük belgeleri işlemeye uygun mu?
Evet, GroupDocs.Parser, metin çıkarma, meta veri çıkarma ve yapılandırılmış veri çıkarma gibi özelliklerle büyük belgeleri verimli bir şekilde işlemek için optimize edilmiştir.
### GroupDocs.Parser için daha fazla belge ve öğreticiyi nerede bulabilirim?
 Ziyaret edin[GroupDocs.Parser belgeleri](https://tutorials.groupdocs.com/parser/net/) ayrıntılı API referansları ve eğitimleri için.
### GroupDocs.Parser için nasıl destek alabilirim?
 Katılmak[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17) Soru sormak ve toplulukla etkileşime geçmek.
### GroupDocs.Parser'ın deneme sürümü mevcut mu?
 Evet, indirebilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) Özelliklerini keşfetmek için GroupDocs.Parser'a bakın.