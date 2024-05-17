---
title: Ham Modda Excel Sayfasından Metin Çıkarma
linktitle: Ham Modda Excel Sayfasından Metin Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: Bu kapsamlı eğitimde GroupDocs.Parser for .NET'i kullanarak Excel sayfalarından nasıl metin ayıklayacağınızı öğrenin. İndirin ve ayrıştırmaya başlayın.
type: docs
weight: 15
url: /tr/net/excel-document-processing/extract-text-from-excel-sheet-in-raw-mode/
---
## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i ham modda kullanarak Excel sayfalarından nasıl metin ayıklanacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin metin çıkarma ve analiz için Excel dosyaları da dahil olmak üzere çeşitli belge formatlarıyla çalışmasına olanak tanıyan güçlü bir API'dir. Excel sayfalarından metin çıkarma sürecini göstermek için önkoşulları inceleyeceğiz, ad alanlarını içe aktaracağız ve her adımı ayrıntılı olarak ele alacağız.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların ayarlandığından emin olun:
- Visual Studio: Makinenize Visual Studio IDE'yi yükleyin.
-  .NET için GroupDocs.Parser: GroupDocs.Parser'ı şu adresten indirip yükleyin:[indirme sayfası](https://releases.groupdocs.com/parser/net/).
- Örnek Excel Dosyası: Metin çıkarmak için kullanacağınız örnek bir Excel dosyası hazırlayın.

## Ad Alanlarını İçe Aktar
GroupDocs.Parser işlevlerine erişmek için gerekli ad alanlarını C# projenize aktararak başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 İlk önce bir örneğini oluşturun`Parser` örnek Excel dosyanızın yolunu sağlayarak sınıf:
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Metin çıkarma kodunuz buraya gelecek
}
```
## 2. Adım: Belge Bilgilerini Alın
 kullanarak belge bilgilerini alın.`GetDocumentInfo()` yöntem:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Adım 3: Sayfalar Üzerinde Yineleme Yapın
Excel dosyasındaki her sayfada döngü yapın:
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine(string.Format("Page {0}/{1}", p + 1, documentInfo.RawPageCount));
    
    //Her sayfadan metin çıkarma kodunuz buraya gelecek
}
```
## Adım 4: Her Sayfadan Metni Çıkarın
 kullanarak her sayfadaki metni çıkarın.`TextReader`:
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak Excel sayfalarından nasıl metin ayıklanacağını ele aldık. Yukarıda özetlenen adımları izleyerek, .NET uygulamalarınızda daha fazla işlem yapmak veya analiz etmek için metin verilerini Excel dosyalarından verimli bir şekilde alabilirsiniz.

## SSS'ler
### GroupDocs.Parser diğer belge formatlarından metin çıkarabilir mi?
Evet, GroupDocs.Parser, Word, PDF, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Parser büyük Excel dosyalarını işlemeye uygun mu?
Evet, GroupDocs.Parser büyük belgeleri verimli bir şekilde işleyecek şekilde tasarlanmıştır.
### GroupDocs.Parser hakkında daha fazla belgeyi nerede bulabilirim?
 Şuraya başvurabilirsiniz:[dokümantasyon](https://reference.groupdocs.com/parser/net/) detaylı bilgi ve örnekler için.
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Ziyaret etmek[bu bağlantı](https://purchase.groupdocs.com/temporary-license/) Geçici lisans istemek için.
### GroupDocs.Parser müşteri desteği sunuyor mu?
Evet, yardım isteyebilir veya soru sorabilirsiniz.[GroupDocs forumu](https://forum.groupdocs.com/c/parser/17).