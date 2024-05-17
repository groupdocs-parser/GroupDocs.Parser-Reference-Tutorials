---
title: दस्तावेज़ पृष्ठ से तालिकाएँ निकालें
linktitle: दस्तावेज़ पृष्ठ से तालिकाएँ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके प्रोग्रामेटिक रूप से दस्तावेज़ों से तालिकाएँ निकालना सीखें। यह व्यापक ट्यूटोरियल चरण-दर-चरण मार्गदर्शन प्रदान करता है।
type: docs
weight: 11
url: /hi/net/table-extraction/extract-tables-from-document-page/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ पृष्ठ से तालिकाएँ निकालने का तरीका जानेंगे। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को PDF, DOCX, XLSX और अन्य जैसे विभिन्न दस्तावेज़ प्रारूपों के साथ काम करने की अनुमति देती है। इसकी सुविधाओं का लाभ उठाकर, हम इन दस्तावेज़ों से तालिकाओं जैसे संरचित डेटा को कुशलतापूर्वक निकाल सकते हैं, जिससे हमें प्रोग्रामेटिक रूप से जानकारी में हेरफेर और विश्लेषण करने में मदद मिलती है।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- आपके मशीन पर Visual Studio स्थापित है.
- C# और .NET विकास की बुनियादी समझ।
-  .NET लाइब्रेरी के लिए GroupDocs.Parser. आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/parser/net/).
- निष्कर्षण के लिए तालिकाओं वाले नमूना दस्तावेज़ (पीडीएफ, डीओसीएक्स, आदि) तक पहुंच।

## नामस्थान आयात करें
सबसे पहले, अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करके शुरुआत करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 उदाहरण प्रस्तुत करें`Parser` अपने नमूना दस्तावेज़ का पथ प्रदान करके class में जोड़ें:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //आपका कोड यहां जारी है...
}
```
## चरण 2: दस्तावेज़ तालिका निष्कर्षण समर्थन की जाँच करें
आगे बढ़ने से पहले, सत्यापित करें कि दस्तावेज़ तालिका निष्कर्षण का समर्थन करता है या नहीं:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## चरण 3: तालिका लेआउट परिभाषित करें
दस्तावेज़ से निकाले जाने वाले टेबल का लेआउट निर्धारित करें। अपने दस्तावेज़ की संरचना के अनुसार कॉलम की चौड़ाई और पंक्ति की ऊँचाई निर्दिष्ट करें:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // स्तंभ की चौड़ाई
    new double[] { 325, 340, 365, 395 });         // पंक्ति की ऊंचाई
```
## चरण 4: तालिका निष्कर्षण विकल्प कॉन्फ़िगर करें
निर्दिष्ट लेआउट का उपयोग करके तालिका निष्कर्षण के लिए विकल्प बनाएँ:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## चरण 5: दस्तावेज़ जानकारी प्राप्त करें
पृष्ठों की संख्या सहित दस्तावेज़ के बारे में जानकारी प्राप्त करें:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## चरण 6: दस्तावेज़ पृष्ठों पर पुनरावृत्ति करें
तालिकाओं को निकालने के लिए दस्तावेज़ के प्रत्येक पृष्ठ पर पुनरावृत्ति करें:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // वर्तमान पृष्ठ से तालिकाएँ निकालें
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // निकाले गए तालिकाओं पर पुनरावृति करें
    foreach (PageTableArea table in tables)
    {
        // तालिका की पंक्तियों पर पुनरावृत्ति करें
        for (int row = 0; row < table.RowCount; row++)
        {
            // तालिका के स्तंभों पर पुनरावृति करें
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // तालिका सेल प्राप्त करें
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // तालिका सेल का पाठ प्रिंट करें
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ पृष्ठों से तालिकाएँ निकालने की प्रक्रिया को कवर किया है। दिए गए चरणों का पालन करके, आप अपने .NET अनुप्रयोगों में तालिका निष्कर्षण कार्यक्षमता को सहजता से एकीकृत कर सकते हैं, जिससे दस्तावेज़ों के भीतर संरचित डेटा के कुशल संचालन और हेरफेर को सक्षम किया जा सके।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser सभी प्रकार के दस्तावेज़ों से तालिकाएँ निकाल सकता है?
GroupDocs.Parser विभिन्न दस्तावेज़ स्वरूपों जैसे PDF, DOCX, XLSX आदि का समर्थन करता है, जिससे संगत फ़ाइल प्रकारों से तालिका निष्कर्षण सक्षम होता है।
### क्या GroupDocs.Parser for .NET बड़े पैमाने पर दस्तावेज़ प्रसंस्करण के लिए उपयुक्त है?
हां, GroupDocs.Parser को बड़े दस्तावेज़ों को कुशलतापूर्वक संभालने के लिए डिज़ाइन किया गया है, जो इसे व्यापक डेटासेट के प्रसंस्करण के लिए उपयुक्त बनाता है।
### क्या GroupDocs.Parser तालिका निष्कर्षण के दौरान स्वरूपण को सुरक्षित रखता है?
हां, GroupDocs.Parser तालिका निष्कर्षण के दौरान सेल सीमाओं, पाठ शैलियों और संरेखण जैसे स्वरूपण विवरण को बरकरार रखता है।
### क्या मैं सामग्री मानदंड के आधार पर विशिष्ट तालिकाएँ निकाल सकता हूँ?
GroupDocs.Parser निष्कर्षण के लिए लेआउट टेम्पलेट्स या सामग्री शर्तों के आधार पर विशिष्ट तालिकाओं को लक्षित करने के लिए लचीले विकल्प प्रदान करता है।
### क्या GroupDocs.Parser .NET कोर के साथ संगत है?
हां, GroupDocs.Parser .NET फ्रेमवर्क और .NET कोर वातावरण दोनों के साथ संगत है।