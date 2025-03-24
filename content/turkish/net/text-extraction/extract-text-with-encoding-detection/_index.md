---
title: Kodlama Algılamayla Metni Çıkarma
linktitle: Kodlama Algılamayla Metni Çıkarma
second_title: GroupDocs.Parser .NET API'si
description: GroupDocs.Parser for .NET'i kullanarak kodlama algılamayla belgelerden metin çıkarın. .NET uygulamalarınızda çeşitli formatları verimli bir şekilde ayrıştırın.
weight: 10
url: /tr/net/text-extraction/extract-text-with-encoding-detection/
---

# Kodlama Algılamayla Metni Çıkarma

## giriiş
GroupDocs.Parser for .NET, geliştiricilerin .NET uygulamalarındaki çeşitli belge formatlarından metin, meta veriler ve diğer bilgileri ayıklamasına olanak tanıyan güçlü bir kitaplıktır. Bu eğitim, kodlamayı algılarken belgelerden metin ayıklamak için GroupDocs.Parser'ı kullanma sürecinde size rehberlik edecektir. Bu adımları izleyerek, .NET projelerinizde farklı belge türlerini verimli bir şekilde ayrıştırabilecek ve bunlarla çalışabileceksiniz.
## Önkoşullar
Bu eğitime dalmadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- C# ve .NET geliştirme konusunda temel bilgiler.
- Sisteminizde yüklü Visual Studio veya tercih edilen herhangi bir .NET geliştirme ortamı.
- .NET kitaplığı için GroupDocs.Parser'a erişim.

## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını C# projenize aktardığınızdan emin olun:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Options;
```
## Adım 1: Kodlamayla LoadOptions Oluşturun
 İlk önce bir örneğini oluşturun`LoadOptions` metin çıkarma için belge biçimini ve kodlamayı belirtmek için sınıf. Bu örnekte, Kelime İşleme belgeleri için varsayılan ANSI kodlamasını (kod sayfası 1251) kullanacağız.
```csharp
LoadOptions loadOptions = new LoadOptions(FileFormat.WordProcessing, null, null, Encoding.GetEncoding(1251));
```
## Adım 2: Ayrıştırıcıyı Başlatın ve Metni Çıkarın
 Ardından, bir örneğini oluşturun`Parser`sınıfa gidin ve belge yolunu birlikte iletin`LoadOptions` buna örnek. Ardından, bunun düz metinli bir belge olup olmadığını kontrol etmek için belge bilgilerini alın.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx", loadOptions))
{
    TextDocumentInfo info = parser.GetDocumentInfo() as TextDocumentInfo;
    if (info == null)
    {
        Console.WriteLine("Isn't a plain text document");
        return;
    }
    
    Console.WriteLine("Encoding: " + info.Encoding.WebName);
}
```

## Çözüm
Bu öğreticide, kodlama algılamayla belgelerden metin ayıklamak için GroupDocs.Parser for .NET'in nasıl kullanılacağını araştırdık. Yukarıda özetlenen adımları izleyerek belge ayrıştırma yeteneklerini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilirsiniz.

## SSS'ler
### GroupDocs.Parser farklı belge formatlarını işleyebilir mi?
Evet, GroupDocs.Parser, Word, PDF, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### GroupDocs.Parser büyük ölçekli belge işlemeye uygun mu?
GroupDocs.Parser kesinlikle büyük belgeleri verimli bir şekilde işlemek için tasarlanmıştır.
### GroupDocs.Parser'ı kullanarak metinle birlikte meta verileri çıkarabilir miyim?
Evet, GroupDocs.Parser meta verilerin, yapılandırılmış metnin ve daha fazlasının çıkarılmasına olanak tanır.
### GroupDocs.Parser bulut tabanlı belge ayrıştırma desteği sağlıyor mu?
GroupDocs.Parser öncelikli olarak şirket içi ortamlarda çalışır ancak belirli kullanım durumları için bulut hizmetleriyle entegre edebilirsiniz.
### GroupDocs.Parser ile ilgili nasıl destek veya yardım alabilirim?
Destek için şu adresteki GroupDocs.Parser forumunu ziyaret edin:[GroupDocs Forumu](https://forum.groupdocs.com/c/parser/17).