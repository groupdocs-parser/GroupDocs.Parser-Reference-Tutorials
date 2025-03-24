---
title: Belgeyi Yerel Diskten Yükle
linktitle: Belgeyi Yerel Diskten Yükle
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak çeşitli belge biçimlerinden nasıl metin ayıklayacağınızı öğrenin. C# ile kolay ve etkili metin çıkarma.
weight: 11
url: /tr/net/document-loading/load-document-from-local-disk/
---
## giriiş
Bu öğreticide, belgelerden metin ayıklamak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin çeşitli belge formatlarını ayrıştırmasına ve metin içeriğini programlı olarak ayıklamasına olanak tanıyan güçlü bir kitaplıktır. Bu kütüphaneyi kullanarak metin çıkarmaya başlamak için gerekli adımları ele alacağız.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların kurulu olduğundan emin olun:
- Sisteminizde Visual Studio yüklü.
- Temel C# programlama dili bilgisi.
-  .NET kitaplığı için GroupDocs.Parser yüklü (indir[Burada](https://releases.groupdocs.com/parser/net/)).

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# projenize aktarmanız gerekir:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## 1. Adım: Belgeyi Yerel Diskten Yükleyin
 Yerel diskinizden bir belge yükleyerek başlayın. Yer değiştirmek`"Your Sample File"` hedef belgenizin yolu ile.
```csharp
// FilePath'i ayarlayın
string filePath = "Your Sample File";
// filePath ile Ayrıştırıcı sınıfının bir örneğini oluşturun
using (Parser parser = new Parser(filePath))
{
    // Metni okuyucuya çıkarın
    using (TextReader reader = parser.GetText())
    {
        //Belgeden çıkarılan metni yazdırın
        // Metin çıkarma desteklenmiyorsa okuyucu boş olacaktır
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Adımların Açıklaması
1. Dosya Yolunu Ayarlama: Metni çıkarmak istediğiniz belgenin yolunu belirterek başlayın (`filePath` değişken).
2.  Ayrıştırıcı Örneği Oluşturma:`Parser` sınıfı geçerek`filePath`.
3.  Metin Çıkarma:`GetText()` yöntemi`Parser` elde etmek için örnek`TextReader` belgeden çıkarılan metni içeren nesne.
4.  Çıkarılan Metni Okumak:`ReadToEnd()` yöntemi`TextReader` Belgeden çıkarılan tüm metin içeriğini almak için.
5.  Desteklenmeyen Formatların İşlenmesi: Belge formatı metin çıkarmayı desteklemiyorsa,`reader` nesne olacak`null`ve bu senaryoyu buna göre halledebilirsiniz.

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir belgeden metin ayıklamak için ilk adımları ele aldık. Bu kitaplık, belge ayrıştırmaya yönelik kapsamlı özellikler sunarak geliştiricilerin uygulamaları dahilinde çeşitli dosya formatlarıyla verimli bir şekilde çalışmasına olanak tanır.

## SSS'ler
### GroupDocs.Parser tüm belge formatlarıyla uyumlu mu?
GroupDocs.Parser, PDF, Microsoft Office belgeleri (Word, Excel, PowerPoint) ve daha fazlasını içeren çok çeşitli formatları destekler.
### GroupDocs.Parser'ı kullanarak metinle birlikte meta verileri çıkarabilir miyim?
Evet, GroupDocs.Parser, desteklenen belge formatlarından hem metin içeriğinin hem de meta verilerin çıkarılmasına olanak tanır.
### GroupDocs.Parser için daha fazla kaynağı ve desteği nerede bulabilirim?
 Ziyaret edin[GroupDocs.Parser Belgeleri](https://tutorials.groupdocs.com/parser/net/) ayrıntılı API referansı için[GroupDocs Forumu](https://forum.groupdocs.com/c/parser/17) topluluk desteği için.
### GroupDocs.Parser için nasıl geçici lisans alabilirim?
 Bir talepte bulunabilirsiniz[geçici lisans](https://purchase.groupdocs.com/temporary-license/) değerlendirme ve test amaçlıdır.
### GroupDocs.Parser'ın ücretsiz deneme sürümü var mı?
 Evet, indirebilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) GroupDocs.Parser'ın sürümü.