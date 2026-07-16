---
date: '2026-07-16'
description: GroupDocs.Parser के साथ जावा में स्प्रेडशीट थंबनेल बनाना सीखें, ऑफिस
  के बिना एक्सेल का प्रीव्यू करें, और एक्सेल शीट्स को इमेज के रूप में रेंडर करें।
  यह गाइड सेटअप, इम्प्लीमेंटेशन और व्यावहारिक उपयोग मामलों को कवर करता है।
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: GroupDocs.Parser के साथ जावा में स्प्रेडशीट थंबनेल बनाएं—ऑफ़िस के
  बिना एक्सेल का प्रीव्यू करें और एक्सेल शीट्स को इमेज के रूप में रेंडर करें। प्रभावी
  ढंग से PNG प्रीव्यू बनाने के लिए इस चरण‑दर‑चरण गाइड का पालन करें।
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: GroupDocs.Parser का उपयोग करके जावा में स्प्रेडशीट थंबनेल बनाएं
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: GroupDocs.Parser का उपयोग करके जावा में स्प्रेडशीट थंबनेल बनाएं
type: docs
url: /hi/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# GroupDocs.Parser का उपयोग करके जावा में स्प्रेडशीट थंबनेल बनाएं

यदि आप **create spreadsheet thumbnail Java** प्रोग्राम बनाना चाहते हैं, तो आप सही जगह पर आए हैं। इस गाइड में हम GroupDocs.Parser for Java का उपयोग करके `.xlsx` वर्कबुक से उच्च‑गुणवत्ता वाले PNG प्रीव्यू बनाने की प्रक्रिया बताएँगे—तेज़ थंबनेल, स्नैपशॉट साझा करने, या आपके एप्लिकेशन में दस्तावेज़‑प्रीव्यू फीचर बनाने के लिए उपयुक्त। यह समाधान Microsoft Office इंस्टॉलेशन के बिना काम करता है और बड़े वर्कबुक को स्केल करता है जबकि मेमोरी उपयोग कम रखता है।

## त्वरित उत्तर
- **“preview Excel” का क्या अर्थ है?** इमेज फ़ाइलें (जैसे PNG) बनाना जो प्रत्येक वर्कशीट पेज का प्रतिनिधित्व करती हैं।  
- **कौन सा फ़ॉर्मेट अनुशंसित है?** PNG बिना नुकसान के गुणवत्ता देता है और वेब थंबनेल के लिए उपयुक्त है।  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए एक फ्री ट्रायल काम करता है; उत्पादन के लिए एक व्यावसायिक लाइसेंस आवश्यक है।  
- **क्या मैं इमेज रिज़ॉल्यूशन बदल सकता हूँ?** हाँ—`PreviewOptions` में DPI समायोजित करें।  
- **क्या अन्य फ़ॉर्मेट्स का प्रीव्यू संभव है?** GroupDocs.Parser PDF, Word, और कई इमेज प्रकारों को भी सपोर्ट करता है।

## GroupDocs.Parser के साथ “how to preview Excel” क्या है?
अपने Excel वर्कबुक को लोड करें और प्रत्येक शीट को PNG इमेज के रूप में रेंडर करें बिना Microsoft Office की आवश्यकता के। GroupDocs.Parser पेज़ को एक‑एक करके स्ट्रीम करता है, जिससे लॉसलेस थंबनेल बनते हैं जिन्हें डिस्क पर सहेजा जा सकता है या HTTP के माध्यम से लौटाया जा सकता है, जो वेब‑आधारित प्रीव्यू सेवाओं के लिए आदर्श है।

GroupDocs.Parser Excel वर्कबुक पढ़ता है, प्रत्येक शीट को विज़ुअल पेज के रूप में रेंडर करता है, और आपको उन पेजों को इमेज फ़ाइलों में स्ट्रीम करने देता है। इससे Office इंटरऑप या थर्ड‑पार्टी कन्वर्टर्स की आवश्यकता समाप्त हो जाती है।

## Excel प्रीव्यू के लिए GroupDocs.Parser क्यों उपयोग करें?
आपको GroupDocs.Parser का उपयोग करना चाहिए क्योंकि यह किसी भी Java सर्वर पर काम करता है, Office इंस्टॉलेशन की आवश्यकता नहीं होती, बड़े वर्कबुक को कम मेमोरी के साथ संभालता है, और कॉन्फ़िगर करने योग्य DPI के साथ लॉसलेस PNG इमेज बनाता है। SDK **100+ इनपुट और आउटपुट फ़ॉर्मेट** को सपोर्ट करता है, 200‑पेज़ वर्कबुक को 3 सेकंड से कम समय में प्रोसेस कर सकता है, और प्रति शीट मेमोरी उपयोग को 50 MB से नीचे रखता है।

- **Office इंस्टॉलेशन की आवश्यकता नहीं** – किसी भी सर्वर‑साइड Java वातावरण पर चलता है।  
- **बड़े फ़ाइलों को सपोर्ट करता है** – पेज़ को एक‑एक करके स्ट्रीम करता है, जिससे मेमोरी उपयोग कम रहता है।  
- **उच्च‑गुणवत्ता आउटपुट** – DPI, फ़ॉर्मेट, और रेंडरिंग विकल्पों पर नियंत्रण।  
- **क्रॉस‑फ़ॉर्मेट लचीलापन** – वही API PDFs, Word दस्तावेज़, और अधिक के लिए काम करता है।

## पूर्वापेक्षाएँ
- **Java Development Kit** (8 +).  
- **IDE** जैसे IntelliJ IDEA या Eclipse।  
- **GroupDocs.Parser for Java SDK** – डाउनलोड करें [यहाँ](https://releases.groupdocs.com/parser/java/) से।  
- **Documentation** – आधिकारिक [दस्तावेज़](https://docs.groupdocs.com/parser/java/) देखें।  
- **Sample Excel file** (`.xlsx`) जिसे आप प्रीव्यू करना चाहते हैं।  
- **Maven या Gradle** (वैकल्पिक) डिपेंडेंसी मैनेजमेंट के लिए।

## पैकेज इम्पोर्ट करें
ये इम्पोर्ट्स आपको parser, preview options, और stream हैंडलिंग यूटिलिटीज़ तक पहुँच प्रदान करते हैं।

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## स्प्रेडशीट पेज प्रीव्यू जनरेट करने के लिए चरण‑दर‑चरण गाइड

### चरण 1: Parser इंस्टेंस को इनिशियलाइज़ करें
`Parser` GroupDocs.Parser की कोर क्लास है जो स्प्रेडशीट फ़ाइलों तक रीड एक्सेस प्रदान करती है और पेज‑वाइज़ रेंडरिंग को सक्षम करती है।  
एक `Parser` ऑब्जेक्ट बनाएं जो आपके Excel वर्कबुक की ओर इशारा करता हो। *try‑with‑resources* ब्लॉक सुनिश्चित करता है कि parser स्वचालित रूप से बंद हो जाए।

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Pro tip:** `FileNotFoundException` से बचने के लिए एक एब्सोल्यूट पाथ उपयोग करें या रिसोर्स फ़ोल्डर कॉन्फ़िगर करें।

### चरण 2: अपने Preview Options तैयार करें
`PreviewOptions` रेंडरिंग पैरामीटर जैसे आउटपुट फ़ॉर्मेट और DPI को कॉन्फ़िगर करता है।  
`ICreatePageStream` एक कॉलबैक इंटरफ़ेस है जो प्रत्येक जेनरेटेड पेज के लिए आउटपुट स्ट्रीम प्रदान करता है। निर्धारित करें कि प्रत्येक पेज कैसे सेव होगा। `ICreatePageStream` इम्प्लीमेंटेशन प्रत्येक वर्कशीट पेज के लिए एक नया `FileOutputStream` रिटर्न करता है।

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> यह चरण वह है जहाँ आप **convert xlsx to png** करते हैं—स्ट्रीम PNG डेटा को डिस्क पर लिखती है।

### चरण 3: रेंडर जानकारी कैप्चर करने के लिए एक डेलीगेट अटैच करें
यदि आपको प्रत्येक रेंडर की गई शीट के बारे में विवरण चाहिए (जैसे, डाइमेंशन, शीट नाम), तो एक कॉलबैक रजिस्टर करें।

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### चरण 4: आउटपुट फ़ॉर्मेट और DPI निर्दिष्ट करें
इमेज फ़ॉर्मेट के रूप में PNG चुनें और ऐसा DPI सेट करें जो गुणवत्ता और फ़ाइल आकार के बीच संतुलन रखे।

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> यदि आपको छोटे थंबनेल चाहिए (जैसे, 96) या हाई‑रिज़ॉल्यूशन प्रिंट (जैसे, 300) चाहिए तो DPI समायोजित करें।

### चरण 5: प्रीव्यू जनरेट करें
सब कुछ कॉन्फ़िगर होने के बाद, `generatePreview` कॉल करें। SDK प्रत्येक वर्कशीट पर इटरैट करेगा और आपके द्वारा प्रदान किए गए स्ट्रीम को इनवोक करेगा।

```java
parser.generatePreview(previewOptions);
```

### चरण 6: `getOutputPath()` हेल्पर को परिभाषित करें
`getOutputPath()` पेज (शीट) नंबर के आधार पर फ़ाइल नाम बनाता है और आउटपुट इमेज के लिए पूरा पाथ रिटर्न करता है। फ़ोल्डर स्ट्रक्चर को कस्टमाइज़ करने में स्वतंत्र महसूस करें।

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Common pitfall:** यदि आप पहले से `output` डायरेक्टरी नहीं बनाते हैं तो `IOException` होगा। इसे प्रोग्रामेटिकली बनाएं या सुनिश्चित करें कि यह मौजूद है।

## पूर्ण कार्यशील उदाहरण (सरलीकृत)

नीचे एक संक्षिप्त संस्करण है जो सभी भागों को जोड़ता है। यह **create spreadsheet thumbnail Java** वर्कफ़्लो को शुरू से अंत तक दर्शाता है।

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

इस स्निपेट को चलाएँ, और आपको `output` फ़ोल्डर में `preview_page_1.png`, `preview_page_2.png`, … फ़ाइलों की श्रृंखला मिलेगी—प्रत्येक मूल Excel वर्कबुक की एक शीट का प्रतिनिधित्व करती है।

## सामान्य समस्याएँ और समाधान
| समस्या | कारण | समाधान |
|-------|-------|-----|
| **कोई इमेज जेनरेट नहीं हुई** | `getOutputPath` एक अमान्य डायरेक्टरी रिटर्न करता है | सुनिश्चित करें कि टार्गेट फ़ोल्डर मौजूद है या इसे `new File("output").mkdirs();` से बनाएं। |
| **बड़ी फ़ाइलों पर मेमोरी समाप्ति त्रुटि** | पूरे वर्कबुक को एक साथ लोड करना | स्ट्रीमिंग एप्रोच (जैसा दिखाया गया) उपयोग करें और पेज़ को एक‑एक करके प्रोसेस करें। |
| **गलत DPI** | `setDpi` कॉल नहीं किया गया या डिफ़ॉल्ट (96) पर सेट है | `generatePreview` से पहले `previewOptions.setDpi(yourDesiredValue);` कॉल करें। |
| **असमर्थित फ़ॉर्मेट** | एक करप्टेड `.xlsx` का प्रीव्यू करने की कोशिश | फ़ाइल को Excel से वैलिडेट करें या प्रोसेस करने से पहले `Parser.isSupported` का उपयोग करें। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं GroupDocs.Parser का उपयोग करके PDFs और इमेजेज के लिए प्रीव्यू जेनरेट कर सकता हूँ?**  
A: हाँ, वही API PDFs, Word दस्तावेज़, और कई इमेज फ़ॉर्मेट्स के लिए काम करता है।

**प्रश्न: मैं आउटपुट इमेज फ़ॉर्मेट कैसे बदलूँ?**  
A: `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (या `Gif`, `Bmp`, आदि) कॉल करें।

**प्रश्न: बहुत बड़े वर्कबुक के साथ प्रदर्शन की चिंता है?**  
A: SDK पेज़ को स्ट्रीम करता है, जिससे मेमोरी उपयोग कम रहता है। बहुत बड़ी फ़ाइलों के लिए, समानांतर बैच में प्रोसेस करने पर विचार करें।

**प्रश्न: प्रीव्यू जेनरेशन के दौरान त्रुटियों को कैसे हैंडल करूँ?**  
A: कोड को try‑catch ब्लॉक्स में रैप करें (जैसा दिखाया गया) और एक्सेप्शन विवरण लॉग करें। यदि आप try‑with‑resources नहीं उपयोग कर रहे हैं तो `finally` ब्लॉक में स्ट्रीम्स को बंद करना सुनिश्चित करें।

**प्रश्न: क्या लाइब्रेरी को Microsoft Office इंस्टॉल करने की आवश्यकता है?**  
A: नहीं। GroupDocs.Parser एक शुद्ध Java समाधान है और किसी भी प्लेटफ़ॉर्म पर काम करता है जो Java 8+ सपोर्ट करता है।

**अंतिम अपडेट:** 2026-07-16  
**परीक्षित संस्करण:** GroupDocs.Parser 23.11 (लेखन के समय नवीनतम)  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल्स

- [कैसे जेनरेट करें प्रीव्यू – GroupDocs.Parser Java के लिए दस्तावेज़ पेज प्रीव्यू जेनरेशन ट्यूटोरियल्स](/parser/java/page-preview-generation/)
- [GroupDocs.Parser के साथ Excel Java पार्स करें: पूर्ण गाइड](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [GroupDocs.Parser for Java का उपयोग करके Excel शीट्स से रॉ टेक्स्ट निकालना: चरण‑दर‑चरण गाइड](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)