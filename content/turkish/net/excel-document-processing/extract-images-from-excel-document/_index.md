---
title: Excel Belgesinden Görüntüleri Çıkarma
linktitle: Excel Belgesinden Görüntüleri Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak Excel belgelerinden görüntüleri nasıl çıkaracağınızı öğrenin. Kod örnekleri içeren adım adım kılavuz.
type: docs
weight: 10
url: /tr/net/excel-document-processing/extract-images-from-excel-document/
---
## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir Excel belgesinden görüntüleri nasıl çıkaracağınızı öğreneceksiniz. GroupDocs.Parser, Excel dosyaları da dahil olmak üzere çeşitli belge formatlarındaki metinleri, meta verileri ve görüntüleri ayrıştırmanıza ve çıkarmanıza olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların ayarlandığından emin olun:
1. Geliştirme Ortamı: Visual Studio'yu veya tercih edilen herhangi bir .NET geliştirme ortamını yükleyin.
2.  GroupDocs.Parser Kütüphanesi: GroupDocs.Parser kütüphanesini indirin ve referans alın. Kütüphaneyi şu adresten alabilirsiniz:[Burada](https://releases.groupdocs.com/parser/net/).
3. Örnek Excel Dosyası: Görüntüleri çıkarmak istediğiniz örnek bir Excel dosyası hazırlayın.
## Ad Alanlarını İçe Aktar
Projenize gerekli ad alanlarını ekleyin:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Bir Excel belgesinden resim çıkarmak için şu adımları izleyin:
## Adım 1: Ayrıştırıcı Sınıfını Örneklendirin
 İlk önce bir örneğini oluşturun`Parser` Excel dosyanızın yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Kodunuz burada...
}
```
## Adım 2: Excel Belgesinden Görüntüleri Alın
 Kullan`GetImages()` Excel dosyasından görüntüleri çıkarma yöntemi.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3. Adım: Görüntü Çıkarma Seçeneklerini Tanımlayın
Çıkarılan görüntüleri kaydetmek için görüntü formatını ve diğer seçenekleri belirtin. Örneğin görüntüleri PNG formatında kaydetmek için:
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Adım 4: Görüntüleri Yineleyin ve Kaydedin
Çıkarılan görüntüler üzerinde yineleme yapın ve her görüntüyü bir dosyaya kaydedin.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Resmi bir PNG dosyasına kaydedin
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Çözüm
Bu öğreticide, bir Excel belgesinden görüntüleri ayıklamak için GroupDocs.Parser for .NET'in nasıl kullanılacağını öğrendiniz. Bu adımları izleyerek görüntü çıkarma yeteneklerini .NET uygulamalarınıza verimli bir şekilde dahil edebilirsiniz.

## SSS'ler
### S: GroupDocs.Parser, Excel'in yanı sıra diğer belge formatlarından da görüntü çıkarabilir mi?
C: Evet, GroupDocs.Parser, Word, PowerPoint, PDF ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### S: GroupDocs.Parser entegrasyonuyla ilgili nasıl destek veya yardım alabilirim?
 C: Destek ve yardım için şu adresi ziyaret edin:[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).
### S: GroupDocs.Parser'ın kullanımı ücretsiz midir?
 C: GroupDocs.Parser ücretsiz deneme olanağı sunar, ancak sürekli kullanım için bir lisans satın almanız gerekebilir. Kontrol edin[fiyatlandırma ve lisanslama](https://purchase.groupdocs.com/buy)detaylar.
### S: Lisans satın almadan önce GroupDocs.Parser'ı deneyebilir miyim?
 C: Evet, alabilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) GroupDocs.Parser'ı değerlendirmek için.
### S: GroupDocs.Parser'a ilişkin ayrıntılı belgeleri nerede bulabilirim?
 C: Kapsamlı içeriğe bakın[dokümantasyon](https://reference.groupdocs.com/parser/net/) GroupDocs.Parser'ın kullanımına ilişkin ayrıntılı bilgi için.