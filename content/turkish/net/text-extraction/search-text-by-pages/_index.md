---
title: Metinleri Sayfalara Göre Ara
linktitle: Metinleri Sayfalara Göre Ara
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak sayfalara göre metin aramayı öğrenin. .NET uygulamalarınızdaki belgelerden belirli içerikleri verimli bir şekilde çıkarın.
type: docs
weight: 22
url: /tr/net/text-extraction/search-text-by-pages/
---
## giriiş
.NET geliştirme dünyasında, belgelerden metni verimli bir şekilde ayrıştırmak ve çıkarmak çok önemli bir görevdir. GroupDocs.Parser for .NET, çeşitli belge formatlarıyla çalışmak için güçlü yetenekler sunarak geliştiricilerin belirli içeriği sorunsuz bir şekilde aramasına ve çıkarmasına olanak tanır. Bu eğitim, .NET uygulamalarınızdaki sayfalara göre metin aramak için GroupDocs.Parser'dan yararlanma sürecinde size rehberlik edecektir.
## Önkoşullar
Bu eğitime dalmadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- C# ve .NET çerçevesine ilişkin temel anlayış
- Sisteminizde Visual Studio yüklü
-  .NET kitaplığı için GroupDocs.Parser yüklü (Şuradan indirin:[Burada](https://releases.groupdocs.com/parser/net/))
- Arama işlevselliğini test etmek için örnek dosya(lar)
## Ad Alanlarını İçe Aktar
GroupDocs.Parser işlevlerine erişmek için öncelikle projenize gerekli ad alanlarını ekleyin:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Örnekleme yaparak başlayın`Parser` örnek dosyanızın yolunu içeren sınıf:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: Sayfa Numaralarıyla Metin Arama
 Kullanın`Search` Belgedeki belirli anahtar kelimeleri sayfa numaralarıyla birlikte arama yöntemi:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## 3. Adım: Arama Desteğini Kontrol Edin
Belge türü için arama işleminin desteklenip desteklenmediğini doğrulayın:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## 4. Adım: Arama Sonuçları Üzerinde Yineleme Yapın
Dizine alınmış konumları, sayfa numaralarını ve bulunan metni almak için arama sonuçlarını yineleyin:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak sayfalara göre metin aramasının nasıl uygulanacağını araştırdık. Bu adımları izleyerek belge ayrıştırma ve arama işlevlerini .NET uygulamalarınıza verimli bir şekilde entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser çeşitli belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Parser, DOCX, PDF, XLSX, PPTX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Parser'ı kullanarak belgelerden görselleri ve meta verileri çıkarabilir miyim?
GroupDocs.Parser kesinlikle belgelerden görsellerin, meta verilerin ve metnin çıkarılmasına olanak tanır.
### GroupDocs.Parser'a ilişkin ayrıntılı belgeleri nerede bulabilirim?
 Dokümantasyona ulaşabilirsiniz[Burada](https://reference.groupdocs.com/parser/net/).
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Geçici lisans talebinde bulunabilirsiniz[Burada](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser ile ilgili nereden destek veya yardım alabilirim?
 Destek ve tartışmalar için GroupDocs.Parser forumunu ziyaret edin[Burada](https://forum.groupdocs.com/c/parser/17).