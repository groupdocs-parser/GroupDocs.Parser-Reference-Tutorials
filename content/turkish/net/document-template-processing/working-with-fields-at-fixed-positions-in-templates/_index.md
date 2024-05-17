---
title: Şablonlarda Sabit Konumlardaki Alanlarla Çalışma
linktitle: Şablonlarda Sabit Konumlardaki Alanlarla Çalışma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerden nasıl veri ayıklayacağınızı öğrenin. Kod örnekleriyle kapsamlı eğitim.
type: docs
weight: 11
url: /tr/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak şablonlar içindeki sabit konumlardaki alanlarla nasıl çalışılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin PDF, Word, Excel ve daha fazlası gibi çeşitli belge formatlarından veri çıkarmasına olanak tanıyan güçlü bir belge ayrıştırma kitaplığıdır. Özellikle, sabit konumlarına göre hedeflenen bilgileri çıkarmak için şablon alanlarını tanımlamaya ve kullanmaya odaklanacağız.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- C# ve .NET geliştirmenin temel anlayışı.
- Sisteminizde Visual Studio yüklü.
- .NET kitaplığı için GroupDocs.Parser yüklendi. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/parser/net/).
- Test için örnek belge dosyaları.

## Ad Alanlarını İçe Aktar
C# projenize gerekli ad alanlarını ekleyerek başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 1. Adım: Şablon Alanı Tanımlayın
Öncelikle şablon içinde sabit konumu olan bir alan tanımlayın. Bu alan, verilerin çıkarılacağı alanı temsil eder.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Burada:
- `Rectangle` alanın konumunu ve boyutunu belirtir.
- `Point(35, 135)` sol üst köşe koordinatlarını temsil eder.
- `Size(100, 10)` Alanın genişliğini ve yüksekliğini tanımlar.
- `"FromCompany"` bu alana atanan addır.
## 2. Adım: Şablon Oluşturun
Tanımlanan alanı kullanarak bir şablon oluşturun.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
`Template` nesne tanımlanmış alanları tutar.
## Adım 3: Şablonu Kullanarak Belgeyi Ayrıştırma
 Örnekleyin`Parser` hedef belge yolu ile sınıfa gidin ve ardından oluşturulan şablonu kullanarak belgeyi ayrıştırın.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Çıkarılan veriler üzerinden yineleme
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Burada:
- `Parser` örnek belge dosya yolu ile başlatılır.
- `ParseByTemplate` yöntemi, sağlanan şablona dayalı olarak verileri çıkarmak için kullanılır.
-  Çıkarılan verilere şunlar kullanılarak erişilir:`DocumentData`burada her öğe tanımlanmış bir alana karşılık gelir.

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak şablonlardaki sabit konumlardaki alanlarla çalışma sürecini ele aldık. Geliştiriciler, belirli alan konumlarına sahip şablonlar tanımlayarak, hedeflenen verileri çeşitli belge formatlarından doğru bir şekilde çıkarabilir.

## SSS'ler
### GroupDocs.Parser tüm belge formatlarıyla uyumlu mu?
 GroupDocs.Parser, PDF, Microsoft Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler. Bakın[dokümantasyon](https://reference.groupdocs.com/parser/net/) ayrıntılı bir liste için.
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Test amaçlı olarak geçici bir lisans alabilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser desteğini nerede bulabilirim?
 Teknik yardım ve tartışmalar için şu adresi ziyaret edin:[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).
### Satın almadan önce GroupDocs.Parser'ı deneyebilir miyim?
 Evet, ücretsiz deneme sürümüyle kütüphaneyi keşfedebilirsiniz[Burada](https://releases.groupdocs.com/).
### GroupDocs.Parser lisansını nasıl satın alabilirim?
 Lisans satın almak için şu adresi ziyaret edin:[satın alma sayfası](https://purchase.groupdocs.com/buy).