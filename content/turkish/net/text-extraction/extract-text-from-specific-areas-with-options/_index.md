---
title: Seçeneklerle Belirli Alanlardan Metin Çıkarma
linktitle: Seçeneklerle Belirli Alanlardan Metin Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerdeki belirli alanlardan metni nasıl çıkaracağınızı öğrenin. Bu eğitimle gelişmiş metin çıkarma seçeneklerini keşfedin.
type: docs
weight: 14
url: /tr/net/text-extraction/extract-text-from-specific-areas-with-options/
---
## giriiş
Bu öğreticide, özelleştirilebilir seçenekleri kullanarak bir belgedeki belirli alanlardan metin çıkarmak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin çeşitli belge formatlarındaki metni zahmetsizce ayrıştırmasına ve ayıklamasına olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Kodlamaya dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. Geliştirme Ortamı: Visual Studio'yu veya başka herhangi bir .NET geliştirme IDE'sini yükleyin.
2.  GroupDocs.Parser Kitaplığı: .NET için GroupDocs.Parser'ı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
3. Örnek Dosya: Metin çıkarmak için örnek bir belge (örneğin, PDF, DOCX, vb.) hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle GroupDocs.Parser sınıflarına ve yöntemlerine erişmek için gerekli ad alanlarını içe aktarmanız gerekir.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Bir örneğini başlat`Parser` örnek dosyanızın yolunu sağlayarak sınıf.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Metin alanı çıkarma kodu buraya gelecek
}
```
## Adım 2: Metin Alanı Çıkarma Seçeneklerini Tanımlayın
 Yaratmak`PageTextAreaOptions` Metin çıkarma kriterlerini belirlemek için.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
Bu örnekte:
- `"\\s[a-z]{2}\\s"` yalnızca küçük harfler içeren metin alanlarını eşleştirmek için kullanılan bir normal ifade modelidir.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` metnin çıkarılacağı sayfadaki dikdörtgeni (konum ve boyut) tanımlar.
## 3. Adım: Metin Alanlarını Çıkarın
Belirtilen kriterleri karşılayan metin alanlarını çıkarmak için tanımlanmış seçenekleri kullanın.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Adım 4: Çıkarılan Metin Alanlarını Kontrol Edin ve Yineleyin
Metin alanı çıkarmanın desteklenip desteklenmediğini kontrol edin ve ardından çıkarılan alanlar üzerinde yineleme yapın.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir belgedeki belirli alanlardan metinlerin nasıl çıkarılacağını ele aldık. Bu kitaplık, çeşitli belge formatlarını ayrıştırmak için kapsamlı yetenekler sunarak onu metin çıkarma görevleri için değerli bir araç haline getirir.

## SSS'ler
### GroupDocs.Parser taranan belgelerden metin çıkarabilir mi?
Evet, GroupDocs.Parser, taranan belgeler için OCR tabanlı metin ayıklamayı destekler.
### GroupDocs.Parser birden çok belge biçimiyle uyumlu mu?
Evet, PDF, DOCX, XLSX, PPTX ve diğer popüler formatlardaki metinleri ayrıştırabilir ve çıkarabilir.
### GroupDocs.Parser .NET Core desteği sağlıyor mu?
Evet, GroupDocs.Parser, .NET Core'un yanı sıra .NET Framework ile de uyumludur.
### GroupDocs.Parser'ı kullanarak metinle birlikte meta verileri çıkarabilir miyim?
Evet, belgelerden hem metin içeriğini hem de meta verileri çıkarabilirsiniz.
### GroupDocs.Parser'ın deneme sürümü mevcut mu?
 Evet, şu adresten ücretsiz deneme alabilirsiniz:[Burada](https://releases.groupdocs.com/).