---
title: Seçeneklerle Belgeden Barkodları Çıkarma
linktitle: Seçeneklerle Belgeden Barkodları Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak belgelerden barkodları nasıl çıkaracağınızı öğrenin. Kod örnekleri ve SSS içeren kapsamlı eğitim.
weight: 14
url: /tr/net/barcode-extraction/extract-barcodes-from-document-with-options/
---

# Seçeneklerle Belgeden Barkodları Çıkarma

## giriiş
Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir belgeden barkod çıkarma işlemini anlatacağız. GroupDocs.Parser, PDF, Microsoft Word, Excel ve daha fazlası gibi çeşitli belge formatlarından metin, meta veriler ve barkodlar çıkarmanıza olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1. Geliştirme Ortamı: Makinenizde Visual Studio'nun kurulu olduğundan emin olun.
2.  GroupDocs.Parser Kitaplığı: GroupDocs.Parser for .NET kitaplığını şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/parser/net/).
3. Örnek Belge: Çıkarma için barkodları içeren örnek bir belge (örneğin, PDF, DOCX) hazırlayın.

## Ad Alanlarını İçe Aktar
GroupDocs.Parser işlevlerini kullanmak için öncelikle gerekli ad alanlarını C# projenize aktarmanız gerekir.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Adım 1: Ayrıştırıcı Sınıfının Bir Örneğini Oluşturun
 Başlamak için şunun bir örneğini oluşturun:`Parser` Örnek belgenizin yolunu ileterek sınıfa gidin.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Sonraki adımlarda eklenecek kod
}
```
## Adım 2: Barkod Çıkarma Desteğini Kontrol Edin
 Daha sonra belgenin barkod çıkarmayı destekleyip desteklemediğini kontrol edin.`Features` mülkiyeti`Parser` misal.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Adım 3: Barkod Çıkarma Seçeneklerini Tanımlayın
 Şimdi, kullanarak barkod çıkarma seçeneklerini belirtin.`BarcodeOptions`. Kalite modları ve barkod türleri gibi parametreleri ayarlayabilirsiniz.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Adım 4: Barkodları Belgeden Çıkarın
 Kullan`GetBarcodes` yöntemi`Parser` Tanımlanan seçeneklere göre barkodları çıkarmak için sınıf.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Adım 5: Çıkarılan Barkodları Yineleyin ve Görüntüleyin
Son olarak, çıkarılan barkodları yineleyin ve sayfa indeksini ve değerlerini görüntüleyin.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Çözüm
 Bu öğreticide, GroupDocs.Parser for .NET'i kullanarak bir belgeden barkodların nasıl çıkarılacağını öğrendik. Bu süreç bir oluşturmayı içerir.`Parser` örneğin çıkarma seçeneklerini tanımlama ve çıkarılan barkodlar üzerinde yineleme yapma. GroupDocs.Parser, çeşitli belge formatlarından barkod çıkarma görevini basitleştirerek .NET uygulamalarınızda verimli belge işlemeye olanak tanır.

## SSS'ler
### GroupDocs.Parser, PDF belgelerinden barkod çıkarabilir mi?
Evet, GroupDocs.Parser, DOCX, XLSX vb. diğer formatların yanı sıra PDF belgelerinden barkod çıkarmayı da destekler.
### GroupDocs.Parser hangi barkod türlerini destekler?
GroupDocs.Parser, QR kodları, Code 39, Code 128 ve daha fazlasını içeren çeşitli barkod türlerini destekler.
### GroupDocs.Parser ticari kullanım için lisans gerektiriyor mu?
 Evet, ticari kullanım için geçerli bir lisans gereklidir. adresinden lisans alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser, belgelerin toplu işlenmesi için uygun mudur?
Evet, GroupDocs.Parser, metin çıkarma, meta veri alma ve barkod çıkarma için belgelerin toplu işlenmesini verimli bir şekilde gerçekleştirebilir.
### GroupDocs.Parser için teknik desteği nerede bulabilirim?
 Teknik destek alabilir veya sorularınızı sorabilirsiniz.[GroupDocs forumu](https://forum.groupdocs.com/c/parser/17).