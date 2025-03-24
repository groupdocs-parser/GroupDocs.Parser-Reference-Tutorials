---
title: Metni Anahtar Kelimeye Göre Ara
linktitle: Metni Anahtar Kelimeye Göre Ara
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerde anahtar kelimeye göre metin aramayı öğrenin. İlgili içeriği kolaylıkla ve verimli bir şekilde çıkarın.
weight: 21
url: /tr/net/text-extraction/search-text-by-keyword/
---
## giriiş
Bu öğreticide, belgeler içindeki metni anahtar kelimeye göre aramak için GroupDocs.Parser for .NET'i kullanmayı ayrıntılı olarak ele alacağız. GroupDocs.Parser, geliştiricilerin PDF'ler, Microsoft Office belgeleri ve daha fazlası gibi çeşitli dosya biçimlerinden metin, meta veriler ve diğer bilgileri ayıklamasına olanak tanıyan güçlü bir kitaplıktır. Bu belgelerde belirli anahtar sözcüklerin aranması, büyük hacimli metinsel verilerle uğraşan uygulamalar için önemli olabilir.
## Önkoşullar
Başlamadan önce aşağıdaki kurulumlara sahip olduğunuzdan emin olun:
1. Geliştirme Ortamı: Visual Studio veya tercih edilen herhangi bir .NET IDE.
2.  .NET için GroupDocs.Parser: Kitaplığı şuradan indirin:[Burada](https://releases.groupdocs.com/parser/net/).
3. Örnek Dosyalara Erişim: Anahtar kelime arama işlevini test etmek için örnek bir dosya (örneğin, PDF, DOCX) hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle projenize gerekli ad alanlarını eklemeniz gerekir.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Adım 1: Ayrıştırıcı Sınıfını Örneklendirin
 Bir örneğini oluşturarak başlayın`Parser` class'a gidin ve örnek dosyanızın yolunu belirtin.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Bir anahtar kelime arayın
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Arama sonuçları üzerinde yineleme
    foreach (SearchResult result in searchResults)
    {
        //Dizini ve bulunan metni yazdırın
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## 2. Adım: Bir Anahtar Kelime Arayın
 İçinde`using` engelle, ara`Search` konusundaki yöntem`parser` İstenilen anahtar kelimeyi argüman olarak ileten nesne.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Yer değiştirmek`"test"` belgede aramak istediğiniz anahtar kelimeyle.
## 3. Adım: Arama Sonuçları Üzerinde Yineleyin
 Daha sonra, elde edilen arama sonuçları üzerinde yineleyin.`Search` kullanarak bir yöntem`foreach` döngü.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Her biri için`SearchResult` nesne`result` , ona erişebilirsiniz`Position` (indeks) ve`Text` (bulunan metin).

## Çözüm
 Bu eğitimde, belgeler içindeki metni anahtar kelimeye göre zahmetsizce aramak için GroupDocs.Parser for .NET'in nasıl kullanılacağını araştırdık. Faydalanmak`Search` yöntemi`Parser` class, belirli arama terimlerine dayalı olarak ilgili metin parçacıklarının etkili bir şekilde alınmasına olanak tanır.

## SSS'ler
### GroupDocs.Parser çeşitli belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Parser, PDF, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### GroupDocs.Parser'ı kullanarak gelişmiş metin çıkarma işlemlerini gerçekleştirebilir miyim?
Kesinlikle! GroupDocs.Parser, metin aramanın yanı sıra meta veri çıkarma, yapılandırılmış metin çıkarma ve daha fazlasını sağlar.
### GroupDocs.Parser'a ilişkin ayrıntılı belgeleri nerede bulabilirim?
Belgelerin tamamını inceleyin[Burada](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser ile ilgili sorgularla ilgili nasıl destek veya yardım alabilirim?
 Destek ve tartışmalar için GroupDocs forumunu ziyaret edin[Burada](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser'ı satın almadan önce değerlendirebileceğiniz bir deneme sürümü var mı?
 Evet, ücretsiz deneme sürümüne erişebilirsiniz[Burada](https://releases.groupdocs.com/).