---
title: रॉ मोड में पेज से टेक्स्ट निकालें
linktitle: रॉ मोड में पेज से टेक्स्ट निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: इस व्यापक ट्यूटोरियल में .NET के लिए Groupdocs.Parser का उपयोग करके दस्तावेज़ पृष्ठों से कुशल पाठ निष्कर्षण सीखें।
weight: 17
url: /hi/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## परिचय
इस ट्यूटोरियल में, आप सीखेंगे कि रॉ मोड में दस्तावेज़ पृष्ठों से टेक्स्ट निकालने के लिए .NET के लिए Groupdocs.Parser का उपयोग कैसे करें। यह लाइब्रेरी विभिन्न फ़ाइल स्वरूपों से सामग्री को पार्स करने और निकालने के लिए कुशल उपकरण प्रदान करती है, जिससे डेवलपर्स को अपने .NET अनुप्रयोगों में दस्तावेज़ टेक्स्ट निष्कर्षण को शामिल करने में सक्षम बनाता है।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- C# और .NET प्रोग्रामिंग का बुनियादी ज्ञान
- आपकी मशीन पर Visual Studio स्थापित है
- .NET लाइब्रेरी के लिए Groupdocs.Parser तक पहुंच
- परीक्षण के लिए नमूना दस्तावेज़ फ़ाइल

## नामस्थान आयात करें
अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को शामिल करके आरंभ करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर आरंभ करें
 सबसे पहले, इसका एक उदाहरण बनाएं`Parser` अपने नमूना दस्तावेज़ फ़ाइल का पथ प्रदान करके class में लॉग इन करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // आपका कोड यहाँ
}
```
## चरण 2: दस्तावेज़ जानकारी प्राप्त करें
 दस्तावेज़ के बारे में जानकारी प्राप्त करने के लिए निम्न का उपयोग करें`GetDocumentInfo()` तरीका।
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## चरण 3: पृष्ठों पर पुनरावृत्ति करें और पाठ निकालें
दस्तावेज़ के प्रत्येक पृष्ठ पर पुनरावृत्ति करें और पाठ सामग्री निकालें।
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // पृष्ठ से पाठ निकालें
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## निष्कर्ष
अब आप जान चुके हैं कि रॉ मोड में दस्तावेज़ पृष्ठों से टेक्स्ट निकालने के लिए .NET के लिए Groupdocs.Parser का उपयोग कैसे करें। यह उन अनुप्रयोगों के लिए एक शक्तिशाली सुविधा हो सकती है जिन्हें विभिन्न फ़ाइल स्वरूपों से टेक्स्ट सामग्री का विश्लेषण या प्रक्रिया करने की आवश्यकता होती है।

## अक्सर पूछे जाने वाले प्रश्न
### क्या Groupdocs.Parser for .NET सभी फ़ाइल स्वरूपों के साथ संगत है?
Groupdocs.Parser PDF, DOCX, XLSX, PPTX, EPUB, आदि सहित फ़ाइल स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं इस लाइब्रेरी का उपयोग करके टेक्स्ट के साथ मेटाडेटा भी निकाल सकता हूँ?
हां, Groupdocs.Parser आपको दस्तावेज़ों से पाठ और मेटाडेटा दोनों निकालने की अनुमति देता है।
### क्या परीक्षण के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं Groupdocs.Parser के लिए तकनीकी सहायता कैसे प्राप्त कर सकता हूं?
 तकनीकी सहायता के लिए कृपया यहां जाएं[Groupdocs.Parser फ़ोरम](https://forum.groupdocs.com/c/parser/17).
### मैं .NET के लिए Groupdocs.Parser का लाइसेंस कहां से खरीद सकता हूं?
 आप लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy).