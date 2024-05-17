---
title: विषय-सूची (TOC) आइटम द्वारा पाठ निकालें
linktitle: विषय-सूची (TOC) आइटम द्वारा पाठ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके विषय-सूची (TOC) द्वारा पाठ निकालें। संरचित डेटा निष्कर्षण के लिए कुशल दस्तावेज़ पार्सिंग तकनीक सीखें।
type: docs
weight: 15
url: /hi/net/text-extraction/extract-text-by-toc-item/
---
## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि दस्तावेज़ों से विषय-सूची (TOC) आइटम पर आधारित टेक्स्ट निकालने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली उपकरण है जो कुशल दस्तावेज़ पार्सिंग और निष्कर्षण की अनुमति देता है।
## आवश्यक शर्तें
इस ट्यूटोरियल के साथ आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. विज़ुअल स्टूडियो: अपने सिस्टम पर विज़ुअल स्टूडियो IDE स्थापित करें।
2.  .NET के लिए GroupDocs.Parser: .NET के लिए GroupDocs.Parser को डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/parser/net/).
3. TOC के साथ एक नमूना दस्तावेज़: एक दस्तावेज़ (जैसे, PDF, DOCX) तैयार करें जिसमें विषय-सूची हो।

## नामस्थान आयात करना
सबसे पहले, अपने C# प्रोजेक्ट में आवश्यक नामस्थान शामिल करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 उदाहरण प्रस्तुत करें`Parser` अपने नमूना दस्तावेज़ के पथ के साथ क्लास:
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // अगले चरण यहां जारी रखें...
}
```
## चरण 2: विषय-सूची (TOC) निकालें
दस्तावेज़ से विषय-सूची (TOC) आइटम प्राप्त करें:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## चरण 3: TOC आइटम पर पुनरावृत्ति करें और टेक्स्ट निकालें
प्रत्येक TOC आइटम को पुनरावृत्त करें और संबंधित पाठ निकालें:
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## निष्कर्ष
इस ट्यूटोरियल में दिखाया गया है कि .NET के लिए GroupDocs.Parser का उपयोग करके टेबल ऑफ़ कंटेंट (TOC) आइटम पर आधारित दस्तावेज़ से टेक्स्ट कैसे निकाला जाता है। बताए गए चरणों का पालन करके, आप अपने दस्तावेज़ों से प्रोग्रामेटिक रूप से विशिष्ट सामग्री को कुशलतापूर्वक पार्स और निकाल सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### GroupDocs.Parser किस फ़ाइल स्वरूप का समर्थन करता है?
GroupDocs.Parser पीडीएफ, माइक्रोसॉफ्ट वर्ड (DOC/DOCX), एक्सेल (XLS/XLSX), पावरपॉइंट (PPT/PPTX), और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं GroupDocs.Parser का उपयोग करके तालिकाओं या छवियों जैसे संरचित डेटा को निकाल सकता हूं?
हां, GroupDocs.Parser विभिन्न दस्तावेज़ प्रकारों से तालिकाओं, छवियों और मेटाडेटा जैसे संरचित डेटा निकालने के लिए API प्रदान करता है।
### क्या GroupDocs.Parser बड़े दस्तावेज़ों के लिए उपयुक्त है?
GroupDocs.Parser बड़े दस्तावेज़ों को कुशलतापूर्वक संभालने के लिए अनुकूलित है, जिससे व्यापक फ़ाइलों से सामग्री को निर्बाध रूप से निकालना संभव हो जाता है।
### मैं GroupDocs.Parser के लिए तकनीकी सहायता कैसे प्राप्त कर सकता हूं?
 आप तकनीकी सहायता प्राप्त कर सकते हैं और समुदाय के साथ बातचीत कर सकते हैं[GroupDocs.Parser फ़ोरम](https://forum.groupdocs.com/c/parser/17).
### क्या ग्रुपडॉक्स मूल्यांकन के लिए निःशुल्क परीक्षण प्रदान करता है?
हां, आप GroupDocs.Parser का एक निःशुल्क परीक्षण संस्करण यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).