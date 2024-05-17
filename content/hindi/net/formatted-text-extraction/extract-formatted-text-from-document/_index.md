---
title: दस्तावेज़ से स्वरूपित पाठ निकालें
linktitle: दस्तावेज़ से स्वरूपित पाठ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से स्वरूपित पाठ निकालना सीखें। आपके अनुप्रयोगों के लिए सरल और कुशल पाठ निष्कर्षण।
type: docs
weight: 10
url: /hi/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## परिचय
इस ट्यूटोरियल में, हम विभिन्न प्रकार के दस्तावेज़ों से स्वरूपित पाठ निकालने के लिए .NET के लिए GroupDocs.Parser का उपयोग करने का तरीका जानेंगे। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को सरल और कुशल तरीके से दस्तावेज़ों के साथ काम करने की अनुमति देती है। इस गाइड के अंत तक, आप अपने .NET अनुप्रयोगों में पाठ निष्कर्षण क्षमताओं को सहजता से एकीकृत करने में सक्षम होंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- विज़ुअल स्टूडियो: सुनिश्चित करें कि आपके सिस्टम पर विज़ुअल स्टूडियो स्थापित है।
-  .NET के लिए GroupDocs.Parser: GroupDocs.Parser लाइब्रेरी को डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/parser/net/).
- दस्तावेज़ नमूने: पाठ निष्कर्षण के लिए नमूना दस्तावेज़ (जैसे, PDF, DOCX) तैयार करें।
## नामस्थान आयात करें
सबसे पहले, अपने C# कोड में आवश्यक नामस्थान शामिल करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 आरंभ करने से शुरू करें`Parser` अपने नमूना दस्तावेज़ के पथ के साथ ऑब्जेक्ट।
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // पाठ निष्कर्षण कोड यहाँ है
}
```
 प्रतिस्थापित करें`"YourSampleFile.pdf"` अपने दस्तावेज़ फ़ाइल के पथ के साथ.

## चरण 2: स्वरूपित पाठ निकालें
 के अंदर`using` ब्लॉक, का उपयोग करें`GetFormattedText` दस्तावेज़ से स्वरूपित पाठ निकालने की विधि। वांछित आउटपुट प्रारूप (जैसे, HTML) निर्दिष्ट करें`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // स्वरूपित पाठ को रीडर में निकालें
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // जाँचें कि क्या निष्कर्षण समर्थित है
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // निकाले गए पाठ को पढ़ें और प्रदर्शित करें
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## निष्कर्ष
बधाई हो! आपने .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से फ़ॉर्मेट किए गए टेक्स्ट को निकालना सीख लिया है। यह बहुमुखी लाइब्रेरी आपके अनुप्रयोगों के भीतर टेक्स्ट प्रोसेसिंग और विश्लेषण के लिए संभावनाएँ खोलती है।

## अक्सर पूछे जाने वाले प्रश्न
### प्रश्न: क्या GroupDocs.Parser पासवर्ड-संरक्षित दस्तावेज़ों से पाठ निकाल सकता है?
उत्तर: हां, GroupDocs.Parser पासवर्ड-संरक्षित दस्तावेज़ों से पाठ निकालने का समर्थन करता है।
### प्रश्न: GroupDocs.Parser द्वारा कौन से दस्तावेज़ प्रारूप समर्थित हैं?
A: GroupDocs.Parser पीडीएफ, DOCX, XLSX, PPTX, और अधिक सहित प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### प्रश्न: मैं GroupDocs.Parser के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 उत्तर: आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### प्रश्न: क्या GroupDocs.Parser दस्तावेज़ों से छवि निष्कर्षण के लिए समर्थन प्रदान करता है?
उत्तर: हां, GroupDocs.Parser पाठ निष्कर्षण के साथ-साथ छवि निष्कर्षण का समर्थन करता है।
### प्रश्न: मैं अतिरिक्त सहायता कहां पा सकता हूं या GroupDocs.Parser के बारे में प्रश्न पूछ सकता हूं?
 उत्तर: यहाँ जाएँ[GroupDocs.Parser मंच](https://forum.groupdocs.com/c/parser/17)समर्थन और चर्चा के लिए।