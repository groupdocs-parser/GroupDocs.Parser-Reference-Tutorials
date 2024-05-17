---
title: मार्कडाउन सामग्री निकालें
linktitle: मार्कडाउन सामग्री निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से Markdown सामग्री निकालने का तरीका जानें। यह ट्यूटोरियल सहज पाठ निष्कर्षण के लिए चरण-दर-चरण निर्देश प्रदान करता है।
type: docs
weight: 13
url: /hi/net/formatted-text-extraction/extract-markdown-content/
---
## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि दस्तावेज़ों से मार्कडाउन सामग्री निकालने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को विभिन्न फ़ाइल स्वरूपों से टेक्स्ट को सहजता से पार्स और निकालने की अनुमति देती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- विज़ुअल स्टूडियो: अपने सिस्टम पर विज़ुअल स्टूडियो स्थापित करें।
-  .NET के लिए GroupDocs.Parser: से GroupDocs.Parser डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/parser/net/).
- C# की बुनियादी समझ: C# प्रोग्रामिंग भाषा से परिचित होना।

## नामस्थान आयात करें
सबसे पहले, आपको अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करने होंगे:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 उदाहरण प्रस्तुत करें`Parser` अपनी नमूना फ़ाइल के पथ के साथ क्लास:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // कोड यहाँ है...
}
```
## चरण 2: मार्कडाउन स्वरूपित पाठ निकालें
 के अंदर`using`ब्लॉक करें, उपयोग करें`GetFormattedText` स्वरूपित पाठ को मार्कडाउन के रूप में निकालने की विधि:
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Markdown)))
{
    // कोड यहाँ है...
}
```
## चरण 3: निकाली गई सामग्री को पढ़ें और आउटपुट करें
 से निकाली गई मार्कडाउन सामग्री पढ़ें`TextReader`:
```csharp
string markdownContent = reader == null ? "Formatted text extraction isn't supported" : reader.ReadToEnd();
Console.WriteLine(markdownContent);
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा है कि .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से मार्कडाउन सामग्री कैसे निकालें। यह शक्तिशाली लाइब्रेरी पार्सिंग और टेक्स्ट निकालने की प्रक्रिया को सरल बनाती है, जिससे डेवलपर्स विभिन्न फ़ाइल स्वरूपों के साथ कुशलतापूर्वक काम कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser विभिन्न फ़ाइल स्वरूपों को संभाल सकता है?
हां, GroupDocs.Parser DOCX, PDF, PPTX, XLSX और अधिक सहित फ़ाइल स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या GroupDocs.Parser .NET कोर के साथ संगत है?
हां, GroupDocs.Parser .NET फ्रेमवर्क और .NET कोर दोनों का समर्थन करता है।
### मैं GroupDocs.Parser के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### क्या GroupDocs.Parser डेवलपर्स के लिए समर्थन प्रदान करता है?
 हां, आप डेवलपर सहायता प्राप्त कर सकते हैं[ग्रुपडॉक्स फोरम](https://forum.groupdocs.com/c/parser/17).
### मैं GroupDocs.Parser के लिए लाइसेंस कहां से खरीद सकता हूं?
 आप लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy).