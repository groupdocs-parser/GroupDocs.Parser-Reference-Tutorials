---
title: Excel Belgesindeki Metni Normal İfadeyle Arama
linktitle: Excel Belgesindeki Metni Normal İfadeyle Arama
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET ile normal ifadeleri kullanarak Excel belgelerinde metin aramayı öğrenin. Gelişmiş metin aramalarını verimli bir şekilde gerçekleştirin.
weight: 17
url: /tr/net/excel-document-processing/search-text-in-excel-document-by-regular-expression/
---

# Excel Belgesindeki Metni Normal İfadeyle Arama

## giriiş
Bu öğreticide, düzenli ifadeler kullanarak Excel belgelerinde belirli metin kalıplarını aramak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin Excel gibi elektronik tablolar da dahil olmak üzere çeşitli belge formatlarından metin ve meta veriler çıkarmasına olanak tanıyan güçlü bir kitaplıktır. Düzenli ifadelerden yararlanarak gelişmiş metin aramalarını verimli bir şekilde gerçekleştirebiliriz.
## Önkoşullar
Başlamadan önce aşağıdaki kuruluma sahip olduğunuzdan emin olun:
1. Visual Studio: .NET geliştirme için Visual Studio'yu veya başka bir uyumlu IDE'yi yükleyin.
2.  GroupDocs.Parser for .NET: Kitaplığı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
3. Örnek Excel Dosyası: Aramak istediğiniz metni içeren örnek bir Excel dosyası hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle projenizde GroupDocs.Parser'ı kullanmak için gerekli ad alanlarını ekleyin:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Bir örneğini oluşturarak başlayın`Parser` sınıf, Excel belgenizin yolunu parametre olarak ileterek.
```csharp
// Ayrıştırıcı sınıfının bir örneğini oluşturun
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Kod burada devam ediyor...
}
```
## 2. Adım: Normal İfade Araması Gerçekleştirin
 İçinde`using` blok, normal ifade modelini kullanarak bir metin araması gerçekleştirin.
```csharp
//Büyük/küçük harf eşleştirmeli normal ifadeyle arama yapın
IEnumerable<SearchResult> searchResults = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
```
- Regex Desen Açıklaması:
  - `\\sthe\\s`: Bu normal ifade modeli, boşluklarla çevrelenmiş "the" (büyük/küçük harfe duyarlı) kelimesini arar.
## 3. Adım: Arama Sonuçları Üzerinde Yineleme Yapın
Daha sonra, eşleşen her bir duruma erişmek için arama sonuçlarını yineleyin.
```csharp
// Arama sonuçları üzerinde yineleme
foreach (SearchResult result in searchResults)
{
    // Konumu ve bulunan metni yazdırın
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
- Çıktı:
  - Bu döngü, belirtilen metin modelinin her örneğini belge içindeki konumuyla birlikte yazdıracaktır.

## Çözüm
Bu öğreticide, Excel belgelerinde normal ifade araması gerçekleştirmek için GroupDocs.Parser for .NET'in nasıl kullanılacağını öğrendik. Bu adımları izleyerek gelişmiş metin arama yeteneklerini .NET uygulamalarınıza verimli bir şekilde entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser, Excel'in yanı sıra diğer belge formatlarından da veri çıkarabilir mi?
Evet, GroupDocs.Parser, Word, PDF, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Parser hakkında nereden destek bulabilirim veya soru sorabilirim?
 Ziyaret edin[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17)Destek ve tartışmalar için.
### GroupDocs.Parser lisansını nasıl satın alabilirim?
 adresinden lisans satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy).
### Test amaçlı geçici lisans alabilir miyim?
 Evet, geçici lisans alabilirsiniz[Burada](https://purchase.groupdocs.com/temporary-license/).