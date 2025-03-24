---
title: Word दस्तावेज़ से HTML के रूप में पाठ निकालें
linktitle: Word दस्तावेज़ से HTML के रूप में पाठ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: Word दस्तावेज़ों से टेक्स्ट निकालने और उसे HTML के रूप में सहेजने के लिए .NET के लिए GroupDocs.Parser का उपयोग करना सीखें। कोड उदाहरणों के साथ चरण-दर-चरण ट्यूटोरियल।
weight: 16
url: /hi/net/word-document-processing/extract-text-from-word-document-as-html/
---

# Word दस्तावेज़ से HTML के रूप में पाठ निकालें

## परिचय
.NET के लिए GroupDocs.Parser एक शक्तिशाली दस्तावेज़ पार्सिंग लाइब्रेरी है जो डेवलपर्स को विभिन्न फ़ाइल स्वरूपों से टेक्स्ट और मेटाडेटा को सहजता से निकालने में सक्षम बनाती है। इस ट्यूटोरियल में, हम Word दस्तावेज़ों से टेक्स्ट निकालने और इसे HTML के रूप में सहेजने के लिए GroupDocs.Parser का लाभ उठाने पर ध्यान केंद्रित करेंगे। यह प्रक्रिया सामग्री विश्लेषण, अनुक्रमण या दस्तावेज़ों को वेब-अनुकूल स्वरूपों में परिवर्तित करने जैसे कार्यों के लिए आवश्यक है। इस गाइड के अंत तक, आपको अपने .NET अनुप्रयोगों में GroupDocs.Parser का कुशलतापूर्वक उपयोग करने के तरीके की स्पष्ट समझ होगी।
## आवश्यक शर्तें
इस ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- C# प्रोग्रामिंग का बुनियादी ज्ञान.
- आपके विकास मशीन पर Visual Studio स्थापित है।
-  .NET लाइब्रेरी के लिए GroupDocs.Parser. आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/parser/net/).
- परीक्षण प्रयोजनों के लिए नमूना वर्ड दस्तावेज़ तक पहुंच।
## नामस्थान आयात करें
आरंभ करने के लिए, आपको अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करने होंगे:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
किसी Word दस्तावेज़ से पाठ निकालने और उसे .NET के लिए GroupDocs.Parser का उपयोग करके HTML के रूप में सहेजने के लिए इन विस्तृत चरणों का पालन करें:
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 सबसे पहले, इसका एक उदाहरण बनाएं`Parser` अपने नमूना Word दस्तावेज़ का पथ प्रदान करके क्लास में जाएँ:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // चरण 2 पर जारी रखें...
}
```
 प्रतिस्थापित करें`"YourSampleFile.docx"`अपने वर्ड दस्तावेज़ के पथ के साथ.
## चरण 2: स्वरूपित पाठ को HTML के रूप में निकालें
 इसके बाद, का उपयोग करें`GetFormattedText` विधि के साथ-साथ`FormattedTextOptions`HTML प्रारूप में पाठ निकालने के लिए:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // स्वरूपित पाठ को रीडर में निकालें
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // चरण 3 पर जारी रखें...
    }
}
```
## चरण 3: निकाले गए HTML को पढ़ें और आउटपुट करें
 अंत में, निकाले गए HTML सामग्री को पढ़ें`TextReader` और इसे कंसोल पर प्रिंट करें:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // स्वरूपित पाठ को रीडर में निकालें
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // स्वरूपित पाठ को HTML के रूप में प्रिंट करें
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Parser का उपयोग करके Word दस्तावेज़ से टेक्स्ट निकालने और उसे HTML के रूप में सहेजने का तरीका खोजा है। यह लाइब्रेरी दस्तावेज़ सामग्री को पार्स करने का एक सीधा और कुशल तरीका प्रदान करती है, जो इसे .NET अनुप्रयोगों में दस्तावेज़ प्रसंस्करण कार्यों के लिए एक अमूल्य उपकरण बनाती है।

## अक्सर पूछे जाने वाले प्रश्न
### मैं GroupDocs.Parser के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप अस्थायी लाइसेंस का अनुरोध कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### मैं GroupDocs.Parser के लिए अधिक दस्तावेज़ कहां पा सकता हूं?
 विस्तृत दस्तावेज उपलब्ध है[यहाँ](https://tutorials.groupdocs.com/parser/net/).
### क्या GroupDocs.Parser के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हां, आप निःशुल्क परीक्षण संस्करण का उपयोग कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं GroupDocs.Parser के लिए समर्थन कैसे प्राप्त करूं?
 सहायता फ़ोरम पर जाएँ[यहाँ](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser किस प्रकार के दस्तावेज़ों का समर्थन करता है?
GroupDocs.Parser वर्ड, पीडीएफ, एक्सेल, पावरपॉइंट और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है।