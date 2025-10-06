---
title: Dikdörtgen Bölgelerdeki Metni Tanıma
linktitle: Dikdörtgen Bölgelerdeki Metni Tanıma
second_title: GroupDocs.Parser .NET API'si
description: OCR özelliklerine sahip GroupDocs.Parser for .NET'i kullanarak belgelerin belirli bölgelerindeki metni nasıl tanıyacağınızı öğrenin.
weight: 14
url: /tr/net/ocr-extraction/recognizing-text-in-rectangular-regions/
type: docs
---
# Dikdörtgen Bölgelerdeki Metni Tanıma

## giriiş
Bu öğreticide, belgelerin belirli dikdörtgen bölgelerindeki metni tanımak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin PDF, Word, Excel ve PowerPoint dahil olmak üzere çeşitli dosya formatlarından metin, meta veriler ve daha fazlasını çıkarmasına olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki kurulumlara sahip olduğunuzdan emin olun:
-  GroupDocs.Parser for .NET: Kitaplığı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
- Geliştirme Ortamı: Visual Studio veya başka herhangi bir .NET IDE.
- Örnek Belge: Tanınacak metni içeren örnek bir dosyaya (örneğin, PDF, DOCX) sahip olun.

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# kodunuza aktarmanız gerekir:
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
## 1. Adım: Ayrıştırıcı Ayarlarını Başlatın
 Kurulumla başlayın`ParserSettings` OCR konektörüyle. Burada Aspose OCR şirket içi bağlayıcıyı kullanacağız:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 2. Adım: Ayrıştırıcı Örneği Oluşturun
 Ardından, örneği oluşturun`Parser` önceden tanımlanmış ayarlara sahip sınıf:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Kod burada devam ediyor
}
```
 Yer değiştirmek`"YourSampleFile.pdf"` belgenizin yolu ile birlikte.
## 3. Adım: OCR Dikdörtgenini Tanımlayın
 Belge içinde metin tanımanın gerçekleştirileceği bir dikdörtgen tanımlayın. Örneğin, başlayan bir dikdörtgen`(0, 0)` genişlik ile`400` ve yükseklik`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## 4. Adım: Metin Tanıma Seçeneklerini Yapılandırın
 Yaratmak`TextOptions` Tanımlanan dikdörtgenle birlikte OCR kullanımını belirtmek için:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Adım 5: OCR kullanarak Metni Çıkarın
 Kullan`GetText` yöntemi`Parser` yapılandırılmış olan örnek`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Çıkarılan metni okuyun veya 'desteklenmiyor' durumunu ele alın
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Çözüm
Bu eğitimde, OCR kullanarak belgelerdeki belirli dikdörtgen bölgelerden metin çıkarmak için GroupDocs.Parser for .NET'ten nasıl yararlanılacağını gösterdik. Bu süreç daha da özelleştirilebilir ve otomatik metin çıkarma görevleri için çeşitli uygulamalara entegre edilebilir.

## SSS'ler
### GroupDocs.Parser taranan belgelerden metin çıkarabilir mi?
Evet, GroupDocs.Parser, taranan belgelerden metin çıkarmak için OCR'yi (Optik Karakter Tanıma) destekler.
### GroupDocs.Parser hangi dosya formatlarını destekler?
GroupDocs.Parser, PDF, DOCX, XLSX, PPTX ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### Metin çıkarma için desteklenmeyen belgeleri nasıl işleyebilirim?
 kullanarak metin çıkarmanın desteklenip desteklenmediğini kontrol edebilirsiniz.`TextReader` tarafından döndürülen örnek`parser.GetText(options)`.
### GroupDocs.Parser büyük ölçekli metin çıkarma görevleri için uygun mu?
Evet, GroupDocs.Parser, büyük ölçekli metin çıkarma görevlerini verimli bir şekilde gerçekleştirecek şekilde tasarlanmıştır.
### GroupDocs.Parser ile ilgili sorunlar için nereden destek alabilirim?
 Destek ve tartışmalar için şu adresi ziyaret edin:[GroupDocs.Parser forumu](https://forum.groupdocs.com/c/parser/17).