---
title: Excel Belgesinden Metni HTML Olarak Çıkarma
linktitle: Excel Belgesinden Metni HTML Olarak Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak Excel belgelerinden nasıl metin ayıklayacağınızı ve bunu HTML'ye nasıl dönüştüreceğinizi öğrenin.
type: docs
weight: 13
url: /tr/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## giriiş
Bu öğreticide, bir Excel belgesinden metin ayıklamak ve onu HTML biçimine dönüştürmek için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin çeşitli belge formatlarıyla çalışmasına, metin ve meta verileri verimli bir şekilde ayıklamasına olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki kurulumlara sahip olduğunuzdan emin olun:
- Sisteminizde Visual Studio yüklü.
- C# programlamanın temel anlayışı.
-  .NET için GroupDocs.Parser kitaplığı. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/parser/net/).
## Ad Alanlarını İçe Aktar
GroupDocs.Parser işlevlerine erişmek için C# projenize gerekli ad alanlarını ekleyerek başlayın.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 İlk olarak, örneği oluşturun`Parser` Excel belgenizin yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Daha fazla kod buraya gelecek
}
```
 Yer değiştirmek`"YourSampleFile.xlsx"` Excel dosyanızın yolu ile birlikte.
## Adım 2: Metni HTML Olarak Çıkarın
 İçinde`using` bloğu`Parser` örneğin, şunu kullanın:`GetFormattedText` HTML modunda biçimlendirilmiş metni çıkarma yöntemi.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Daha fazla kod buraya gelecek
    }
}
```
## 3. Adım: Çıkarılan HTML Metnini Okuyun ve Yazdırın
 Daha sonra, çıkarılan HTML metnini okuyun.`TextReader` ve konsola yazdırın.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Bu kod yürütüldüğünde, metni Excel belgesinden çıkaracak ve konsolda HTML formatı olarak görüntüleyecektir.
## Çözüm
Bu eğitimde, bir Excel belgesinden metin ayıklamak ve onu HTML biçimine dönüştürmek için GroupDocs.Parser for .NET'i nasıl kullanacağımızı öğrendik. Bu kitaplık, çeşitli belge biçimleriyle çalışmanın basit bir yolunu sunarak geliştiricilerin uygulamalarında metin çıkarma görevlerini verimli bir şekilde gerçekleştirmelerine olanak tanır.

## SSS'ler
### GroupDocs.Parser, Excel'in yanı sıra diğer belge formatlarını da işleyebilir mi?
Evet, GroupDocs.Parser; PDF, Word, PowerPoint ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### GroupDocs.Parser .NET Core ile uyumlu mu?
Evet, GroupDocs.Parser hem .NET Framework hem de .NET Core ile uyumludur.
### GroupDocs.Parser, metin çıkarma sırasında biçimlendirmeyi koruyor mu?
Evet, GroupDocs.Parser, metin çıkarma sırasında yazı tipleri, stiller ve düzen gibi formatları koruyabilir.
### GroupDocs.Parser'ı kullanarak belgelerden meta verileri çıkarabilir miyim?
Evet, GroupDocs.Parser, desteklenen belge türlerinden yazar, oluşturulma tarihi ve daha fazlası gibi meta verilerin çıkarılmasına olanak tanır.
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).