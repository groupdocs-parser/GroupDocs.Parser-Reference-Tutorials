---
title: विकल्पों के साथ विशिष्ट क्षेत्रों से पाठ निकालें
linktitle: विकल्पों के साथ विशिष्ट क्षेत्रों से पाठ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों में विशिष्ट क्षेत्रों से टेक्स्ट निकालने का तरीका जानें। इस ट्यूटोरियल के साथ उन्नत टेक्स्ट निष्कर्षण विकल्पों का अन्वेषण करें।
type: docs
weight: 14
url: /hi/net/text-extraction/extract-text-from-specific-areas-with-options/
---
## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि कस्टमाइज़ करने योग्य विकल्पों का उपयोग करके दस्तावेज़ के भीतर विशिष्ट क्षेत्रों से टेक्स्ट निकालने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को विभिन्न दस्तावेज़ प्रारूपों से आसानी से टेक्स्ट को पार्स और निकालने में सक्षम बनाती है।
## आवश्यक शर्तें
इससे पहले कि हम कोडिंग में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1. विकास वातावरण: विज़ुअल स्टूडियो या कोई अन्य .NET विकास IDE स्थापित करें।
2.  GroupDocs.Parser लाइब्रेरी: .NET के लिए GroupDocs.Parser डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/parser/net/).
3. नमूना फ़ाइल: पाठ निकालने के लिए एक नमूना दस्तावेज़ (जैसे, PDF, DOCX, आदि) तैयार करें।

## नामस्थान आयात करें
सबसे पहले, आपको GroupDocs.Parser वर्गों और विधियों तक पहुँचने के लिए आवश्यक नामस्थानों को आयात करना होगा।
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 का एक उदाहरण आरंभ करें`Parser` अपनी नमूना फ़ाइल का पथ प्रदान करके class में लॉग इन करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // टेक्स्ट क्षेत्र निष्कर्षण के लिए कोड यहां जाएगा
}
```
## चरण 2: टेक्स्ट क्षेत्र निष्कर्षण विकल्प परिभाषित करें
 बनाएं`PageTextAreaOptions` पाठ निष्कर्षण के लिए मानदंड निर्दिष्ट करने के लिए.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
इस उदाहरण में:
- `"\\s[a-z]{2}\\s"` केवल लोअरकेस अक्षरों वाले पाठ क्षेत्रों से मिलान करने के लिए एक नियमित अभिव्यक्ति पैटर्न है।
- `new Rectangle(new Point(0, 0), new Size(300, 100))` पृष्ठ पर आयत (स्थिति और आकार) को परिभाषित करता है, जहाँ से पाठ निकालना है।
## चरण 3: पाठ क्षेत्र निकालें
निर्दिष्ट मानदंडों को पूरा करने वाले पाठ क्षेत्रों को निकालने के लिए परिभाषित विकल्पों का उपयोग करें।
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## चरण 4: निकाले गए पाठ क्षेत्रों की जाँच करें और उन पर पुनरावृत्ति करें
जाँच करें कि क्या पाठ क्षेत्र निष्कर्षण समर्थित है और फिर निकाले गए क्षेत्रों पर पुनरावृत्ति करें।
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ के भीतर विशिष्ट क्षेत्रों से टेक्स्ट निकालने का तरीका बताया है। यह लाइब्रेरी विभिन्न दस्तावेज़ प्रारूपों को पार्स करने के लिए व्यापक क्षमताएँ प्रदान करती है, जिससे यह टेक्स्ट निष्कर्षण कार्यों के लिए एक मूल्यवान उपकरण बन जाता है।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser स्कैन किए गए दस्तावेज़ों से पाठ निकाल सकता है?
हां, GroupDocs.Parser स्कैन किए गए दस्तावेज़ों के लिए OCR-आधारित पाठ निष्कर्षण का समर्थन करता है।
### क्या GroupDocs.Parser एकाधिक दस्तावेज़ प्रारूपों के साथ संगत है?
हां, यह PDF, DOCX, XLSX, PPTX और अन्य लोकप्रिय प्रारूपों से पाठ को पार्स और निकाल सकता है।
### क्या GroupDocs.Parser .NET कोर के लिए समर्थन प्रदान करता है?
हां, GroupDocs.Parser .NET कोर के साथ-साथ .NET फ्रेमवर्क के साथ भी संगत है।
### क्या मैं GroupDocs.Parser का उपयोग करके पाठ के साथ मेटाडेटा निकाल सकता हूँ?
हां, आप दस्तावेज़ों से पाठ्य सामग्री और मेटाडेटा दोनों निकाल सकते हैं।
### क्या GroupDocs.Parser के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से निःशुल्क परीक्षण प्राप्त कर सकते हैं[यहाँ](https://releases.groupdocs.com/).