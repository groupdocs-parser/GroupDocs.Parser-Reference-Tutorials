---
title: दस्तावेज़ पृष्ठ से छवियाँ निकालें
linktitle: दस्तावेज़ पृष्ठ से छवियाँ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से छवियाँ निकालना सीखें। अपने दस्तावेज़ प्रसंस्करण क्षमताओं को बढ़ाएँ।
weight: 12
url: /hi/net/image-extraction/extract-images-from-document-page/
type: docs
---
# दस्तावेज़ पृष्ठ से छवियाँ निकालें

## परिचय
इस ट्यूटोरियल में, हम सीखेंगे कि .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ पृष्ठ से छवियाँ कैसे निकालें। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो आपको PDF, Microsoft Word, Excel, PowerPoint और अन्य जैसे विभिन्न दस्तावेज़ प्रारूपों से टेक्स्ट, मेटाडेटा, छवियाँ और बहुत कुछ निकालने की अनुमति देती है। हम इस लाइब्रेरी का उपयोग करके दस्तावेज़ पृष्ठ से छवियाँ निकालने के लिए आवश्यक चरणों से गुजरेंगे।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- आपके मशीन पर Visual Studio स्थापित है.
- C# और .NET प्रोग्रामिंग की बुनियादी समझ।
- .NET पुस्तकालय के लिए GroupDocs.Parser स्थापित। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/parser/net/).

## नामस्थान आयात करें
GroupDocs.Parser की कार्यक्षमताओं का उपयोग करने के लिए अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को आयात करके प्रारंभ करें।
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 इसका एक उदाहरण बनाकर शुरू करें`Parser` क्लास पर जाएँ और अपने नमूना दस्तावेज़ का पथ निर्दिष्ट करें.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // आपका कोड यहाँ
}
```
## चरण 2: छवि निष्कर्षण समर्थन के लिए दस्तावेज़ की जाँच करें
 इसके बाद, जाँचें कि क्या दस्तावेज़ छवि निष्कर्षण का समर्थन करता है`Features.Images` संपत्ति।
```csharp
if (!parser.Features.Images)
{
    Console.WriteLine("Document doesn't support image extraction.");
    return;
}
```
## चरण 3: दस्तावेज़ जानकारी प्राप्त करें
 दस्तावेज़ के बारे में जानकारी प्राप्त करने के लिए निम्न का उपयोग करें:`GetDocumentInfo()` तरीका।
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## चरण 4: दस्तावेज़ पृष्ठों पर पुनरावृत्ति करें
जाँच करें कि दस्तावेज़ में पृष्ठ हैं या नहीं और फिर छवियों को निकालने के लिए प्रत्येक पृष्ठ पर पुनरावृत्ति करें।
```csharp
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // पृष्ठ से छवियाँ निकालने के लिए आपका कोड
}
```
## चरण 5: प्रत्येक पृष्ठ से छवियाँ निकालें
 पृष्ठ पुनरावृत्ति लूप के भीतर, का उपयोग करें`GetImages(pageIndex)` प्रत्येक पृष्ठ से छवियों को पुनः प्राप्त करने की विधि।
```csharp
foreach (PageImageArea image in parser.GetImages(pageIndex))
{
    Console.WriteLine($"Rectangle: {image.Rectangle}, FileType: {image.FileType}");
    // छवि को सहेजने या संसाधित करने के लिए अतिरिक्त कोड
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ पृष्ठ से छवियों को निकालने का तरीका खोजा। हमने पार्सर इंस्टेंस बनाने, छवि निष्कर्षण समर्थन की जाँच करने, दस्तावेज़ जानकारी प्राप्त करने, पृष्ठों पर पुनरावृत्ति करने और प्रत्येक पृष्ठ से छवियों को निकालने जैसे आवश्यक चरणों को कवर किया। अब, आप अपने .NET अनुप्रयोगों में छवि निष्कर्षण कार्यक्षमता को कुशलतापूर्वक एकीकृत कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser PDF दस्तावेज़ों से छवियाँ निकाल सकता है?
हां, GroupDocs.Parser पीडीएफ सहित विभिन्न दस्तावेज़ प्रारूपों से छवि निष्कर्षण का समर्थन करता है।
### क्या GroupDocs.Parser दस्तावेजों के बैच प्रसंस्करण के लिए उपयुक्त है?
बिल्कुल! आप कई दस्तावेज़ों को बैच प्रक्रिया और वांछित सामग्री को कुशलतापूर्वक निकालने के लिए GroupDocs.Parser का उपयोग कर सकते हैं।
### मैं GroupDocs.Parser के लिए अधिक संसाधन और समर्थन कहां पा सकता हूं?
 आप यहां जा सकते हैं[GroupDocs.Parser मंच](https://forum.groupdocs.com/c/parser/17) सामुदायिक समर्थन और चर्चा के लिए।
### क्या मैं खरीदने से पहले GroupDocs.Parser आज़मा सकता हूँ?
 हाँ, आप प्राप्त कर सकते हैं[निःशुल्क परीक्षण संस्करण](https://releases.groupdocs.com/) पुस्तकालय की क्षमताओं का मूल्यांकन करने के लिए।
### मैं GroupDocs.Parser के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप एक प्राप्त कर सकते हैं[अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/) परीक्षण और विकास प्रयोजनों के लिए।