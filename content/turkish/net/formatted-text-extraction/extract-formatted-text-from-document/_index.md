---
title: Biçimlendirilmiş Metni Belgeden Çıkart
linktitle: Biçimlendirilmiş Metni Belgeden Çıkart
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerden biçimlendirilmiş metni nasıl çıkaracağınızı öğrenin. Uygulamalarınız için basit ve etkili metin çıkarma.
weight: 10
url: /tr/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## giriiş
Bu öğreticide, çeşitli belge türlerinden biçimlendirilmiş metni ayıklamak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin belgelerle basit ve verimli bir şekilde çalışmasına olanak tanıyan güçlü bir kitaplıktır. Bu kılavuzun sonunda, metin çıkarma yeteneklerini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebileceksiniz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Visual Studio: Sisteminizde Visual Studio'nun kurulu olduğundan emin olun.
-  .NET için GroupDocs.Parser: GroupDocs.Parser kitaplığını şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
- Belge Örnekleri: Metin çıkarma için örnek belgeler (örneğin, PDF, DOCX) hazırlayın.
## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# kodunuza ekleyin:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Bir başlatarak başlayın`Parser` örnek belgenizin yolunu içeren nesne.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Metin çıkarma kodu buraya gelecek
}
```
 Yer değiştirmek`"YourSampleFile.pdf"` belge dosyanızın yolu ile birlikte.

## Adım 2: Biçimlendirilmiş Metni Çıkarın
 İçinde`using` bloke et, kullan`GetFormattedText` Belgeden biçimlendirilmiş metni çıkarma yöntemi. kullanarak istediğiniz çıktı formatını (örn. HTML) belirtin.`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Biçimlendirilmiş metni okuyucuya çıkarın
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Ekstraksiyonun desteklenip desteklenmediğini kontrol edin
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Çıkarılan metni okuyun ve görüntüleyin
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Çözüm
Tebrikler! GroupDocs.Parser for .NET'i kullanarak belgelerden biçimlendirilmiş metni nasıl çıkaracağınızı öğrendiniz. Bu çok yönlü kitaplık, uygulamalarınızda metin işleme ve analiz olanaklarının önünü açar.

## SSS'ler
### S: GroupDocs.Parser parola korumalı belgelerden metin çıkarabilir mi?
C: Evet, GroupDocs.Parser parola korumalı belgelerden metin çıkarmayı destekler.
### S: GroupDocs.Parser hangi belge formatlarını destekliyor?
C: GroupDocs.Parser, PDF, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli formatları destekler.
### S: GroupDocs.Parser için nasıl geçici lisans alabilirim?
 C: Geçici lisansı şu adresten alabilirsiniz:[Burada](https://purchase.groupdocs.com/temporary-license/).
### S: GroupDocs.Parser belgelerden görüntü çıkarma desteği sağlıyor mu?
C: Evet, GroupDocs.Parser, metin çıkarmanın yanı sıra görüntü çıkarmayı da destekler.
### S: GroupDocs.Parser hakkında nereden ek destek bulabilirim veya soru sorabilirim?
 C: Ziyaret edin[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17)Destek ve tartışmalar için.