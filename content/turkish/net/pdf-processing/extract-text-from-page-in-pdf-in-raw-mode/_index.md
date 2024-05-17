---
title: Ham Modda PDF'deki Sayfadan Metin Çıkarma
linktitle: Ham Modda PDF'deki Sayfadan Metin Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: C# dilinde GroupDocs.Parser'ı kullanarak PDF'lerden metin çıkarın. Bu güçlü .NET kitaplığıyla verimli PDF metin çıkarmayı öğrenin.
type: docs
weight: 16
url: /tr/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## giriiş
Bu öğreticide, ham modu kullanarak PDF belgelerindeki sayfalardan metin çıkarmak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin çeşitli belge formatlarıyla programlı olarak çalışmasına olanak tanıyan güçlü bir araçtır.
## Önkoşullar
Bu eğitime başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Makinenizde Visual Studio yüklü.
- Temel C# programlama bilgisi.
- .NET kitaplığı için GroupDocs.Parser[buradan indir](https://releases.groupdocs.com/parser/net/).
- Test amaçlı örnek bir PDF dosyası.

## Ad Alanlarını İçe Aktar
Öncelikle C# projenize gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Başlamak için örneği oluşturun`Parser`Örnek PDF dosyanızın yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: Belge Bilgilerini Alın ve Sayfalar Üzerinde Yineleyin
Daha sonra, belge bilgilerini alın ve metni çıkarmak için her sayfayı yineleyin.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Metin çıkarma kodunuz buraya gelecek
}
```
## Adım 3: Her Sayfadan Metni Çıkarın
 Döngünün içinde şunu kullanın:`GetText` Her sayfadan metin çıkarma ve yazdırma yöntemi.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Çözüm
 Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak PDF sayfalarından ham modda nasıl metin çıkaracağımızı öğrendik. Bu süreç bir oluşturmayı içerir.`Parser` Örneğin, belge bilgilerinin elde edilmesi, her sayfada yineleme yapılması ve`GetText` yöntem.

## SSS'ler
### .NET için GroupDocs.Parser nedir?
GroupDocs.Parser for .NET, geliştiricilerin program aracılığıyla çeşitli dosya biçimlerinden metin, meta veriler ve diğer bilgileri ayıklamasına olanak tanıyan bir belge ayrıştırma API'sidir.
### .NET için GroupDocs.Parser'ı nasıl indirebilirim?
 Kütüphaneyi adresinden indirebilirsiniz.[GroupDocs web sitesi](https://releases.groupdocs.com/parser/net/).
### Ücretsiz deneme mevcut mu?
 Evet, GroupDocs.Parser for .NET'in ücretsiz deneme sürümüne şu adresten erişebilirsiniz:[Burada](https://releases.groupdocs.com/).
### .NET için GroupDocs.Parser desteğini nerede bulabilirim?
 Teknik yardım ve topluluk desteği için şu adresi ziyaret edin:[GroupDocs forumu](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser for .NET lisansını nasıl satın alabilirim?
 adresinden lisans satın alabilirsiniz.[satın alma sayfası](https://purchase.groupdocs.com/buy) veya geçici bir lisans edinin[Burada](https://purchase.groupdocs.com/temporary-license/).