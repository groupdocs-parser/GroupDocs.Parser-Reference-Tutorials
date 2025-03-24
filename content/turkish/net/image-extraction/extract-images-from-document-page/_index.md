---
title: Belge Sayfasından Görüntüleri Çıkarma
linktitle: Belge Sayfasından Görüntüleri Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerden görüntüleri nasıl çıkaracağınızı öğrenin. Belge işleme yeteneklerinizi geliştirin.
weight: 12
url: /tr/net/image-extraction/extract-images-from-document-page/
---

# Belge Sayfasından Görüntüleri Çıkarma

## giriiş
Bu eğitimde, GroupDocs.Parser for .NET'i kullanarak bir belge sayfasından görüntülerin nasıl çıkarılacağını öğreneceğiz. GroupDocs.Parser, PDF, Microsoft Word, Excel, PowerPoint ve diğerleri gibi çeşitli belge formatlarından metin, meta veriler, resimler ve daha fazlasını çıkarmanıza olanak tanıyan güçlü bir kitaplıktır. Bu kütüphaneyi kullanarak bir belge sayfasından görseller çıkarmak için gerekli adımları izleyeceğiz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Makinenizde Visual Studio yüklü.
- C# ve .NET programlamanın temel anlayışı.
- .NET kitaplığı için GroupDocs.Parser yüklendi. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/parser/net/).

## Ad Alanlarını İçe Aktar
GroupDocs.Parser'ın işlevlerinden yararlanmak için C# projenize gerekli ad alanlarını içe aktararak başlayın.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Bir örneğini oluşturarak başlayın`Parser` sınıfını seçin ve örnek belgenizin yolunu belirtin.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kodunuz burada
}
```
## Adım 2: Görüntü Çıkarma Desteği İçin Belgeyi Kontrol Edin
 Daha sonra belgenin görüntü çıkarmayı destekleyip desteklemediğini kontrol edin.`Features.Images` mülk.
```csharp
if (!parser.Features.Images)
{
    Console.WriteLine("Document doesn't support image extraction.");
    return;
}
```
## 3. Adım: Belge Bilgilerini Alın
 kullanarak belge hakkındaki bilgileri alın.`GetDocumentInfo()` yöntem.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Adım 4: Belge Sayfaları Üzerinde Yineleme Yapın
Belgenin sayfa içerip içermediğini kontrol edin ve ardından görüntüleri çıkarmak için her sayfayı yineleyin.
```csharp
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Sayfadan görsel çıkarmak için kodunuz
}
```
## Adım 5: Her Sayfadan Görüntüleri Çıkarın
 Sayfa yineleme döngüsü içinde şunu kullanın:`GetImages(pageIndex)` Her sayfadan görsel alma yöntemi.
```csharp
foreach (PageImageArea image in parser.GetImages(pageIndex))
{
    Console.WriteLine($"Rectangle: {image.Rectangle}, FileType: {image.FileType}");
    // Görüntüyü kaydetmek veya işlemek için ek kod
}
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir belge sayfasından görüntülerin nasıl çıkarılacağını araştırdık. Ayrıştırıcı örneği oluşturma, görüntü çıkarma desteğini kontrol etme, belge bilgilerini alma, sayfalar üzerinde yineleme yapma ve her sayfadan görüntüleri çıkarma gibi temel adımları ele aldık. Artık görüntü çıkarma işlevini .NET uygulamalarınıza verimli bir şekilde entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser, PDF belgelerinden resim çıkarabilir mi?
Evet, GroupDocs.Parser, PDF dahil çeşitli belge formatlarından görüntü çıkarmayı destekler.
### GroupDocs.Parser, belgelerin toplu işlenmesi için uygun mudur?
Kesinlikle! Birden fazla belgeyi toplu olarak işlemek ve istenen içeriği verimli bir şekilde çıkarmak için GroupDocs.Parser'ı kullanabilirsiniz.
### GroupDocs.Parser için daha fazla kaynağı ve desteği nerede bulabilirim?
 Ziyaret edebilirsiniz[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17) topluluk desteği ve tartışmalar için.
### Satın almadan önce GroupDocs.Parser'ı deneyebilir miyim?
 Evet, alabilirsiniz[ücretsiz deneme sürümü](https://releases.groupdocs.com/) Kütüphanenin yeteneklerini değerlendirmek.
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Bir satın alabilirsiniz[geçici lisans](https://purchase.groupdocs.com/temporary-license/) test ve geliştirme amaçlı.