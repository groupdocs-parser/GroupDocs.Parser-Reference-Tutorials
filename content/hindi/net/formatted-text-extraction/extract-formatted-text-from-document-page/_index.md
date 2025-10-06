---
title: दस्तावेज़ पृष्ठ से स्वरूपित पाठ निकालें
linktitle: दस्तावेज़ पृष्ठ से स्वरूपित पाठ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ पृष्ठों से स्वरूपित पाठ निकालें। कुशल और विश्वसनीय पाठ निष्कर्षण समाधान।
weight: 11
url: /hi/net/formatted-text-extraction/extract-formatted-text-from-document-page/
type: docs
---
# दस्तावेज़ पृष्ठ से स्वरूपित पाठ निकालें

## परिचय
इस ट्यूटोरियल में, हम आपको .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ पृष्ठों से स्वरूपित पाठ निकालने की प्रक्रिया के माध्यम से मार्गदर्शन करेंगे। यह लाइब्रेरी आपको PDF, Word, Excel और अन्य जैसे विभिन्न दस्तावेज़ स्वरूपों से कुशलतापूर्वक पार्स और पाठ निकालने की अनुमति देती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- आपके सिस्टम पर Visual Studio स्थापित है.
- C# प्रोग्रामिंग का बुनियादी ज्ञान.
-  .NET लाइब्रेरी के लिए GroupDocs.Parser. आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/parser/net/).

## नामस्थान आयात करें
सबसे पहले, अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस को आयात करके शुरुआत करें।
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 इसका एक उदाहरण बनाकर शुरू करें`Parser` अपनी नमूना फ़ाइल का पथ प्रदान करके class में लॉग इन करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // कोड यहाँ जाएगा
}
```
## चरण 2: जांचें कि क्या फ़ॉर्मेटेड टेक्स्ट एक्सट्रैक्शन समर्थित है
पाठ निष्कर्षण के साथ आगे बढ़ने से पहले, सत्यापित करें कि दस्तावेज़ स्वरूपित पाठ निष्कर्षण का समर्थन करता है या नहीं।
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## चरण 3: दस्तावेज़ जानकारी प्राप्त करें
दस्तावेज़ के बारे में जानकारी प्राप्त करें, जैसे पृष्ठों की संख्या।
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## चरण 4: दस्तावेज़ पृष्ठों पर पुनरावृत्ति करें और स्वरूपित पाठ निकालें
दस्तावेज़ के प्रत्येक पृष्ठ पर पुनरावृत्ति करें और निर्दिष्ट विकल्पों (जैसे, मार्कडाउन प्रारूप) का उपयोग करके स्वरूपित पाठ निकालें।
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## निष्कर्ष
अब आप जानते हैं कि .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ पृष्ठों से स्वरूपित पाठ कैसे निकाला जाता है। यह लाइब्रेरी विभिन्न फ़ाइल स्वरूपों से पाठ निष्कर्षण के लिए एक शक्तिशाली और उपयोग में आसान समाधान प्रदान करती है।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser विभिन्न फ़ाइल स्वरूपों को संभाल सकता है?
हां, GroupDocs.Parser पीडीएफ, DOCX, XLSX, PPTX, और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या GroupDocs.Parser .NET कोर के साथ संगत है?
हां, GroupDocs.Parser .NET कोर और .NET फ्रेमवर्क का समर्थन करता है।
### क्या GroupDocs.Parser निष्कर्षण के दौरान पाठ स्वरूपण को सुरक्षित रखता है?
हां, GroupDocs.Parser पाठ निकालते समय शैलियों और फ़ॉन्ट जैसे स्वरूपण को बनाए रख सकता है।
### क्या मैं GroupDocs.Parser का उपयोग करके छवियां और मेटाडेटा निकाल सकता हूं?
हां, GroupDocs.Parser दस्तावेज़ों से छवियों, मेटाडेटा और पाठ को निकालने की अनुमति देता है।
### मैं GroupDocs.Parser के लिए समर्थन कैसे प्राप्त कर सकता हूं?
 आप यहाँ से सहायता प्राप्त कर सकते हैं[GroupDocs.Parser मंच](https://forum.groupdocs.com/c/parser/17).