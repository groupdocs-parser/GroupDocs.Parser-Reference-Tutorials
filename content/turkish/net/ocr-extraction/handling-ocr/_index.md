---
title: OCR'yi yönetme
linktitle: OCR'yi yönetme
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak OCR'yi nasıl işleyeceğinizi öğrenin. Görüntülerden ve taranan belgelerden metni verimli bir şekilde çıkarın.
weight: 11
url: /tr/net/ocr-extraction/handling-ocr/
type: docs
---
# OCR'yi yönetme

## giriiş
Bu öğreticide, Optik Karakter Tanıma (OCR) görevlerini verimli bir şekilde gerçekleştirmek için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. Bu kitaplık, belgelerden metin ayıklamak için güçlü araçlar sağlar ve OCR ile görüntülerden veya taranmış belgelerden bile metin ayıklayabilirsiniz. Süreci adım adım inceleyelim.
## Önkoşullar
Başlamadan önce aşağıdaki kurulumlara sahip olduğunuzdan emin olun:
- .NET Kitaplığı için GroupDocs.Parser: Kitaplığı şuradan indirin:[Burada](https://releases.groupdocs.com/parser/net/).
- Örnek Dosyanız: İçinden metin çıkarmak istediğiniz örnek bir dosya (belge veya resim) hazırlayın.
- C# ve .NET ortamına ilişkin temel bilgiler.

## Ad Alanlarını İçe Aktar
Öncelikle .NET uygulamanızda GroupDocs.Parser işlevlerini kullanmak için gerekli ad alanlarını içe aktarmanız gerekir.
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1. Adım: OCR Bağlayıcıyla Ayrıştırıcı Ayarları Oluşturun
 Başlat`ParserSettings` OCR konektörüyle sınıf. Örneğin Aspose OCR'ı şirket içinde kullanmak.
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 2. Adım: OCR Seçeneklerini Yapılandırın
 Bir kurulum yapın`OcrEventHandler` OCR işlemi sırasında uyarıları işlemek için.
```csharp
OcrEventHandler handler = new OcrEventHandler();
OcrOptions ocrOptions = new OcrOptions(handler);
```
## 3. Adım: Metin Çıkarma Seçeneklerini Yapılandırın
 Yaratmak`TextOptions` OCR tabanlı metin ayıklamayı etkinleştirmek için.
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Adım 4: OCR kullanarak Metni Çıkarın
 Örnekleyin`Parser` ayarlarla sınıflayın ve OCR kullanarak metni çıkarın.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    using (TextReader reader = parser.GetText(options))
    {
        if (reader == null)
        {
            Console.WriteLine("Text extraction isn't supported.");
        }
        else
        {
            Console.WriteLine(reader.ReadToEnd());
        }
    }
    if (handler.HasWarnings)
    {
        Console.WriteLine("The following warnings occurred during text recognition:");
        foreach (string w in handler.Warnings)
        {
            Console.WriteLine("\t* " + w);
        }
    }
    else
    {
        Console.WriteLine("Text recognition was performed without any warnings.");
    }
}
```

## Çözüm
Bu adımları izleyerek, uygulamalarınızda OCR görevlerini etkili bir şekilde gerçekleştirmek için GroupDocs.Parser for .NET'ten yararlanabilirsiniz. Bu kütüphanenin sunduğu güçlü özellikler sayesinde resimlerden veya taranmış belgelerden metin çıkarmak kusursuz hale gelir.

## SSS'ler
### GroupDocs.Parser for .NET farklı dosya formatlarıyla uyumlu mu?
Evet, GroupDocs.Parser, PDF, DOCX, PPTX, XLSX, resimler (JPEG, PNG, TIFF) ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### GroupDocs.Parser for .NET'i ticari projelerimde kullanabilir miyim?
Evet, lisans satın aldıktan sonra GroupDocs.Parser for .NET'i ticari uygulamalarınıza entegre edebilirsiniz.
### GroupDocs.Parser şifrelenmiş veya parola korumalı dosyaları işliyor mu?
GroupDocs.Parser, parola korumalı PDF belgelerindeki metni ayrıştırabilir ve çıkarabilir.
### GroupDocs.Parser for .NET'in deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Parser for .NET ile ilgili desteği nerede bulabilirim veya soru sorabilirim?
 Ziyaret edebilirsiniz[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17) Herhangi bir destek sorgusu veya tartışması için.