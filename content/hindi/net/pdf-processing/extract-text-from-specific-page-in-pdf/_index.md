---
title: पीडीएफ में विशिष्ट पृष्ठ से पाठ निकालें
linktitle: पीडीएफ में विशिष्ट पृष्ठ से पाठ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके PDF से टेक्स्ट निकालें। इस शक्तिशाली लाइब्रेरी के साथ विशिष्ट पृष्ठ सामग्री को आसानी से पुनः प्राप्त करें।
weight: 15
url: /hi/net/pdf-processing/extract-text-from-specific-page-in-pdf/
---

# पीडीएफ में विशिष्ट पृष्ठ से पाठ निकालें

## परिचय
इस ट्यूटोरियल में, आप सीखेंगे कि PDF दस्तावेज़ के भीतर किसी विशिष्ट पृष्ठ से टेक्स्ट निकालने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को PDF, Microsoft Word, Excel और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों के साथ काम करने की अनुमति देती है। अपने .NET एप्लिकेशन में टेक्स्ट निष्कर्षण को एकीकृत करने के लिए इन चरणों का पालन करें।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- विजुअल स्टूडियो: .NET विकास के लिए एकीकृत विकास वातावरण (आईडीई)।
-  .NET के लिए GroupDocs.Parser: लाइब्रेरी डाउनलोड करें[यहाँ](https://releases.groupdocs.com/parser/net/).
- C# का ज्ञान: C# प्रोग्रामिंग भाषा की बुनियादी समझ।
- नमूना पीडीएफ फाइल: पाठ निकालने के लिए एक पीडीएफ दस्तावेज़।

## नामस्थान आयात करें
अपने C# कोड में आवश्यक नेमस्पेस आयात करके प्रारंभ करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 उदाहरण प्रस्तुत करें`Parser`अपने नमूना पीडीएफ फ़ाइल का पथ प्रदान करके क्लास का चयन करें।
```csharp
// पार्सर क्लास का एक उदाहरण बनाएँ
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // आपका कोड यहाँ
}
```
## चरण 2: दस्तावेज़ जानकारी प्राप्त करें
 PDF दस्तावेज़ के बारे में जानकारी प्राप्त करें`GetDocumentInfo()` तरीका।
```csharp
// दस्तावेज़ जानकारी प्राप्त करें
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## चरण 3: पृष्ठों पर पुनरावृत्ति करें
पाठ निष्कर्षण के लिए विशिष्ट पृष्ठ का चयन करने हेतु दस्तावेज़ के प्रत्येक पृष्ठ पर जाएँ।
```csharp
// पृष्ठों पर पुनरावृत्ति करें
for (int p = 0; p < documentInfo.PageCount; p++)
{
    // आपका कोड यहाँ
}
```
## चरण 4: पृष्ठ से पाठ निकालें
 इच्छित पृष्ठ से पाठ निकालें`GetText(int pageIndex)` तरीका।
```csharp
// रीडर में पाठ निकालें
using (TextReader reader = parser.GetText(pageIndex))
{
    // आपका कोड यहाँ
    string extractedText = reader.ReadToEnd();
    Console.WriteLine(extractedText); // निकाले गए पाठ को आउटपुट करें
}
```

## निष्कर्ष
अब आप सीख चुके हैं कि .NET के लिए GroupDocs.Parser का उपयोग करके PDF फ़ाइल में किसी विशिष्ट पृष्ठ से टेक्स्ट कैसे निकाला जाता है। इस प्रक्रिया में पार्सर को आरंभ करना, दस्तावेज़ जानकारी प्राप्त करना, पृष्ठों पर पुनरावृत्ति करना और वांछित पृष्ठ से टेक्स्ट निकालना शामिल है। PDF टेक्स्ट निष्कर्षण को कुशलतापूर्वक संभालने के लिए इन चरणों को अपने .NET एप्लिकेशन में शामिल करें।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser for .NET .NET फ्रेमवर्क के सभी संस्करणों के साथ संगत है?
हां, .NET के लिए GroupDocs.Parser .NET फ्रेमवर्क संस्करण 4.5 और उससे ऊपर का समर्थन करता है।
### क्या GroupDocs.Parser एन्क्रिप्टेड पीडीएफ फाइलों से पाठ निकाल सकता है?
नहीं, GroupDocs.Parser एन्क्रिप्टेड या पासवर्ड-संरक्षित PDF फ़ाइलों से पाठ निष्कर्षण का समर्थन नहीं करता है।
### क्या GroupDocs.Parser पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों को संभालता है?
हां, GroupDocs.Parser माइक्रोसॉफ्ट वर्ड, एक्सेल, पावरपॉइंट और अन्य सहित कई प्रारूपों का समर्थन करता है।
### क्या GroupDocs.Parser के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप GroupDocs.Parser के निःशुल्क परीक्षण को यहां से एक्सेस कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Parser के लिए तकनीकी सहायता कहां मिल सकती है?
 आप तकनीकी सहायता पा सकते हैं और समुदाय के साथ जुड़ सकते हैं[ग्रुपडॉक्स फ़ोरम](https://forum.groupdocs.com/c/parser/17).