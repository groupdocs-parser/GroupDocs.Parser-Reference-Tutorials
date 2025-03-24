---
title: Görüntüleri Dosyalara Çıkartın
linktitle: Görüntüleri Dosyalara Çıkartın
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak PDF ve DOCX gibi çeşitli belge türlerinden görüntüleri zahmetsizce çıkarın. Belge ayrıştırma görevlerinizi basitleştirin.
weight: 13
url: /tr/net/image-extraction/extract-images-to-files/
---

# Görüntüleri Dosyalara Çıkartın

## giriiş
Bu öğreticide, PDF, Word, Excel ve PowerPoint gibi çeşitli belge biçimlerinden görüntüleri ayıklamak için GroupDocs.Parser for .NET'i nasıl kullanacağınızı öğreneceksiniz. GroupDocs.Parser, geliştiricilerin belgelerden metni, meta verileri, görüntüleri ve daha fazlasını basit bir şekilde ayrıştırmasına ve ayıklamasına olanak tanıyan güçlü bir kitaplıktır. Bu kılavuz, C# kullanarak görüntüleri çıkarma ve bunları ayrı dosyalar olarak kaydetme sürecinde size yol gösterecektir.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
1. Visual Studio: Sisteminizde Visual Studio'nun kurulu olduğundan emin olun.
2.  .NET için GroupDocs.Parser: .NET için GroupDocs.Parser'ı şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
3. Örnek Belge: İçinden resim çıkarmak istediğiniz örnek bir belge (örneğin, PDF, DOCX, XLSX) hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# kodunuza ekleyin:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. Adım: Ayrıştırıcı Örneği Oluşturun
 Örnekleyin`Parser` örnek belgenizin yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kod buraya gelecek
}
```
## Adım 2: Belgeden Görüntüleri Çıkarın
 Kullan`GetImages()` yöntemi`Parser` Belgeden görüntüleri almak için nesne.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3. Adım: Görüntü Çıkarma Desteğini Kontrol Edin
Belgenin görüntü çıkarmayı destekleyip desteklemediğini doğrulayın.
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## 4. Adım: Görüntü Kaydetme Seçeneklerini Ayarlayın
Formatı belirtin (`ImageFormat`) ayıklanan görüntüleri (ör. PNG) kaydetmek istediğiniz yere tıklayın.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Adım 5: Görüntüleri Yineleyin ve Kaydedin
Çıkarılan görüntüler arasında dolaşın ve her görüntüyü bir dosyaya kaydedin.
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
Bu öğreticide, C# kullanarak belgelerden görüntüleri ayıklamak için GroupDocs.Parser for .NET'i nasıl kullanacağınızı öğrendiniz. Bu güçlü kitaplık, çeşitli dosya biçimlerinden veri ayrıştırma ve çıkarma işlemini basitleştirerek onu .NET uygulamalarındaki belge işleme görevleri için önemli bir araç haline getirir.

## SSS'ler
### Parola korumalı belgelerden görüntüleri çıkarabilir miyim?
Evet, GroupDocs.Parser, ayrıştırma sırasında doğru parolayı girmeniz durumunda parola korumalı belgelerden görüntülerin çıkarılmasını destekler.
### Görüntü çıkarma için hangi belge formatları desteklenir?
GroupDocs.Parser, PDF, DOCX, XLSX, PPTX, EPUB ve daha fazlasını içeren çok çeşitli formatları destekler.
### Görüntü çıkarma sırasında istisnaları nasıl ele alabilirim?
Görüntü çıkarma sırasında oluşabilecek istisnaları yakalamak ve yönetmek için kodunuza hata işleme uygulayabilirsiniz.
### GroupDocs.Parser, belgelerin toplu işlenmesi için uygun mudur?
Evet, birden fazla belgeyi toplu olarak işlemek, görüntüleri ve diğer verileri verimli bir şekilde çıkarmak için GroupDocs.Parser'ı kullanabilirsiniz.
### GroupDocs.Parser, taranan belgeler için OCR yetenekleri sağlıyor mu?
GroupDocs.Parser şu anda OCR'yi (Optik Karakter Tanıma) desteklememektedir ancak yapılandırılmış verileri belgelerden ayrıştırmada mükemmeldir.