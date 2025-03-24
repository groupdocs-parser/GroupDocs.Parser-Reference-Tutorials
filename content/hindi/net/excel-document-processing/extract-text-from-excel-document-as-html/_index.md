---
title: Excel दस्तावेज़ से HTML के रूप में पाठ निकालें
linktitle: Excel दस्तावेज़ से HTML के रूप में पाठ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके Excel दस्तावेज़ों से टेक्स्ट निकालना और उसे HTML में परिवर्तित करना सीखें।
weight: 13
url: /hi/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Parser का उपयोग करके Excel दस्तावेज़ से टेक्स्ट निकालने और उसे HTML फ़ॉर्मेट में बदलने का तरीका जानेंगे। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को विभिन्न दस्तावेज़ फ़ॉर्मेट के साथ काम करने, टेक्स्ट और मेटाडेटा को कुशलतापूर्वक निकालने की अनुमति देती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित सेटअप है:
- आपके सिस्टम पर Visual Studio स्थापित है.
- C# प्रोग्रामिंग की बुनियादी समझ.
-  .NET के लिए GroupDocs.Parser लाइब्रेरी। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/parser/net/).
## नामस्थान आयात करें
GroupDocs.Parser कार्यात्मकताओं तक पहुंचने के लिए अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को शामिल करके प्रारंभ करें।
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 सबसे पहले, उदाहरण दें`Parser` अपने एक्सेल दस्तावेज़ का पथ प्रदान करके क्लास को सक्रिय करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // आगे का कोड यहाँ जाएगा
}
```
 प्रतिस्थापित करें`"YourSampleFile.xlsx"` अपनी एक्सेल फ़ाइल के पथ के साथ.
## चरण 2: टेक्स्ट को HTML के रूप में निकालें
 के अंदर`using` ब्लॉक का`Parser` उदाहरण के लिए, का उपयोग करें`GetFormattedText` HTML मोड में स्वरूपित पाठ निकालने की विधि।
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // आगे का कोड यहाँ जाएगा
    }
}
```
## चरण 3: निकाले गए HTML पाठ को पढ़ें और प्रिंट करें
 इसके बाद, निकाले गए HTML पाठ को पढ़ें`TextReader` और इसे कंसोल पर प्रिंट करें.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
एक बार निष्पादित होने के बाद, यह कोड एक्सेल दस्तावेज़ से पाठ निकालेगा और इसे कंसोल में HTML प्रारूप में प्रदर्शित करेगा।
## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि Excel दस्तावेज़ से टेक्स्ट निकालने और उसे HTML फ़ॉर्मेट में बदलने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। यह लाइब्रेरी विभिन्न दस्तावेज़ फ़ॉर्मेट के साथ काम करने का एक सीधा तरीका प्रदान करती है, जिससे डेवलपर्स अपने अनुप्रयोगों में टेक्स्ट निष्कर्षण कार्यों को कुशलतापूर्वक संभालने में सक्षम होते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser Excel के अलावा अन्य दस्तावेज़ स्वरूपों को भी संभाल सकता है?
हां, GroupDocs.Parser पीडीएफ, वर्ड, पावरपॉइंट और अन्य सहित फ़ाइल स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या GroupDocs.Parser .NET कोर के साथ संगत है?
हां, GroupDocs.Parser .NET फ्रेमवर्क और .NET कोर दोनों के साथ संगत है।
### क्या GroupDocs.Parser पाठ निष्कर्षण के दौरान स्वरूपण को सुरक्षित रखता है?
हां, GroupDocs.Parser पाठ निष्कर्षण के दौरान फ़ॉन्ट, शैली और लेआउट जैसे स्वरूपण को संरक्षित कर सकता है।
### क्या मैं GroupDocs.Parser का उपयोग करके दस्तावेज़ों से मेटाडेटा निकाल सकता हूँ?
हां, GroupDocs.Parser समर्थित दस्तावेज़ प्रकारों से लेखक, निर्माण तिथि और अधिक जैसे मेटाडेटा निकालने की अनुमति देता है।
### क्या GroupDocs.Parser के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हां, आप यहां से निःशुल्क परीक्षण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).