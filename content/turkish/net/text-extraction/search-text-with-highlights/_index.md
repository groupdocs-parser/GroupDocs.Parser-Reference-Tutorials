---
title: Vurgulanan Metinlerde Arama Yapın
linktitle: Vurgulanan Metinlerde Arama Yapın
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerde metni nasıl arayacağınızı ve vurgulayacağınızı öğrenin. Değerli içgörüleri verimli bir şekilde çıkarın.
type: docs
weight: 24
url: /tr/net/text-extraction/search-text-with-highlights/
---
## giriiş
Bu öğreticide, bir belge içindeki metni aramak ve arama sonuçlarını vurgulamak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, çeşitli belge formatlarıyla çalışmanıza ve metin, meta veriler ve daha fazlasını çıkarmanıza olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  GroupDocs.Parser for .NET: Kitaplığı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
2. IDE: .NET geliştirme için Visual Studio'yu veya tercih edilen herhangi bir IDE'yi kullanın.
3. Örnek Dosya: Metin araması için örnek bir belge (örn. PDF, DOCX) hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle .NET projenize gerekli ad alanlarını içe aktararak başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. Adım: Ayrıştırıcı Örneği Oluşturun
 Örnekleme yaparak başlayın`Parser` örnek dosyanızın yolunu içeren sınıf:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kodunuz burada
}
```
## Adım 2: Vurgu Seçeneklerini Tanımlayın
 Belirtin`HighlightOptions` arama sonuçlarının nasıl vurgulanacağını yapılandırmak için. Örneğin, 15 karakterlik bir bağlam penceresi ayarlamak:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## 3. Adım: Metin Arama
Şimdi belge içinde bir metin araması gerçekleştirin. Aramak istediğiniz anahtar kelimeyi girin (örneğin, "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## 4. Adım: Arama Sonuçlarını İşleyin
Arama sonuçlarını yineleyin ve bulunan metni vurgulamalarla birlikte görüntüleyin:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Çözüm
Bu öğreticide, belgeler içindeki metni aramak ve arama sonuçlarını vurgulamak için GroupDocs.Parser for .NET'i nasıl kullanacağınızı öğrendiniz. Bu işlevsellik, .NET uygulamalarınızdaki metin çıkarma ve analiz için son derece yararlı olabilir.

## SSS'ler
### GroupDocs.Parser çeşitli belge formatlarını işlemeye uygun mu?
Evet, GroupDocs.Parser, PDF, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Belgelerden meta verileri çıkarmak için GroupDocs.Parser'ı kullanabilir miyim?
Kesinlikle! GroupDocs.Parser, belgelerden meta verileri, metni ve yapılandırılmış verileri çıkarmanıza olanak tanır.
### GroupDocs.Parser hakkında nereden destek bulabilirim veya soru sorabilirim?
 Ziyaret edebilirsiniz[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17) Destekle ilgili tüm sorularınız için.
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, şu adrese erişebilirsiniz:[ücretsiz deneme](https://releases.groupdocs.com/) Özelliklerini değerlendirmek için GroupDocs.Parser'ın.
### GroupDocs.Parser lisansını nasıl satın alabilirim?
 adresinden lisans satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy) ve ayrıca geçici lisanslar alın[Burada](https://purchase.groupdocs.com/temporary-license/).