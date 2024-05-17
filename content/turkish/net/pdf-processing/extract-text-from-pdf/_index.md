---
title: PDF'den Metin Çıkart
linktitle: PDF'den Metin Çıkart
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak PDF belgelerinden nasıl metin ayıklayacağınızı öğrenin. Geliştiriciler için adım adım eğitim.
type: docs
weight: 14
url: /tr/net/pdf-processing/extract-text-from-pdf/
---
## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak PDF belgelerinden nasıl metin ayıklanacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin PDF, Microsoft Office ve daha fazlasını içeren çeşitli belge formatlarından metin, meta veriler ve yapılandırılmış veriler çıkarmasına olanak tanıyan güçlü bir API'dir.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Makinenizde Visual Studio yüklü.
-  .NET için GroupDocs.Parser yüklü. İndirebilirsin[Burada](https://releases.groupdocs.com/parser/net/).
- Temel C# programlama bilgisi.

## Ad Alanlarını İçe Aktar
Öncelikle C# kodunuza gerekli ad alanlarını içe aktararak başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Örnekleyin`Parser` örnek PDF dosyanızın yolunu sağlayarak sınıf:
```csharp
// Ayrıştırıcı sınıfının bir örneğini oluşturun
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: PDF'den Metin Çıkarın
 İçinde`Parser` örneğin, şunu kullanın:`GetText()` PDF'den metin çıkarma yöntemi:
```csharp
// Bir metni okuyucuya çıkarma
using (TextReader reader = parser.GetText())
{
    // Kodunuz buraya gelecek
}
```
## 3. Adım: Çıkarılan Metni Okuyun ve Yazdırın
 Şimdi, alıntılanan metni okuyun.`TextReader` ve yazdırın:
```csharp
// Çıkarılan metni yazdır
Console.WriteLine(reader.ReadToEnd());
```

## Çözüm
 Bu eğitimde, GroupDocs.Parser for .NET'i kullanarak PDF belgelerinden metin çıkarmanın temellerini ele aldık. Nasıl başlatılacağını öğrendiniz`Parser` sınıf, metni çıkarın ve çıkarılan içeriği yazdırın. Bu API, PDF ve diğer belge formatlarını programlı olarak işlemek için basit bir yol sağlar.

## SSS'ler
### GroupDocs.Parser, PDF'nin yanı sıra diğer belge formatlarıyla da uyumlu mu?
Evet, GroupDocs.Parser, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli formatları destekler.
### Lisans satın almadan önce GroupDocs.Parser'ı deneyebilir miyim?
 Evet, ücretsiz deneme sürümünü alabilirsiniz[Burada](https://releases.groupdocs.com/).
### GroupDocs.Parser belgelerini nerede bulabilirim?
 Detaylı dokümantasyon mevcut[Burada](https://reference.groupdocs.com/parser/net/).
### GroupDocs.Parser için nasıl teknik destek alabilirim?
 Destek forumunda yardım arayabilirsiniz[Burada](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser için nasıl geçici lisans edinebilirim?
 Geçici lisanslar alınabilecek[Burada](https://purchase.groupdocs.com/temporary-license/).