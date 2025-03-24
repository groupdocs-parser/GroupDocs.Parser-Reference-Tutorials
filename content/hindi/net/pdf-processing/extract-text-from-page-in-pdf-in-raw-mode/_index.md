---
title: रॉ मोड में पीडीएफ में पेज से टेक्स्ट निकालें
linktitle: रॉ मोड में पीडीएफ में पेज से टेक्स्ट निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: C# में GroupDocs.Parser का उपयोग करके PDF से टेक्स्ट निकालें। इस शक्तिशाली .NET लाइब्रेरी के साथ कुशल PDF टेक्स्ट निष्कर्षण सीखें।
weight: 16
url: /hi/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# रॉ मोड में पीडीएफ में पेज से टेक्स्ट निकालें

## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि रॉ मोड का उपयोग करके PDF दस्तावेज़ों में पृष्ठों से टेक्स्ट निकालने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली उपकरण है जो डेवलपर्स को प्रोग्रामेटिक रूप से विभिन्न दस्तावेज़ प्रारूपों के साथ काम करने में सक्षम बनाता है।
## आवश्यक शर्तें
इस ट्यूटोरियल को शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- आपके मशीन पर Visual Studio स्थापित है.
- C# प्रोग्रामिंग का बुनियादी ज्ञान.
- .NET लाइब्रेरी के लिए GroupDocs.Parser, जिसे आप कर सकते हैं[यहाँ डाउनलोड करें](https://releases.groupdocs.com/parser/net/).
- परीक्षण प्रयोजनों के लिए एक नमूना पीडीएफ फाइल।

## नामस्थान आयात करें
सबसे पहले, अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करना सुनिश्चित करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 आरंभ करने के लिए, उदाहरण बनाएं`Parser`अपने नमूना पीडीएफ फ़ाइल का पथ प्रदान करके क्लास का चयन करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // आपका कोड यहां जाएगा
}
```
## चरण 2: दस्तावेज़ जानकारी प्राप्त करें और पृष्ठों पर पुनरावृत्ति करें
इसके बाद, दस्तावेज़ की जानकारी प्राप्त करें और पाठ निकालने के लिए प्रत्येक पृष्ठ पर पुनरावृत्ति करें।
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // पाठ निष्कर्षण के लिए आपका कोड यहां है
}
```
## चरण 3: प्रत्येक पृष्ठ से पाठ निकालें
 लूप के भीतर, का उपयोग करें`GetText` प्रत्येक पृष्ठ से पाठ निकालने और उसे प्रिंट करने की विधि।
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## निष्कर्ष
 इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Parser का उपयोग करके रॉ मोड में PDF पृष्ठों से टेक्स्ट निकालना सीखा है। इस प्रक्रिया में एक बनाना शामिल है`Parser` उदाहरण के लिए, दस्तावेज़ जानकारी प्राप्त करना, प्रत्येक पृष्ठ पर पुनरावृत्ति करना, और इसका उपयोग करके पाठ निकालना`GetText` तरीका।

## अक्सर पूछे जाने वाले प्रश्न
### .NET के लिए GroupDocs.Parser क्या है?
GroupDocs.Parser for .NET एक दस्तावेज़ पार्सिंग एपीआई है जो डेवलपर्स को प्रोग्रामेटिक रूप से विभिन्न फ़ाइल प्रारूपों से पाठ, मेटाडेटा और अन्य जानकारी निकालने की अनुमति देता है।
### मैं .NET के लिए GroupDocs.Parser कैसे डाउनलोड करूं?
 आप लाइब्रेरी को यहां से डाउनलोड कर सकते हैं[ग्रुपडॉक्स वेबसाइट](https://releases.groupdocs.com/parser/net/).
### क्या कोई निःशुल्क परीक्षण उपलब्ध है?
 हां, आप .NET के लिए GroupDocs.Parser के एक नि: शुल्क परीक्षण का उपयोग कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मुझे .NET के लिए GroupDocs.Parser हेतु समर्थन कहां मिल सकता है?
 तकनीकी सहायता और सामुदायिक समर्थन के लिए, यहां जाएं[ग्रुपडॉक्स फ़ोरम](https://forum.groupdocs.com/c/parser/17).
### मैं .NET के लिए GroupDocs.Parser का लाइसेंस कैसे खरीद सकता हूं?
 आप यहां से लाइसेंस खरीद सकते हैं[खरीद पृष्ठ](https://purchase.groupdocs.com/buy) या अस्थायी लाइसेंस प्राप्त करें[यहाँ](https://purchase.groupdocs.com/temporary-license/).