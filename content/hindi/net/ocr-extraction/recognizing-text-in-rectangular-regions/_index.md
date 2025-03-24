---
title: आयताकार क्षेत्रों में पाठ को पहचानना
linktitle: आयताकार क्षेत्रों में पाठ को पहचानना
second_title: GroupDocs.Parser .NET एपीआई
description: OCR क्षमताओं के साथ .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों के विशिष्ट क्षेत्रों में पाठ को पहचानना सीखें।
weight: 14
url: /hi/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---

# आयताकार क्षेत्रों में पाठ को पहचानना

## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि दस्तावेज़ों के विशिष्ट आयताकार क्षेत्रों में टेक्स्ट को पहचानने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को PDF, Word, Excel और PowerPoint सहित विभिन्न फ़ाइल स्वरूपों से टेक्स्ट, मेटाडेटा और बहुत कुछ निकालने की अनुमति देती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित सेटअप है:
-  .NET के लिए GroupDocs.Parser: लाइब्रेरी डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/parser/net/).
- विकास वातावरण: विजुअल स्टूडियो या कोई अन्य .NET IDE.
- नमूना दस्तावेज़: एक नमूना फ़ाइल (जैसे, PDF, DOCX) रखें जिसमें पहचाना जाने वाला पाठ हो।

## नामस्थान आयात करें
सबसे पहले, आपको अपने C# कोड में आवश्यक नेमस्पेस आयात करने होंगे:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर सेटिंग्स आरंभ करें
 सेटअप करके शुरू करें`ParserSettings` OCR कनेक्टर के साथ। यहाँ, हम Aspose OCR ऑन-प्रिमाइसेस कनेक्टर का उपयोग करेंगे:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## चरण 2: पार्सर इंस्टेंस बनाएँ
 इसके बाद, उदाहरण बनाएं`Parser` पहले से परिभाषित सेटिंग्स के साथ क्लास:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // कोड यहाँ जारी है
}
```
 प्रतिस्थापित करें`"YourSampleFile.pdf"` अपने दस्तावेज़ के पथ के साथ.
## चरण 3: OCR आयत को परिभाषित करें
 दस्तावेज़ के अंदर एक आयत परिभाषित करें जहाँ पाठ पहचान की जाएगी। उदाहरण के लिए, एक आयत जो शुरू होती है`(0, 0)` चौड़ाई के साथ`400` और ऊंचाई`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## चरण 4: पाठ पहचान विकल्प कॉन्फ़िगर करें
 बनाएं`TextOptions` परिभाषित आयत के साथ OCR उपयोग निर्दिष्ट करने के लिए:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## चरण 5: OCR का उपयोग करके टेक्स्ट निकालें
 उपयोग`GetText` की विधि`Parser` कॉन्फ़िगर किए गए उदाहरण के साथ`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // निकाला गया पाठ पढ़ें या 'समर्थित नहीं' मामले को संभालें
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने दिखाया है कि OCR का उपयोग करके दस्तावेज़ों में विशिष्ट आयताकार क्षेत्रों से टेक्स्ट निकालने के लिए .NET के लिए GroupDocs.Parser का लाभ कैसे उठाया जाए। इस प्रक्रिया को स्वचालित टेक्स्ट निष्कर्षण कार्यों के लिए विभिन्न अनुप्रयोगों में और अधिक अनुकूलित और एकीकृत किया जा सकता है।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser स्कैन किए गए दस्तावेज़ों से पाठ निकाल सकता है?
हां, GroupDocs.Parser स्कैन किए गए दस्तावेज़ों से पाठ निकालने के लिए OCR (ऑप्टिकल कैरेक्टर रिकॉग्निशन) का समर्थन करता है।
### GroupDocs.Parser किस फ़ाइल स्वरूप का समर्थन करता है?
GroupDocs.Parser पीडीएफ, DOCX, XLSX, PPTX, आदि सहित फ़ाइल स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### मैं उन दस्तावेज़ों को कैसे संभाल सकता हूँ जो पाठ निष्कर्षण के लिए समर्थित नहीं हैं?
 आप जाँच कर सकते हैं कि पाठ निष्कर्षण समर्थित है या नहीं`TextReader` द्वारा लौटाया गया उदाहरण`parser.GetText(options)`.
### क्या GroupDocs.Parser बड़े पैमाने पर पाठ निष्कर्षण कार्यों के लिए उपयुक्त है?
हां, GroupDocs.Parser को बड़े पैमाने पर पाठ निष्कर्षण कार्यों को कुशलतापूर्वक संभालने के लिए डिज़ाइन किया गया है।
### मुझे GroupDocs.Parser से संबंधित समस्याओं के लिए समर्थन कहां मिल सकता है?
 समर्थन और चर्चा के लिए, यहां जाएं[GroupDocs.Parser मंच](https://forum.groupdocs.com/c/parser/17).