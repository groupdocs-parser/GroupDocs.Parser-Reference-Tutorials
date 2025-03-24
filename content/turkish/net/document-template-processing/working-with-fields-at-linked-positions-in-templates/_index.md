---
title: Şablonlarda Bağlantılı Konumlardaki Alanlarla Çalışma
linktitle: Şablonlarda Bağlantılı Konumlardaki Alanlarla Çalışma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerden verileri verimli bir şekilde nasıl çıkaracağınızı öğrenin. Kod örnekleriyle adım adım eğitim.
weight: 12
url: /tr/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## giriiş
GroupDocs.Parser for .NET, belge ayrıştırma ve veri çıkarma görevlerini kolaylaştırmak için tasarlanmış güçlü bir kitaplıktır. PDF, DOCX, XLSX ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler. Temel özelliklerinden biri, bir belge içindeki alanları tanımlamanıza ve bu önceden tanımlanmış şablonlara dayalı olarak belirli verileri çıkarmanıza olanak tanıyan şablon tabanlı veri çıkarmadır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- C# programlamanın temel anlayışı
- Sisteminizde Visual Studio yüklü
-  .NET kitaplığı için GroupDocs.Parser (şu adresten indirin:[Burada](https://releases.groupdocs.com/parser/net/))
- Çalışılacak örnek belge dosyaları

## Ad Alanlarını İçe Aktarma
C# projenize gerekli ad alanlarını ekleyerek başlayın:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 1. Adım: Şablon Alanlarını Tanımlayın
İlk olarak, normal ifadeleri ve bağlantılı konumları kullanarak şablon alanlarını tanımlayın:
```csharp
// Düzenli ifadeyle bir alan tanımlayın
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Belirli konum ayarlarıyla bağlantılı bir alan tanımlayın
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## 2. Adım: Şablon Oluşturun
Daha sonra tanımlı alanları içeren bir şablon oluşturun:
```csharp
// Tanımlanan alanlarla bir şablon oluşturun
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Adım 3: Belgeyi Şablonla Ayrıştırma
 Şimdi, başlat`Parser` şablonu kullanarak belgeyi sınıflandırın ve ayrıştırın:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Belgeyi şablona göre ayrıştırın
    DocumentData data = parser.ParseByTemplate(template);
    // Çıkarılan verileri yineleyin ve sonuçları yazdırın
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Çözüm
GroupDocs.Parser for .NET, şablonlar kullanarak belgelerden yapılandırılmış veri çıkarma işlemini basitleştirir. Alanları tanımlayarak ve şablonları uygulayarak ilgili bilgileri verimli bir şekilde çıkarabilir, belge işleme görevlerinde otomasyonu ve üretkenliği artırabilirsiniz.

## SSS'ler
### GroupDocs.Parser şifrelenmiş PDF dosyalarından veri çıkarabilir mi?
Evet, GroupDocs.Parser, ayrıştırma sırasında parolayı sağlayarak şifrelenmiş PDF dosyalarının ayrıştırılmasını destekler.
### Şablon tabanlı çıkarma için hangi dosya formatları desteklenir?
GroupDocs.Parser, PDF, DOCX, XLSX, PPTX, TXT ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### GroupDocs.Parser'ın deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### Belgelerin toplu işlenmesi için GroupDocs.Parser'ı kullanabilir miyim?
Evet, GroupDocs.Parser, toplu işlemenin birden fazla belgeyi aynı anda ayrıştırmasına olanak tanır.
### GroupDocs.Parser için nereden teknik destek alabilirim?
 Şu adresten teknik destek arayabilir ve toplulukla etkileşime geçebilirsiniz:[GroupDocs forumu](https://forum.groupdocs.com/c/parser/17).