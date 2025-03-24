---
title: Belirli Alanlardaki Metni Tanıma
linktitle: Belirli Alanlardaki Metni Tanıma
second_title: GroupDocs.Parser .NET API'si
description: OCR özelliklerine sahip belgelerdeki belirli alanlardan metin çıkarmak için GroupDocs.Parser for .NET'i nasıl kullanacağınızı öğrenin.
weight: 13
url: /tr/net/ocr-extraction/recognizing-text-in-specific-areas/
---

# Belirli Alanlardaki Metni Tanıma

## giriiş
Bu öğreticide, bir belgedeki belirli alanlardaki metni tanımak ve çıkarmak için GroupDocs.Parser for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Parser, geliştiricilerin PDF, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge formatlarıyla çalışmasına olanak tanıyan güçlü bir belge ayrıştırma kitaplığıdır. Özellikle, bir belge içindeki tanımlı alanlardan metin çıkarmak için GroupDocs.Parser'ın OCR (Optik Karakter Tanıma) özelliklerinden yararlanmaya odaklanacağız.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulları oluşturduğunuzdan emin olun:
1. Visual Studio IDE: Makinenizde Visual Studio'nun kurulu olduğundan emin olun.
2.  GroupDocs.Parser for .NET: GroupDocs.Parser for .NET'i şu adresten indirip yükleyin:[İndirme: {link](https://releases.groupdocs.com/parser/net/).
3. Belge Örnekleri: Metin çıkarmak istediğiniz örnek dosyaları (örneğin, PDF, DOCX) hazırlayın.

## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını projenize aktarın:
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

GroupDocs.Parser for .NET'i kullanarak süreci ayrıntılı adımlara ayıralım:
## 1. Adım: OCR Bağlayıcıyla Ayrıştırıcı Ayarları Oluşturun
 İlk önce bir örneğini oluşturun`ParserSettings`sınıflandırın ve bunu bir OCR konektörüyle başlatın, örneğin`AsposeOcrOnPremise`:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Adım 2: Ayrıştırıcıyı Ayarlarla Örneklendirin
 Ardından, bir örneğini oluşturun`Parser` önceden oluşturulmuş olanı geçerek sınıf`ParserSettings`:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Kod pasajı devam ediyor...
}
```
 Yer değiştirmek`"YourSampleFile.pdf"` hedef belgenizin yolu ile.
## 3. Adım: Metin Alanı Çıkarma Seçeneklerini Yapılandırma
 Bir örneğini oluşturun`PageTextAreaOptions` OCR tabanlı metin ayıklamayı etkinleştirmek için:
```csharp
PageTextAreaOptions options = new PageTextAreaOptions(true);
```
 Ayarlamak`true` Daha iyi metin tanıma amacıyla OCR'yi etkinleştirmek için.
## Adım 4: Metin Alanlarını Çıkarın
 Çağırmak`parser.GetTextAreas(options)` belgeden metin alanlarını çıkarmak için:
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Adım 5: Çıkarılan Metin Alanlarını İşleyin
Çıkarılan metin alanları üzerinde yineleme yapın ve metin, konum ve boyut bilgilerini alın:
```csharp
foreach (PageTextArea area in areas)
{
    Console.WriteLine(area.Text);
    Console.WriteLine($"\tPosition: ({area.Rectangle.Left}; {area.Rectangle.Top})");
    Console.WriteLine($"\tSize: ({area.Rectangle.Size.Width}; {area.Rectangle.Size.Height})");
}
```

## Çözüm
Bu öğreticide, GroupDocs.Parser for .NET'i OCR yetenekleriyle kullanarak bir belgenin belirli alanlarından metin çıkarma sürecini ele aldık. Bu adımları izleyerek, metin çıkarma görevlerini programlı bir şekilde gerçekleştirmek için GroupDocs.Parser'ın ayrıştırma işlevlerinden etkili bir şekilde yararlanabilirsiniz.

## SSS'ler
### GroupDocs.Parser taranan belgelerden metin çıkarabilir mi?
Evet, GroupDocs.Parser, belgeler içindeki taranmış görüntülerden metin çıkarmak için OCR'yi destekler.
### GroupDocs.Parser hangi belge formatlarını destekler?
GroupDocs.Parser, PDF, DOCX, XLSX, PPTX, TXT ve daha fazlasını içeren çok çeşitli formatları destekler.
### GroupDocs.Parser, belgelerin toplu işlenmesi için uygun mudur?
Evet, GroupDocs.Parser, belge ayrıştırma ve çıkarma için toplu işleme görevlerini verimli bir şekilde gerçekleştirebilir.
### GroupDocs.Parser ile metin çıkarma seçeneklerini özelleştirebilir miyim?
Evet, GroupDocs.Parser, metin ayıklamayı belirli gereksinimlere göre özelleştirmek için çeşitli seçenekler sunar.
### GroupDocs.Parser, belgelerden meta verilerin çıkarılmasına yönelik destek sağlıyor mu?
Evet, GroupDocs.Parser, yazar, oluşturulma tarihi ve daha fazlası gibi meta verilerin desteklenen belge formatlarından çıkarılmasına olanak tanır.