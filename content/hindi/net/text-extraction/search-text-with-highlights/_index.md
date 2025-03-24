---
title: हाइलाइट्स के साथ टेक्स्ट खोजें
linktitle: हाइलाइट्स के साथ टेक्स्ट खोजें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके दस्तावेज़ों में टेक्स्ट खोजना और हाइलाइट करना सीखें। कुशलतापूर्वक बहुमूल्य जानकारी निकालें।
weight: 24
url: /hi/net/text-extraction/search-text-with-highlights/
---
## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि किसी दस्तावेज़ में टेक्स्ट खोजने और खोज परिणामों को हाइलाइट करने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो आपको विभिन्न दस्तावेज़ प्रारूपों के साथ काम करने और टेक्स्ट, मेटाडेटा और बहुत कुछ निकालने की अनुमति देती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Parser: लाइब्रेरी डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/parser/net/).
2. IDE: .NET विकास के लिए विजुअल स्टूडियो या किसी भी पसंदीदा IDE का उपयोग करें।
3. नमूना फ़ाइल: पाठ खोज के लिए एक नमूना दस्तावेज़ (जैसे, PDF, DOCX) तैयार करें।

## नामस्थान आयात करें
सबसे पहले, अपने .NET प्रोजेक्ट में आवश्यक नेमस्पेस आयात करके शुरुआत करें:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## चरण 1: पार्सर इंस्टेंस बनाएँ
 प्रारंभ में इसे उदाहरण के रूप में प्रस्तुत करें`Parser` अपनी नमूना फ़ाइल के पथ के साथ क्लास:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // आपका कोड यहाँ
}
```
## चरण 2: हाइलाइट विकल्प परिभाषित करें
 विवरण दें`HighlightOptions` खोज परिणामों को कैसे हाइलाइट किया जाना चाहिए, इसे कॉन्फ़िगर करने के लिए। उदाहरण के लिए, 15 वर्णों की संदर्भ विंडो सेट करना:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## चरण 3: टेक्स्ट खोजें
अब, दस्तावेज़ के भीतर टेक्स्ट सर्च करें। वह कीवर्ड प्रदान करें जिसे आप खोजना चाहते हैं (उदाहरण के लिए, "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## चरण 4: खोज परिणामों को संसाधित करें
खोज परिणामों को पुनरावृत्त करें और पाए गए पाठ को हाइलाइट के साथ प्रदर्शित करें:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## निष्कर्ष
इस ट्यूटोरियल में, आपने सीखा कि दस्तावेज़ों के भीतर टेक्स्ट खोजने और खोज परिणामों को हाइलाइट करने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। यह कार्यक्षमता आपके .NET अनुप्रयोगों में टेक्स्ट निष्कर्षण और विश्लेषण के लिए बेहद उपयोगी हो सकती है।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser विभिन्न दस्तावेज़ प्रारूपों को संसाधित करने के लिए उपयुक्त है?
हां, GroupDocs.Parser पीडीएफ, DOCX, XLSX, PPTX, और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं दस्तावेज़ों से मेटाडेटा निकालने के लिए GroupDocs.Parser का उपयोग कर सकता हूँ?
बिल्कुल! GroupDocs.Parser आपको दस्तावेज़ों से मेटाडेटा, टेक्स्ट और संरचित डेटा निकालने की अनुमति देता है।
### मैं सहायता कहां पा सकता हूं या GroupDocs.Parser के बारे में प्रश्न पूछ सकता हूं?
 आप यहां जा सकते हैं[GroupDocs.Parser मंच](https://forum.groupdocs.com/c/parser/17) किसी भी सहायता-संबंधी प्रश्नों के लिए.
### क्या GroupDocs.Parser के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हां, आप इसका उपयोग कर सकते हैं[मुफ्त परीक्षण](https://releases.groupdocs.com/) GroupDocs.Parser की विशेषताओं का मूल्यांकन करने के लिए।
### मैं GroupDocs.Parser के लिए लाइसेंस कैसे खरीद सकता हूं?
 आप यहां से लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy) और अस्थायी लाइसेंस भी प्राप्त करें[यहाँ](https://purchase.groupdocs.com/temporary-license/).