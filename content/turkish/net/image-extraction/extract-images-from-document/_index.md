---
title: Belgeden Görüntüleri Çıkartın
linktitle: Belgeden Görüntüleri Çıkartın
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerdeki görüntüleri zahmetsizce çıkarın. Belge işleme yetenekleriniz ve görüntü çıkarma görevlerinizi verimli bir şekilde kolaylaştırın.
weight: 11
url: /tr/net/image-extraction/extract-images-from-document/
type: docs
---
# Belgeden Görüntüleri Çıkartın

## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak belgelerden görüntülerin nasıl çıkarılacağını inceleyeceğiz. GroupDocs.Parser, geliştiricilerin çeşitli belge formatlarından metin, meta veriler, resimler ve daha fazlasını çıkarmasına olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların ayarlandığından emin olun:
- Visual Studio: Visual Studio'yu makinenize yükleyin.
-  .NET için GroupDocs.Parser: GroupDocs.Parser'ı şu adresten indirip yükleyin:[indirme sayfası](https://releases.groupdocs.com/parser/net/).
- Örnek Belge: İçinden görsel çıkarmak istediğiniz örnek bir belge (PDF, DOCX vb.) hazırlayın.

## Ad Alanlarını İçe Aktar
C# projenize gerekli ad alanlarını içe aktararak başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 İlk önce bir örneğini oluşturun`Parser` örnek belgenizin yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kodunuz buraya gelecek
}
```
 Yer değiştirmek`"YourSampleFile.pdf"` belge dosyanızın yolu ile birlikte.
## Adım 2: Belgeden Görüntüleri Çıkarın
 Daha sonra, kullanarak belgeden görüntüleri çıkarın.`GetImages()` yöntem.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
`GetImages()` yöntem bir koleksiyon döndürür`PageImageArea` belgede bulunan görüntüleri temsil eden nesneler.
## 3. Adım: Görüntü Çıkarma Desteğini Kontrol Edin
Görüntüler üzerinde yineleme yapmadan önce belge için görüntü çıkarmanın desteklenip desteklenmediğini kontrol edin.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Bu adım, belgenin çıkarılabilir görüntüler içermesini sağlar.
## Adım 4: Çıkarılan Görüntüler Üzerinde Yineleme Yapın
Şimdi, her bir görsel hakkında sayfa dizini, dikdörtgen koordinatları ve görsel türü gibi ayrıntılı bilgilere erişmek için çıkarılan görseller üzerinde yineleme yapın.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Bu döngü, çıkarılan her görüntüyle ilgili, konumu ve türü de dahil olmak üzere bilgileri yazdırır.

## Çözüm
Bu öğreticide, belgelerden programlı olarak görüntü ayıklamak için GroupDocs.Parser for .NET'in nasıl kullanılacağını öğrendik. Bu adımları izleyerek belge görüntüsü çıkarma işlevini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser tüm belge formatlarından görüntüleri çıkarabilir mi?
GroupDocs.Parser, PDF, DOCX, XLSX ve daha fazlası dahil olmak üzere çeşitli formatlardan görüntülerin çıkarılmasını destekler.
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, GroupDocs.Parser'ın ücretsiz deneme sürümüne şu adresten erişebilirsiniz:[İnternet sitesi](https://releases.groupdocs.com/).
### GroupDocs.Parser belgelerini nerede bulabilirim?
 GroupDocs.Parser için ayrıntılı belgeler bulunabilir[Burada](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Geçici lisansı adresinden alabilirsiniz.[geçici lisans sayfası](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser için nereden destek alabilirim?
 Teknik destek ve yardım için şu adresi ziyaret edin:[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).