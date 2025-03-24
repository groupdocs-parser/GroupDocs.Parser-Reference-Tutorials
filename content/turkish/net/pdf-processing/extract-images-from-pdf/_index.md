---
title: PDF'den Görüntüleri Çıkartın
linktitle: PDF'den Görüntüleri Çıkartın
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak PDF belgelerinden görüntüleri nasıl çıkaracağınızı öğrenin. Kod örnekleri içeren adım adım kılavuz.
weight: 12
url: /tr/net/pdf-processing/extract-images-from-pdf/
---
## giriiş
Bu eğitimde, PDF belgelerinden görüntüleri ayıklamak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin bir .NET ortamında PDF, DOCX, PPTX ve daha fazlası dahil olmak üzere çeşitli belge formatlarıyla çalışmasına olanak tanıyan güçlü bir kitaplıktır. Bu adımları izleyerek PDF dosyalarından görüntüleri zahmetsizce çıkarabileceksiniz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- Sisteminizde Visual Studio yüklü
- C# programlamaya ilişkin temel bilgiler
-  .NET kitaplığı için GroupDocs.Parser (İndir[Burada](https://releases.groupdocs.com/parser/net/))

## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını C# kod dosyanıza ekleyin.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 İlk önce bir örneğini oluşturun`Parser`Örnek PDF dosyanızın yolunu sağlayarak sınıf.
```csharp
// Ayrıştırıcı sınıfının bir örneğini oluşturun
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Resimleri çıkartmaya yönelik kod buraya gelecek
}
```
## Adım 2: Görüntüleri PDF'den Çıkarın
 İçinde`using` bloke edin, kullanın`GetImages` yöntemi`Parser` PDF belgesinden bir resim koleksiyonu almak için örnek.
```csharp
// PDF'den görüntüleri çıkarın
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3. Adım: Görüntü Kaydetme Seçeneklerini Yapılandırın
Çıkarılan görüntülerin nasıl kaydedileceğini belirtmek için seçenekleri tanımlayın. Burada görselleri PNG formatında kaydedeceğiz.
```csharp
// Görüntüleri PNG formatında kaydetmek için seçenekler oluşturun
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Adım 4: Çıkarılan Görüntüler Üzerinde Yineleyin ve Kaydedin
 Her görüntüde yineleme yapın`images` koleksiyonunu oluşturun ve bunları sırayla PNG dosyalarına kaydedin.
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
Bu eğitimde, GroupDocs.Parser for .NET'i kullanarak PDF belgelerinden görüntülerin nasıl çıkarılacağını gösterdik. Bu adımları izleyerek görüntü çıkarma işlevini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser diğer belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Parser, PDF, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Görüntü çıkarma seçeneklerini değiştirebilir miyim?
Kesinlikle! GroupDocs.Parser, görüntü ayıklamayı özelleştirmek için görüntü formatı ve kalite ayarları gibi çeşitli seçenekler sunar.
### GroupDocs.Parser ticari kullanım için lisans gerektiriyor mu?
 Evet, GroupDocs.Parser'ı üretim ortamlarında kullanmak için ticari lisans gereklidir. Daha fazla bilgi edin[Burada](https://purchase.groupdocs.com/buy).
### Nerede ek destek veya yardım bulabilirim?
 GroupDocs.Parser'ı ziyaret edin[forum](https://forum.groupdocs.com/c/parser/17) topluluk desteği ve rehberlik için.
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, ücretsiz deneme sürümünü şuradan edinebilirsiniz:[Burada](https://releases.groupdocs.com/) GroupDocs.Parser'ın özelliklerini keşfetmek için.