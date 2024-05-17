---
title: İşaretleme İçeriğini Çıkart
linktitle: İşaretleme İçeriğini Çıkart
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak Markdown içeriğini belgelerden nasıl çıkaracağınızı öğrenin. Bu eğitimde kesintisiz metin çıkarma için adım adım talimatlar verilmektedir.
type: docs
weight: 13
url: /tr/net/formatted-text-extraction/extract-markdown-content/
---
## giriiş
Bu öğreticide, Markdown içeriğini belgelerden çıkarmak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin çeşitli dosya formatlarındaki metinleri sorunsuz bir şekilde ayrıştırmasına ve ayıklamasına olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- Visual Studio: Visual Studio'yu sisteminize yükleyin.
-  .NET için GroupDocs.Parser: GroupDocs.Parser'ı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
- Temel C# anlayışı: C# programlama diline aşinalık.

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# projenize aktarmanız gerekir:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Örnekleyin`Parser` örnek dosyanızın yolunu içeren sınıf:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Kod buraya gelecek...
}
```
## Adım 2: Markdown Formatlı Metni Çıkarın
 İçinde`using`engellemek, kullanmak`GetFormattedText` Biçimlendirilmiş metni Markdown olarak çıkarma yöntemi:
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Markdown)))
{
    // Kod buraya gelecek...
}
```
## 3. Adım: Çıkarılan İçeriği Okuyun ve Çıktısını Alın
 Çıkarılan Markdown içeriğini okuyun`TextReader`:
```csharp
string markdownContent = reader == null ? "Formatted text extraction isn't supported" : reader.ReadToEnd();
Console.WriteLine(markdownContent);
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak Markdown içeriğini belgelerden nasıl çıkaracağımızı öğrendik. Bu güçlü kitaplık, metin ayrıştırma ve çıkarma işlemini basitleştirerek geliştiricilerin çeşitli dosya formatlarıyla verimli bir şekilde çalışmasına olanak tanır.
## SSS'ler
### GroupDocs.Parser farklı dosya formatlarını işleyebilir mi?
Evet, GroupDocs.Parser, DOCX, PDF, PPTX, XLSX ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### GroupDocs.Parser .NET Core ile uyumlu mu?
Evet, GroupDocs.Parser hem .NET Framework'ü hem de .NET Core'u destekler.
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Geçici lisans alabilirsiniz[Burada](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser geliştiricilere destek sağlıyor mu?
 Evet, şu adresten geliştirici desteği alabilirsiniz:[GroupDocs Forumu](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser lisansını nereden satın alabilirim?
 Lisans satın alabilirsiniz[Burada](https://purchase.groupdocs.com/buy).