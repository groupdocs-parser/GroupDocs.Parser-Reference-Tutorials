---
title: दस्तावेज़ से तालिकाएँ निकालें
linktitle: दस्तावेज़ से तालिकाएँ निकालें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए Groupdocs.Parser का उपयोग करके दस्तावेज़ों से तालिकाएँ निकालने का तरीका जानें। इस कार्यक्षमता को एकीकृत करने के बारे में विस्तृत मार्गदर्शिका के लिए आगे बढ़ें।
weight: 10
url: /hi/net/table-extraction/extract-tables-from-document/
---
## परिचय
.NET के लिए Groupdocs.Parser एक व्यापक लाइब्रेरी है जो दस्तावेज़ पार्सिंग की सुविधा प्रदान करती है, जिससे आप दस्तावेज़ों से तालिकाएँ, पाठ, मेटाडेटा और बहुत कुछ जैसी मूल्यवान जानकारी निकाल सकते हैं। इस ट्यूटोरियल में, हम Groupdocs.Parser API का उपयोग करके दस्तावेज़ों से तालिकाएँ निकालने पर विशेष रूप से ध्यान केंद्रित करते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- आपके सिस्टम पर Visual Studio स्थापित है.
- .NET फ्रेमवर्क या .NET कोर स्थापित.
- C# प्रोग्रामिंग का बुनियादी ज्ञान.

## नामस्थान आयात करें
सबसे पहले, आपको Groupdocs.Parser क्लासेस और विधियों तक पहुंचने के लिए आवश्यक नामस्थानों को आयात करना होगा।
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
 का एक नया उदाहरण आरंभ करें`Parser` अपने नमूना दस्तावेज़ का पथ प्रदान करके class में लॉग इन करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // आपका कोड यहां जाएगा
}
```
## चरण 2: तालिका निष्कर्षण समर्थन की जाँच करें
 सत्यापित करें कि क्या दस्तावेज़ तालिका निष्कर्षण का समर्थन करता है`Features` की संपत्ति`Parser` कक्षा।
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## चरण 3: तालिका लेआउट परिभाषित करें
उन तालिकाओं का लेआउट परिभाषित करें जिन्हें आप निकालना चाहते हैं`TemplateTableLayout`अपने दस्तावेज़ की संरचना के आधार पर स्तंभ की चौड़ाई और पंक्ति की ऊँचाई निर्दिष्ट करें।
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## चरण 4: तालिका निष्कर्षण विकल्प सेट करें
 बनाएं`PageTableAreaOptions` तालिकाओं को कैसे निकाला जाना चाहिए यह निर्दिष्ट करने के लिए परिभाषित लेआउट के साथ।
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## चरण 5: तालिकाएँ निकालें
 उपयोग करें`GetTables` की विधि`Parser` निर्दिष्ट विकल्पों के आधार पर दस्तावेज़ से तालिकाएँ निकालने के लिए क्लास।
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## चरण 6: तालिका डेटा को पुनरावृत्त करें और एक्सेस करें
सेल डेटा तक पहुंचने के लिए निकाले गए तालिकाओं और उनकी संबंधित पंक्तियों और स्तंभों के माध्यम से पुनरावृति करें।
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## निष्कर्ष
इस ट्यूटोरियल में, हमने बताया है कि दस्तावेज़ों से तालिकाओं को कुशलतापूर्वक निकालने के लिए .NET के लिए Groupdocs.Parser का उपयोग कैसे करें। इस लाइब्रेरी की क्षमताओं का लाभ उठाते हुए, आप अपने .NET अनुप्रयोगों में तालिका निष्कर्षण को सहजता से एकीकृत कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### क्या Groupdocs.Parser विभिन्न दस्तावेज़ स्वरूपों को संभाल सकता है?
हां, Groupdocs.Parser DOCX, PDF, XLSX, और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या .NET के लिए Groupdocs.Parser का कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से निःशुल्क परीक्षण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं Groupdocs.Parser से संबंधित प्रश्नों के लिए समर्थन कैसे प्राप्त कर सकता हूं?
 आप यहां जा सकते हैं[Groupdocs.Parser फ़ोरम](https://forum.groupdocs.com/c/parser/17) सहायता के लिए।
### मैं Groupdocs.Parser के लिए लाइसेंस कहां से खरीद सकता हूं?
 आप यहां से लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy).
### मैं मूल्यांकन प्रयोजनों के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).