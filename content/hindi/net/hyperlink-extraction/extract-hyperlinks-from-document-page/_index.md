---
title: दस्तावेज़ पृष्ठ से हाइपरलिंक निकालें
linktitle: दस्तावेज़ पृष्ठ से हाइपरलिंक निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से हाइपरलिंक निकालने का तरीका जानें। C# में हाइपरलिंक निकालने के लिए चरण-दर-चरण मार्गदर्शिका।
weight: 11
url: /hi/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
type: docs
---
# दस्तावेज़ पृष्ठ से हाइपरलिंक निकालें

## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों से हाइपरलिंक्स को चरण-दर-चरण कैसे निकाला जाए। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को विभिन्न दस्तावेज़ प्रारूपों को पार्स करने और टेक्स्ट, मेटाडेटा और अन्य तत्वों को निकालने में सक्षम बनाती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- विज़ुअल स्टूडियो: अपने विकास मशीन पर विज़ुअल स्टूडियो स्थापित करें।
-  GroupDocs.Parser लाइब्रेरी: GroupDocs.Parser लाइब्रेरी डाउनलोड करें और उसका संदर्भ लें। आप इसे यहाँ से प्राप्त कर सकते हैं[यहाँ](https://releases.groupdocs.com/parser/net/).
- नमूना दस्तावेज़: परीक्षण के लिए हाइपरलिंक युक्त एक नमूना दस्तावेज़ (जैसे, DOCX, PDF) तैयार करें।

## नामस्थान आयात करें
सबसे पहले, GroupDocs.Parser कार्यक्षमताओं का उपयोग करने के लिए आवश्यक नामस्थान शामिल करें:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर इंस्टेंस बनाएँ
 उदाहरण प्रस्तुत करें`Parser` अपने नमूना दस्तावेज़ के पथ के साथ क्लास बनाएँ।
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // कोड यहाँ है...
}
```
## चरण 2: हाइपरलिंक निष्कर्षण समर्थन की जाँच करें
आगे बढ़ने से पहले सुनिश्चित करें कि दस्तावेज़ हाइपरलिंक निष्कर्षण का समर्थन करता है।
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## चरण 3: दस्तावेज़ जानकारी प्राप्त करें
दस्तावेज़ के बारे में बुनियादी जानकारी प्राप्त करें और जाँचें कि उसमें पृष्ठ हैं या नहीं।
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## चरण 4: दस्तावेज़ पृष्ठों पर पुनरावृत्ति करें
दस्तावेज़ के प्रत्येक पृष्ठ को पुनरावृत्त करें।
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // वर्तमान पृष्ठ से हाइपरलिंक निकालें
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // निकाले गए हाइपरलिंक पर पुनरावृति करें
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // पठनीयता के लिए रिक्त पंक्ति
    }
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने दस्तावेज़ों से हाइपरलिंक निकालने के लिए .NET के लिए GroupDocs.Parser का उपयोग करने की मूल बातें कवर की हैं। आपने सीखा कि कैसे पार्सर को आरंभीकृत किया जाए, हाइपरलिंक समर्थन की जांच की जाए, दस्तावेज़ जानकारी प्राप्त की जाए, और हाइपरलिंक को कुशलतापूर्वक निकालने के लिए दस्तावेज़ पृष्ठों के माध्यम से पुनरावृति की जाए।

## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं विभिन्न दस्तावेज़ प्रारूपों से हाइपरलिंक निकाल सकता हूँ?
हां, GroupDocs.Parser हाइपरलिंक निष्कर्षण के लिए DOCX, PDF, PPTX आदि जैसे विभिन्न स्वरूपों का समर्थन करता है।
### क्या GroupDocs.Parser मौजूदा .NET अनुप्रयोगों में एकीकृत करना आसान है?
बिल्कुल, GroupDocs.Parser को सीधा बनाया गया है और इसे आसानी से आपके .NET प्रोजेक्ट्स में एकीकृत किया जा सकता है।
### क्या मैं GroupDocs.Parser का उपयोग करके हाइपरलिंक के साथ अन्य मेटाडेटा निकाल सकता हूं?
हां, हाइपरलिंक के अलावा, आप इस लाइब्रेरी का उपयोग करके दस्तावेज़ों से पाठ, चित्र और मेटाडेटा निकाल सकते हैं।
### क्या GroupDocs.Parser एन्क्रिप्टेड या पासवर्ड-संरक्षित दस्तावेज़ों को संभालता है?
यदि पासवर्ड प्रदान किया गया है तो GroupDocs.Parser पासवर्ड-संरक्षित दस्तावेज़ों को पार्स कर सकता है।
### क्या खरीदने से पहले परीक्षण के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).