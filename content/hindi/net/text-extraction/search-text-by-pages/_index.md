---
title: पेज के अनुसार टेक्स्ट खोजें
linktitle: पेज के अनुसार टेक्स्ट खोजें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके पृष्ठों द्वारा पाठ खोजना सीखें। अपने .NET अनुप्रयोगों में दस्तावेज़ों से विशिष्ट सामग्री को कुशलतापूर्वक निकालें।
weight: 22
url: /hi/net/text-extraction/search-text-by-pages/
type: docs
---
# पेज के अनुसार टेक्स्ट खोजें

## परिचय
.NET विकास की दुनिया में, दस्तावेज़ों से कुशलतापूर्वक पार्स करना और टेक्स्ट निकालना एक महत्वपूर्ण कार्य है। .NET के लिए GroupDocs.Parser विभिन्न दस्तावेज़ प्रारूपों के साथ काम करने के लिए शक्तिशाली क्षमताएँ प्रदान करता है, जिससे डेवलपर्स को विशिष्ट सामग्री को सहजता से खोजने और निकालने की अनुमति मिलती है। यह ट्यूटोरियल आपके .NET अनुप्रयोगों में पृष्ठों द्वारा टेक्स्ट खोजने के लिए GroupDocs.Parser का लाभ उठाने की प्रक्रिया के माध्यम से आपका मार्गदर्शन करेगा।
## आवश्यक शर्तें
इस ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- C# और .NET फ्रेमवर्क की बुनियादी समझ
- आपके सिस्टम पर Visual Studio स्थापित है
-  .NET लाइब्रेरी स्थापित करने के लिए GroupDocs.Parser (डाउनलोड करें[यहाँ](https://releases.groupdocs.com/parser/net/))
- खोज कार्यक्षमता के परीक्षण के लिए नमूना फ़ाइल(फ़ाइलें)
## नामस्थान आयात करें
सबसे पहले, GroupDocs.Parser कार्यक्षमताओं तक पहुँचने के लिए अपने प्रोजेक्ट में आवश्यक नामस्थान शामिल करें:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 प्रारंभ में इसे उदाहरण के रूप में प्रस्तुत करें`Parser` अपनी नमूना फ़ाइल के पथ के साथ क्लास:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // आपका कोड यहां जाएगा
}
```
## चरण 2: पृष्ठ संख्या के साथ पाठ खोजें
 उपयोग करें`Search` दस्तावेज़ में पृष्ठ संख्या के साथ विशिष्ट कीवर्ड खोजने की विधि:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## चरण 3: खोज सहायता की जाँच करें
सत्यापित करें कि क्या खोज ऑपरेशन दस्तावेज़ प्रकार के लिए समर्थित है:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## चरण 4: खोज परिणामों पर पुनरावृति करें
अनुक्रमित स्थिति, पृष्ठ संख्या और पाया गया पाठ पुनः प्राप्त करने के लिए खोज परिणामों के माध्यम से पुनरावृति करें:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Parser का उपयोग करके पृष्ठों द्वारा पाठ खोज को लागू करने का तरीका खोजा है। इन चरणों का पालन करके, आप अपने .NET अनुप्रयोगों में दस्तावेज़ पार्सिंग और खोज कार्यक्षमताओं को कुशलतापूर्वक एकीकृत कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser विभिन्न दस्तावेज़ प्रारूपों के साथ संगत है?
हां, GroupDocs.Parser DOCX, PDF, XLSX, PPTX, और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं GroupDocs.Parser का उपयोग करके दस्तावेज़ों से छवियाँ और मेटाडेटा निकाल सकता हूँ?
बिल्कुल, GroupDocs.Parser दस्तावेजों से छवियों, मेटाडेटा और पाठ को निकालने की अनुमति देता है।
### मैं GroupDocs.Parser के लिए विस्तृत दस्तावेज़ कहां पा सकता हूं?
 आप दस्तावेज़ तक पहुँच सकते हैं[यहाँ](https://tutorials.groupdocs.com/parser/net/).
### मैं GroupDocs.Parser के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप अस्थायी लाइसेंस का अनुरोध कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### मुझे GroupDocs.Parser के साथ समर्थन या सहायता कहां मिल सकती है?
 सहायता और चर्चा के लिए, GroupDocs.Parser फ़ोरम पर जाएँ[यहाँ](https://forum.groupdocs.com/c/parser/17).