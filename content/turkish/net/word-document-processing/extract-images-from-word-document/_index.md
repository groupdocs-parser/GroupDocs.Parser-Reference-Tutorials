---
title: Word Belgesinden Görüntüleri Çıkarma
linktitle: Word Belgesinden Görüntüleri Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak bir Word belgesinden görüntüleri nasıl çıkaracağınızı öğrenin. Bu öğretici, görüntüyü .NET'inize entegre etmek için adım adım rehberlik sağlar.
weight: 11
url: /tr/net/word-document-processing/extract-images-from-word-document/
type: docs
---
# Word Belgesinden Görüntüleri Çıkarma

## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir Word belgesinden görüntülerin nasıl çıkarılacağını öğreneceksiniz. GroupDocs.Parser, Word (DOCX) dahil olmak üzere çeşitli belge biçimlerinden metin, meta veriler, görüntüler ve daha fazlasını ayrıştırmanıza ve çıkarmanıza olanak tanıyan güçlü bir .NET kitaplığıdır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların ayarlandığından emin olun:
- Makinenizde Visual Studio yüklü.
- Temel C# programlama bilgisi.
- .NET kitaplığı için GroupDocs.Parser yüklendi. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/parser/net/).
## Ad Alanlarını İçe Aktar
GroupDocs.Parser işlevlerini kullanmak için öncelikle C# projenize gerekli ad alanlarını içe aktarmanız gerekir:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Şimdi bir Word belgesinden görsel çıkarma işlemini basit adımlara ayıralım:
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Bir örneğini oluşturarak başlayacaksınız`Parser`sınıfı, giriş olarak Word belgenizin yolunu sağlar.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Görüntü çıkarma kodu buraya gelecek
}
```
## Adım 2: Word Belgesinden Görüntüleri Çıkarın
 Daha sonra şunu kullanın:`GetImages()` yöntemi`Parser` Belgeden görüntüleri çıkarmak için nesne.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3. Adım: Görüntü Kaydetme Seçeneklerini Tanımlayın
Çıkarılan görüntüleri kaydetme seçeneklerini belirtin. Örneğin, görüntü formatını (ör. PNG) seçebilir ve diğer ayarları yapılandırabilirsiniz.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Adım 4: Çıkarılan Görüntüler Üzerinde Yineleyin ve Kaydedin
Çıkarılan her görüntüyü yineleyin ve belirtilen seçenekleri kullanarak bir dosyaya kaydedin.
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
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir Word belgesinden görüntüleri nasıl çıkaracağınızı öğrendiniz. Bu adımları izleyerek belge ayrıştırma ve görüntü çıkarma yeteneklerini .NET uygulamalarınıza kolayca entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser, Word'ün yanı sıra diğer belge formatlarından da görüntü çıkarabilir mi?
Evet, GroupDocs.Parser; PDF, PowerPoint, Excel ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Aşağıdaki adresten test amaçlı geçici bir lisans alabilirsiniz:[Burada](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser for .NET hakkında daha fazla belgeyi nerede bulabilirim?
 Tüm belgelere başvurabilirsiniz[Burada](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, GroupDocs.Parser'ın özelliklerini ücretsiz deneme sürümüyle keşfedebilirsiniz[Burada](https://releases.groupdocs.com/).
### GroupDocs.Parser ile ilgili nasıl destek alabilirim veya soru sorabilirim?
 Sorularınızı şu adrese yazabilirsiniz:[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).