---
title: Belge Sayfası Alanından Görüntüleri Çıkarın
linktitle: Belge Sayfası Alanından Görüntüleri Çıkarın
second_title: GroupDocs.Parser .NET API'si
description: Groupdocs.Parser for .NET'i kullanarak belgelerden görüntüleri tam olarak nasıl çıkaracağınızı keşfedin. Doğru görüntü çıkarımı için belirli alanları hedeflemeyi öğrenin.
weight: 10
url: /tr/net/image-extraction/extract-images-from-document-page-area/
type: docs
---
# Belge Sayfası Alanından Görüntüleri Çıkarın

## giriiş
Bu eğitimde, bir belge sayfasının belirli alanlarından görüntüleri çıkarmak için Groupdocs.Parser for .NET'in nasıl kullanılacağını öğreneceğiz. Bu işlem, belgedeki tanımlı koordinatlara ve boyutlara göre görüntüleri hassas bir şekilde hedeflemenize ve almanıza olanak tanır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Makinenizde Visual Studio yüklü
-  .NET kitaplığı için Groupdocs.Parser. İndirebilirsin[Burada](https://releases.groupdocs.com/parser/net/)
- Görüntü çıkarma için kullanılacak örnek bir belge dosyası
## Ad Alanlarını İçe Aktarma
Groupdocs.Parser işlevlerine erişmek için C# kodunuza gerekli ad alanlarını içe aktararak başlayın.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. Adım: Ayrıştırıcı Örneğini Başlatın
 Bir örneğini oluşturun`Parser` class'a gidin ve örnek belge dosyanızın yolunu belirtin.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: Çıkarma Seçeneklerini Tanımlayın
 Görüntüleri çıkarmak istediğiniz alanı belirtmek için çıkarma seçeneklerini tanımlayın. Kullanmak`PageAreaOptions` ve sağlamak`Rectangle` sayfada istenen alanı temsil eder.
```csharp
PageAreaOptions options = new PageAreaOptions(new Rectangle(new Point(340, 150), new Size(300, 100)));
```
Bu örnekte:
- `(340, 150)`alanın sol üst köşe koordinatını temsil eder
- `300` alanın genişliği
- `100` alanın yüksekliği
## 3. Adım: Görüntüleri Çıkarın
 Çağır`GetImages` yöntemi`Parser` örneğin, tanımlanmış olanı geçerek`PageAreaOptions` . Bu, numaralandırılabilir bir koleksiyon döndürecektir.`PageImageArea` çıkarılan görüntüleri içeren nesneler.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages(options);
```
## Adım 4: Ekstraksiyon Desteğini Kontrol Edin
 Belirtilen belge için çıkarma işleminin desteklenip desteklenmediğini doğrulayın. Eğer`images` koleksiyon`null`, görüntülerin çıkarılması desteklenmez.
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## Adım 5: Çıkarılan Görüntüler Üzerinde Yineleme Yapın
 Döngü boyunca`images` Çıkarılan her görüntüyü işlemek için koleksiyon. Çıkarılan görüntüler şu şekilde temsil edilir:`PageImageArea` sayfa dizini, dikdörtgen ayrıntıları ve görüntü türü sağlayan nesneler.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
    // Her görüntüyle daha fazla işlem yapılabilir
}
```
## Çözüm
Tebrikler! Groupdocs.Parser for .NET'i kullanarak bir belgenin belirli alanlarından görüntüleri nasıl çıkaracağınızı öğrendiniz. Bu yaklaşım, tanımlanmış koordinatlara dayalı olarak hassas görüntü çıkarmaya olanak tanır ve belgelerden hedeflenen görüntü alımını mümkün kılar.

## SSS'ler
### Bu yöntemi kullanarak PDF dosyalarından resim çıkarabilir miyim?
Evet, Groupdocs.Parser, PDF dosyaları da dahil olmak üzere çeşitli belge formatlarından görüntü çıkarmayı destekler.
### Görüntü çıkarma sırasında istisnaları nasıl ele alabilirim?
Çıkarma işlemi sırasında oluşabilecek istisnaları işlemek için try-catch bloklarını kullanabilirsiniz.
### Groupdocs.Parser for .NET'in deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünden yararlanabilirsiniz[Burada](https://releases.groupdocs.com/).
### Groupdocs.Parser, şifrelenmiş veya parola korumalı belgelerden ayıklamayı destekliyor mu?
Evet, Groupdocs.Parser, uygun izinlerle parola korumalı belgelerden ayıklama işlemini gerçekleştirebilir.
### Groupdocs.Parser için nereden teknik destek alabilirim?
 Teknik destek ve tartışmalar için şu adresi ziyaret edin:[Groupdocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).