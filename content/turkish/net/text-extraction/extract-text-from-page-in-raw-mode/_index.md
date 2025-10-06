---
title: Ham Modda Sayfadan Metin Çıkarma
linktitle: Ham Modda Sayfadan Metin Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: Bu kapsamlı eğitimde Groupdocs.Parser for .NET'i kullanarak belge sayfalarından verimli metin çıkarmayı öğrenin.
weight: 17
url: /tr/net/text-extraction/extract-text-from-page-in-raw-mode/
type: docs
---
# Ham Modda Sayfadan Metin Çıkarma

## giriiş
Bu öğreticide, ham modda belge sayfalarından metin çıkarmak için Groupdocs.Parser for .NET'in nasıl kullanılacağını öğreneceksiniz. Bu kitaplık, çeşitli dosya biçimlerinden içerik ayrıştırmak ve çıkarmak için etkili araçlar sağlayarak geliştiricilerin belge metni ayıklamayı .NET uygulamalarına dahil etmelerine olanak tanır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- C# ve .NET programlamaya ilişkin temel bilgiler
- Makinenizde Visual Studio yüklü
- .NET kitaplığı için Groupdocs.Parser'a erişim
- Test için örnek belge dosyası

## Ad Alanlarını İçe Aktar
C# projenize gerekli ad alanlarını ekleyerek başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. Adım: Ayrıştırıcıyı Başlatın
 İlk önce bir örneğini oluşturun`Parser` Örnek belge dosyanızın yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kodunuz burada
}
```
## 2. Adım: Belge Bilgilerini Alın
 Kullanarak belge hakkındaki bilgileri alın`GetDocumentInfo()` yöntem.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## 3. Adım: Sayfalar Üzerinde Yineleme Yapın ve Metni Çıkarın
Belgenin her sayfasını yineleyin ve metin içeriğini çıkarın.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Sayfadan metin çıkarma
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Çözüm
Artık ham modda belge sayfalarından metin çıkarmak için Groupdocs.Parser for .NET'i nasıl kullanacağınızı öğrendiniz. Bu, çeşitli dosya formatlarındaki metin içeriğini analiz etmesi veya işlemesi gereken uygulamalar için güçlü bir özellik olabilir.

## SSS'ler
### Groupdocs.Parser for .NET tüm dosya formatlarıyla uyumlu mu?
Groupdocs.Parser, PDF, DOCX, XLSX, PPTX, EPUB ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### Bu kitaplığı kullanarak metinle birlikte meta verileri çıkarabilir miyim?
Evet, Groupdocs.Parser belgelerden hem metin hem de meta verileri çıkarmanıza olanak tanır.
### Test için mevcut bir deneme sürümü var mı?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### Groupdocs.Parser için nasıl teknik destek alabilirim?
 Teknik yardım için şu adresi ziyaret edin:[Groupdocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).
### Groupdocs.Parser for .NET lisansını nereden satın alabilirim?
 Lisans satın alabilirsiniz[Burada](https://purchase.groupdocs.com/buy).