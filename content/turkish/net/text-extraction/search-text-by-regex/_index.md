---
title: Normal İfadeye Göre Metin Arama (Regex)
linktitle: Normal İfadeye Göre Metin Arama (Regex)
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerde normal ifadeleri kullanarak nasıl metin arayacağınızı öğrenin. Belirli içerikleri zahmetsizce çıkarın.
weight: 23
url: /tr/net/text-extraction/search-text-by-regex/
---

# Normal İfadeye Göre Metin Arama (Regex)

## giriiş
Bu öğreticide, belgeler içindeki normal ifadeye (Regex) göre metin aramak için GroupDocs.Parser for .NET'i kullanmayı ayrıntılı olarak ele alacağız. GroupDocs.Parser, geliştiricilerin PDF, DOCX, XLSX ve daha fazlası gibi çeşitli dosya formatlarından metin ve meta veriler çıkarmasına olanak tanıyan güçlü bir kitaplıktır. Düzenli ifadeler kullanarak metin aramak, özellikle belgelerdeki kalıpları veya belirli içerikleri verimli bir şekilde bulmak için kullanışlıdır.
## Önkoşullar
Bu eğitime dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. Visual Studio: .NET geliştirme için Visual Studio IDE'yi yükleyin.
2.  .NET için GroupDocs.Parser: .NET için GroupDocs.Parser'ı şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
3. Örnek Dosya: Arama işlevselliğini test etmek için örnek bir belge (PDF, DOCX vb.) hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle C# kodunuza gerekli ad alanlarını ekleyerek başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Örnekleyin`Parser` örnek dosyanızın yolunu sağlayarak class:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kod buraya gelecek
}
```
 Yer değiştirmek`"YourSampleFile.pdf"` gerçek dosyanızın yolu ile birlikte.
## 2. Adım: Normal İfade Kullanarak Arama Yapın
Aramayı normal ifade modelini kullanarak tanımlayın ve yürütün. Örneğin, belgedeki sayısal dizileri (örneğin tamsayılar) bulmak için:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 Bu örnekte,`[0-9]+` bir veya daha fazla rakamla eşleşen normal ifade modelidir.
## 3. Adım: Arama Desteğini Kontrol Edin
Belge türü için arama işleminin desteklenip desteklenmediğini doğrulayın:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## 4. Adım: Arama Sonuçları Üzerinde Yineleme Yapın
Arama sonuçlarını yineleyin ve her eşleşmeyi işleyin:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Bu döngü, belgede bulunan konumu ve eşleşen metni yazdıracaktır.

## Çözüm
Sonuç olarak, GroupDocs.Parser for .NET'ten yararlanmak, çeşitli belge formatlarında düzenli ifadeler kullanılarak verimli metin aramasına olanak tanır. Geliştiriciler bu kılavuzu izleyerek belge ayrıştırmayı ve normal ifade tabanlı metin çıkarmayı .NET uygulamalarına sorunsuz bir şekilde entegre edebilirler.

## SSS'ler
### GroupDocs.Parser şifrelenmiş belgelerde arama yapabilir mi?
Hayır, GroupDocs.Parser şifrelenmiş veya parola korumalı belgelerde arama yapamaz.
### GroupDocs.Parser OCR'yi (Optik Karakter Tanıma) destekliyor mu?
Hayır, GroupDocs.Parser OCR gerçekleştirmez. Belgenin iç yapısından metin çıkarmaya dayanır.
### Düzenli ifadeler kullanarak karmaşık kalıpları arayabilir miyim?
Evet, GroupDocs.Parser tam donanımlı düzenli ifadeleri destekleyerek belgeler içinde karmaşık desen eşleşmesine olanak tanır.
### Metin çıkarma için hangi belge formatları desteklenir?
GroupDocs.Parser, PDF, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli formatları destekler.
### GroupDocs.Parser .NET Core ile uyumlu mu?
Evet, GroupDocs.Parser, platformlar arası geliştirme için .NET Core ile uyumludur.