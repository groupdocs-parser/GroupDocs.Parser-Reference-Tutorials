---
title: कीवर्ड द्वारा वर्ड दस्तावेज़ में टेक्स्ट खोजें
linktitle: कीवर्ड द्वारा वर्ड दस्तावेज़ में टेक्स्ट खोजें
second_title: GroupDocs.Parser .NET एपीआई
description: .NET के लिए GroupDocs.Parser का उपयोग करके Word दस्तावेज़ों में टेक्स्ट खोजना सीखें। विशिष्ट कीवर्ड को कुशलतापूर्वक निकालें।
weight: 18
url: /hi/net/word-document-processing/search-text-in-word-document-by-keyword/
---

# कीवर्ड द्वारा वर्ड दस्तावेज़ में टेक्स्ट खोजें

## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि C# का उपयोग करके Word दस्तावेज़ में विशिष्ट टेक्स्ट खोजने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। GroupDocs.Parser एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को Word दस्तावेज़ों सहित विभिन्न दस्तावेज़ स्वरूपों से टेक्स्ट और मेटाडेटा निकालने की अनुमति देती है।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. विकास वातावरण: विज़ुअल स्टूडियो या अन्य संगत IDE स्थापित करें।
2.  GroupDocs.Parser लाइब्रेरी: .NET लाइब्रेरी के लिए GroupDocs.Parser डाउनलोड करें और इंस्टॉल करें[वेबसाइट](https://releases.groupdocs.com/parser/net/).
3. नमूना वर्ड दस्तावेज़: पाठ खोजने के लिए उपयोग करने हेतु एक नमूना वर्ड दस्तावेज़ तैयार करें।

## नामस्थान आयात करें
अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को आयात करके आरंभ करें:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## चरण 1: पार्सर क्लास का एक इंस्टेंस बनाएं
 सबसे पहले, इसका एक उदाहरण बनाएं`Parser` अपने नमूना वर्ड दस्तावेज़ के पथ को पास करके क्लास का चयन करें।
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // कोड यहाँ है
}
```
## चरण 2: कीवर्ड खोजें
 इसके बाद, का उपयोग करें`Search` की विधि`Parser` दस्तावेज़ के भीतर एक विशिष्ट कीवर्ड खोजने के लिए क्लास का उपयोग करें।
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 प्रतिस्थापित करें`"keyword"` उस पाठ के साथ जिसे आप दस्तावेज़ के भीतर खोजना चाहते हैं.
## चरण 3: खोज परिणामों पर पुनरावृति करें
 खोज परिणामों पर पुनरावृत्ति करने के लिए एक का उपयोग करें`foreach` प्रत्येक तक पहुँचने के लिए लूप`SearchResult` वस्तु।
```csharp
foreach (SearchResult result in searchResults)
{
    //प्रत्येक खोज परिणाम को संभालने के लिए कोड
}
```
## चरण 4: खोज परिणाम विवरण तक पहुंचें
 लूप के भीतर, आप प्रत्येक खोज परिणाम की स्थिति और पाठ तक पहुंच सकते हैं`Position` और`Text` के गुण`SearchResult` वस्तु।
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
यह कोड स्निपेट इंडेक्स प्रिंट करता है (`Position`) और पाया गया पाठ (`Text`) को कंसोल पर प्रत्येक खोज परिणाम के लिए भेजें।

## निष्कर्ष
इस ट्यूटोरियल में, आपने सीखा है कि Word दस्तावेज़ में विशिष्ट टेक्स्ट खोजने के लिए .NET के लिए GroupDocs.Parser का उपयोग कैसे करें। यह लाइब्रेरी प्रोग्रामेटिक रूप से विभिन्न दस्तावेज़ प्रारूपों से सामग्री निकालने और उसमें हेरफेर करने का एक सुविधाजनक तरीका प्रदान करती है।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Parser Word के अलावा अन्य दस्तावेज़ स्वरूपों को भी संभाल सकता है?
हां, GroupDocs.Parser पीडीएफ, एक्सेल, पावरपॉइंट और अन्य सहित कई प्रकार के प्रारूपों का समर्थन करता है।
### क्या GroupDocs.Parser .NET कोर के साथ संगत है?
हां, GroupDocs.Parser .NET फ्रेमवर्क और .NET कोर दोनों के साथ संगत है।
### मैं GroupDocs.Parser के लिए अस्थायी लाइसेंस कैसे प्राप्त करूं?
 आप अस्थायी लाइसेंस का अनुरोध कर सकते हैं[ग्रुपडॉक्स खरीद पृष्ठ](https://purchase.groupdocs.com/temporary-license/).
### मैं अतिरिक्त सहायता कहां पा सकता हूं या GroupDocs.Parser के बारे में प्रश्न पूछ सकता हूं?
 दौरा करना[GroupDocs.Parser मंच](https://forum.groupdocs.com/c/parser/17) सामुदायिक समर्थन और चर्चा के लिए।
### क्या मैं खरीदने से पहले GroupDocs.Parser को मुफ्त में आज़मा सकता हूँ?
 हां, आप यहां से निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं।[ग्रुपडॉक्स ने पेज जारी किया](https://releases.groupdocs.com/).