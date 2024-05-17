---
title: टेम्पलेट्स में निश्चित स्थानों पर फ़ील्ड्स के साथ कार्य करना
linktitle: टेम्पलेट्स में निश्चित स्थानों पर फ़ील्ड्स के साथ कार्य करना
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से डेटा निकालना सीखें। कोड उदाहरणों के साथ व्यापक ट्यूटोरियल।
type: docs
weight: 11
url: /hi/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Parser का उपयोग करके टेम्प्लेट के भीतर निश्चित स्थानों पर फ़ील्ड के साथ काम करने का तरीका जानेंगे। GroupDocs.Parser एक शक्तिशाली दस्तावेज़ पार्सिंग लाइब्रेरी है जो डेवलपर्स को PDF, Word, Excel और अन्य जैसे विभिन्न दस्तावेज़ प्रारूपों से डेटा निकालने में सक्षम बनाती है। विशेष रूप से, हम उनके निश्चित पदों के आधार पर लक्षित जानकारी निकालने के लिए टेम्प्लेट फ़ील्ड को परिभाषित करने और उनका उपयोग करने पर ध्यान केंद्रित करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- C# और .NET विकास की बुनियादी समझ।
- आपके सिस्टम पर Visual Studio स्थापित है.
- .NET पुस्तकालय के लिए GroupDocs.Parser स्थापित। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/parser/net/).
- परीक्षण के लिए नमूना दस्तावेज़ फ़ाइलें.

## नामस्थान आयात करें
अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को शामिल करके आरंभ करें:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## चरण 1: टेम्पलेट फ़ील्ड परिभाषित करें
सबसे पहले, टेम्पलेट के भीतर एक निश्चित स्थान वाला फ़ील्ड परिभाषित करें। यह फ़ील्ड उस क्षेत्र का प्रतिनिधित्व करता है जहाँ से डेटा निकाला जाएगा।
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
यहाँ:
- `Rectangle` क्षेत्र की स्थिति और आकार निर्दिष्ट करता है.
- `Point(35, 135)` ऊपरी-बाएं कोने के निर्देशांक को दर्शाता है.
- `Size(100, 10)` क्षेत्र की चौड़ाई और ऊंचाई को परिभाषित करता है.
- `"FromCompany"` इस फ़ील्ड को निर्दिष्ट नाम है.
## चरण 2: एक टेम्पलेट बनाएँ
परिभाषित फ़ील्ड का उपयोग करके एक टेम्पलेट बनाएँ.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
`Template` ऑब्जेक्ट परिभाषित फ़ील्ड रखता है.
## चरण 3: टेम्पलेट का उपयोग करके दस्तावेज़ को पार्स करें
 उदाहरण प्रस्तुत करें`Parser` क्लास को लक्ष्य दस्तावेज़ पथ के साथ जोड़ें और फिर बनाए गए टेम्पलेट का उपयोग करके दस्तावेज़ को पार्स करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // निकाले गए डेटा के माध्यम से पुनरावृत्ति करें
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
यहाँ:
- `Parser` नमूना दस्तावेज़ फ़ाइल पथ के साथ आरंभ किया गया है.
- `ParseByTemplate` विधि का उपयोग प्रदान किए गए टेम्पलेट के आधार पर डेटा निकालने के लिए किया जाता है।
-  निकाले गए डेटा तक पहुँच का उपयोग किया जाता है`DocumentData`जहां प्रत्येक आइटम एक परिभाषित फ़ील्ड से मेल खाता है।

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Parser का उपयोग करके टेम्प्लेट में निश्चित स्थानों पर फ़ील्ड के साथ काम करने की प्रक्रिया को कवर किया है। विशिष्ट फ़ील्ड स्थितियों वाले टेम्प्लेट को परिभाषित करके, डेवलपर्स विभिन्न दस्तावेज़ प्रारूपों से लक्षित डेटा को सटीक रूप से निकाल सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser सभी दस्तावेज़ प्रारूपों के साथ संगत है?
 GroupDocs.Parser पीडीएफ, माइक्रोसॉफ्ट वर्ड, एक्सेल, पावरपॉइंट, आदि सहित फ़ाइल स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।[प्रलेखन](https://reference.groupdocs.com/parser/net/) विस्तृत सूची के लिए कृपया देखें.
### मैं GroupDocs.Parser के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप परीक्षण प्रयोजनों के लिए अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### मुझे GroupDocs.Parser के लिए समर्थन कहां मिल सकता है?
 तकनीकी सहायता और चर्चा के लिए कृपया यहां जाएं[GroupDocs.Parser मंच](https://forum.groupdocs.com/c/parser/17).
### क्या मैं खरीदने से पहले GroupDocs.Parser आज़मा सकता हूँ?
 हां, आप निःशुल्क परीक्षण के साथ लाइब्रेरी का भ्रमण कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं GroupDocs.Parser के लिए लाइसेंस कैसे खरीदूं?
 लाइसेंस खरीदने के लिए, यहां जाएं[खरीद पृष्ठ](https://purchase.groupdocs.com/buy).