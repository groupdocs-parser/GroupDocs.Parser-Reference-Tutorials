---
title: Düz Metni Çıkart
linktitle: Düz Metni Çıkart
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerden düz metin çıkarmayı öğrenin. Metin çıkarmayı uygulamalarınıza entegre etmek için kolay adımlar.
weight: 14
url: /tr/net/formatted-text-extraction/extract-plain-text/
---

# Düz Metni Çıkart

## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak çeşitli belge formatlarından düz metinlerin nasıl çıkarılacağını inceleyeceğiz. GroupDocs.Parser, geliştiricilerin belgelerle sorunsuz bir şekilde çalışmasına, metin ve meta verileri verimli bir şekilde ayıklamasına olanak tanıyan güçlü bir kitaplıktır. Bu kılavuz, bu kitaplığı .NET uygulamalarınıza entegre etmek ve kullanmak için gerekli adımlarda size yol gösterecektir.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1. Visual Studio: Visual Studio'yu geliştirme makinenize yükleyin.
2.  GroupDocs.Parser Kitaplığı: GroupDocs.Parser for .NET'i şu adresten indirip yükleyin:[indirme sayfası](https://releases.groupdocs.com/parser/net/).
3. Örnek Belgeler: Metin çıkarma için örnek belgeler (örneğin, DOCX, PDF, TXT) hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle GroupDocs.Parser'ın işlevlerine erişmek için C# projenize gerekli ad alanlarını ekleyin:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 1. Adım: Ayrıştırıcıyı Başlatın
 Bir örneğini oluşturun`Parser` örnek belgenizin yolunu belirterek sınıf.
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    // Metin çıkarma kodu buraya gelir
}
```
## Adım 2: Biçimlendirilmiş Metni Çıkarın
 İçinde`using` bloğu`Parser`kullanarak biçimlendirilmiş metni çıkarın.`GetFormattedText` ile yöntem`PlainText` modu.
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    // Çıkarılan metni okumak ve işlemek için kod
}
```
## 3. Adım: Çıkarılan Metni Okuyun
 Kullan`TextReader` çıkarılan düz metni okumak ve çıktısını almak için örnek.
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak belgelerden düz metin ayıklamanın temellerini ele aldık. Bu adımları izleyerek metin çıkarma yeteneklerini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser birden çok belge biçimiyle uyumlu mu?
Evet, GroupDocs.Parser, DOCX, PDF, TXT ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Parser'ı kullanarak metinle birlikte meta verileri çıkarabilir miyim?
Kesinlikle, GroupDocs.Parser hem metin içeriğinin hem de yazar, oluşturulma tarihi vb. gibi meta verilerin çıkarılmasına izin verir.
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, GroupDocs.Parser'ın ücretsiz deneme sürümüne erişebilirsiniz[Burada](https://releases.groupdocs.com/).
### GroupDocs.Parser için teknik desteği nerede bulabilirim?
 Teknik yardım için GroupDocs.Parser'ı ziyaret edin.[forum](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Geçici bir lisans almak için GroupDocs.Parser'ı ziyaret edin.[geçici lisans sayfası](https://purchase.groupdocs.com/temporary-license/).