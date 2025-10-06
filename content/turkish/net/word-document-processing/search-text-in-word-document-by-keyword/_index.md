---
title: Word Belgesindeki Metni Anahtar Kelimeye Göre Arama
linktitle: Word Belgesindeki Metni Anahtar Kelimeye Göre Arama
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak Word belgelerinde nasıl metin arayacağınızı öğrenin. Belirli anahtar kelimeleri verimli bir şekilde çıkarın.
weight: 18
url: /tr/net/word-document-processing/search-text-in-word-document-by-keyword/
type: docs
---
# Word Belgesindeki Metni Anahtar Kelimeye Göre Arama

## giriiş
Bu öğreticide, C# kullanarak bir Word belgesinde belirli bir metni aramak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin Word belgeleri de dahil olmak üzere çeşitli belge biçimlerinden metin ve meta veriler çıkarmasına olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1. Geliştirme Ortamı: Visual Studio'yu veya başka bir uyumlu IDE'yi yükleyin.
2.  GroupDocs.Parser Kitaplığı: .NET için GroupDocs.Parser kitaplığını indirip yükleyin.[İnternet sitesi](https://releases.groupdocs.com/parser/net/).
3. Örnek Word Belgesi: Metin aramada kullanılacak örnek bir Word belgesi hazırlayın.

## Ad Alanlarını İçe Aktar
C# projenize gerekli ad alanlarını içe aktararak başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 İlk önce bir örneğini oluşturun`Parser` Örnek Word belgenizin yolunu ileterek sınıfa gidin.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kod buraya gelecek
}
```
## 2. Adım: Bir Anahtar Kelime Arayın
 Daha sonra şunu kullanın:`Search` yöntemi`Parser` Belge içinde belirli bir anahtar kelimeyi aramak için sınıf.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Yer değiştirmek`"keyword"` belge içinde aramak istediğiniz metni içeren
## 3. Adım: Arama Sonuçları Üzerinde Yineleme Yapın
 Arama sonuçlarını kullanarak yineleyin`foreach` her birine erişmek için döngü`SearchResult` nesne.
```csharp
foreach (SearchResult result in searchResults)
{
    //Her arama sonucunu işlemek için kod
}
```
## 4. Adım: Arama Sonucu Ayrıntılarına Erişin
 Döngü içinde, her bir arama sonucunun konumuna ve metnine aşağıdaki düğmeyi kullanarak erişebilirsiniz:`Position` Ve`Text` özellikleri`SearchResult` nesne.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Bu kod parçacığı dizini yazdırır (`Position`) ve bulunan metin (`Text`) her arama sonucu için konsola.

## Çözüm
Bu öğreticide, bir Word belgesinde belirli bir metni aramak için GroupDocs.Parser for .NET'i nasıl kullanacağınızı öğrendiniz. Bu kitaplık, çeşitli belge biçimlerinden içeriği programlı olarak çıkarmak ve değiştirmek için kullanışlı bir yol sağlar.

## SSS'ler
### GroupDocs.Parser, Word'ün yanı sıra diğer belge formatlarını da işleyebilir mi?
Evet, GroupDocs.Parser, PDF, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli formatları destekler.
### GroupDocs.Parser .NET Core ile uyumlu mu?
Evet, GroupDocs.Parser hem .NET Framework hem de .NET Core ile uyumludur.
### GroupDocs.Parser için nasıl geçici lisans edinebilirim?
 Geçici lisans talebinde bulunabilirsiniz.[GroupDocs satın alma sayfası](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser hakkında nerede ek destek bulabilirim veya soru sorabilirim?
 Ziyaret edin[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17) topluluk desteği ve tartışmalar için.
### Satın almadan önce GroupDocs.Parser'ı ücretsiz deneyebilir miyim?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[GroupDocs sürüm sayfası](https://releases.groupdocs.com/).