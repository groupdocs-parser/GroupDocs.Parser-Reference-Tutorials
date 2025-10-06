---
title: Biçimlendirilmiş Metni Belge Sayfasından Çıkart
linktitle: Biçimlendirilmiş Metni Belge Sayfasından Çıkart
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belge sayfalarından biçimlendirilmiş metni çıkarın. Verimli ve güvenilir metin çıkarma çözümü.
weight: 11
url: /tr/net/formatted-text-extraction/extract-formatted-text-from-document-page/
type: docs
---
# Biçimlendirilmiş Metni Belge Sayfasından Çıkart

## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak belge sayfalarından biçimlendirilmiş metni çıkarma sürecinde size rehberlik edeceğiz. Bu kitaplık, PDF, Word, Excel ve daha fazlası gibi çeşitli belge formatlarındaki metinleri verimli bir şekilde ayrıştırmanıza ve çıkarmanıza olanak tanır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Sisteminizde Visual Studio yüklü.
- Temel C# programlama bilgisi.
-  .NET kitaplığı için GroupDocs.Parser. İndirebilirsin[Burada](https://releases.groupdocs.com/parser/net/).

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# projenize aktararak başlayın.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Bir örneğini oluşturarak başlayın`Parser` örnek dosyanızın yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kod buraya gelecek
}
```
## 2. Adım: Biçimlendirilmiş Metin Çıkarmanın Desteklenip Desteklenmediğini Kontrol Edin
Metin çıkarmaya devam etmeden önce belgenin biçimlendirilmiş metin çıkarmayı destekleyip desteklemediğini doğrulayın.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## 3. Adım: Belge Bilgilerini Alın
Sayfa sayısı gibi belgeyle ilgili bilgileri alın.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Adım 4: Belge Sayfaları Üzerinde Yineleme Yapın ve Biçimlendirilmiş Metni Çıkarın
Belgenin her sayfasını yineleyin ve belirtilen seçenekleri (örneğin, Markdown formatı) kullanarak formatlanmış metni çıkarın.
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Çözüm
Artık GroupDocs.Parser for .NET'i kullanarak belge sayfalarından biçimlendirilmiş metni nasıl çıkaracağınızı biliyorsunuz. Bu kütüphane, çeşitli dosya formatlarından metin çıkarmak için güçlü ve kullanımı kolay bir çözüm sunar.

## SSS'ler
### GroupDocs.Parser farklı dosya formatlarını işleyebilir mi?
Evet, GroupDocs.Parser, PDF, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Parser .NET Core ile uyumlu mu?
Evet, GroupDocs.Parser .NET Core ve .NET Framework'ü destekler.
### GroupDocs.Parser, çıkarma sırasında metin biçimlendirmesini koruyor mu?
Evet, GroupDocs.Parser, metin ayıklanırken stiller ve yazı tipleri gibi formatları koruyabilir.
### GroupDocs.Parser'ı kullanarak görüntüleri ve meta verileri çıkarabilir miyim?
Evet, GroupDocs.Parser belgelerden görsellerin, meta verilerin ve metnin çıkarılmasına olanak tanır.
### GroupDocs.Parser için nasıl destek alabilirim?
 adresinden destek alabilirsiniz.[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).