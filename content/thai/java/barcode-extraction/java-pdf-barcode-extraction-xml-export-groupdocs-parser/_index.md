---
date: '2026-10-12'
description: เรียนรู้วิธีแยก QR จาก PDF ใน Java ด้วย GroupDocs.Parser และส่งออกข้อมูล
  barcode เป็น XML เพื่อการประมวลผลต่อไป
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: เรียนรู้วิธีแยก QR จาก PDF ใน Java ด้วย GroupDocs.Parser และส่งออกข้อมูล
  barcode เป็น XML เพื่อการประมวลผลต่อไป
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: วิธีแยก QR จาก PDF ใน Java ด้วย GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: วิธีแยก QR จาก PDF ใน Java ด้วย GroupDocs.Parser
type: docs
url: /th/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# วิธีการดึง QR จาก PDF ด้วย Java และ GroupDocs.Parser

ในกระบวนการทำงานของธุรกิจสมัยใหม่, **การดึง QR จาก PDF** สามารถเปลี่ยนคอขวดการป้อนข้อมูลด้วยมือให้เป็นสายงานอัตโนมัติเต็มรูปแบบ ไม่ว่าคุณจะจัดการกับรายการจัดส่ง, ใบเสร็จรับเงินของร้านค้า, หรือแคตาล็อกสินค้า การดึงข้อมูล QR อย่างรวดเร็วและเชื่อถือได้เป็นสิ่งสำคัญสำหรับระบบ downstream. คู่มือนี้จะพาคุณผ่านการใช้ **GroupDocs.Parser for Java** เพื่ออ่าน QR code (และบาร์โค้ดอื่น) จาก PDF และส่งออกผลลัพธ์เป็นไฟล์ XML ที่สะอาดซึ่ง ERP, ระบบสินค้าคงคลัง, หรือแพลตฟอร์มวิเคราะห์ของคุณสามารถนำไปใช้ได้.

## คำตอบสั้น
- **GroupDocs.Parser for Java ทำอะไร?** มันอ่านไฟล์ PDF และดึงข้อมูลโครงสร้างเช่นบาร์โค้ด, ตาราง, และข้อความ.  
- **วิธีดึง QR code?** Configure `BarcodeOptions` with the QR type and call `parser.getBarcodes()`.  
- **ฉันสามารถอ่าน QR code ใน Java ได้ไหม?** Yes—set the barcode type to `"QR"` in the options.  
- **ฉันต้องการไลเซนส์หรือไม่?** A trial works for testing; a commercial license is required for production.  
- **ต้องการเวอร์ชัน Java ใด?** Java 8 หรือสูงกว่าแนะนำ.  

## “การดึง QR จาก PDF” คืออะไรในบริบทของการประมวลผล PDF?
การดึง QR จาก PDF หมายถึงการสแกนแต่ละหน้าสำหรับกราฟิกที่เข้ารหัสเป็น QR, ถอดรหัสข้อมูลที่ฝังอยู่, และส่งคืนในรูปแบบที่โปรแกรมสามารถใช้งานได้ GroupDocs.Parser ทำหน้าที่นามธรรมการวิเคราะห์ภาพระดับล่างเพื่อให้คุณโฟกัสที่ตรรกะธุรกิจแทนการจัดการพิกเซล.

## ทำไมต้องใช้ GroupDocs.Parser สำหรับการดึง QR?
GroupDocs.Parser รองรับ **over 30 input formats** และสามารถประมวลผล PDF ขนาด **500 MB** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ, ให้ผลลัพธ์ที่แม่นยำสูงแม้กับการสแกนความละเอียดต่ำ คุณสามารถเลือก `QualityMode.Low` เพื่อความเร็วหรือ `QualityMode.High` เพื่อความแม่นยำสูงสุด, และ API เดียวกันทำงานกับ PDF, รูปภาพ, และเอกสาร Office, ลดความจำเป็นในการใช้หลายไลบรารี.

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Parser for Java** (เวอร์ชัน 25.5 หรือใหม่กว่า).  
- Maven หรือดาวน์โหลด JAR ด้วยตนเอง.  
- สภาพแวดล้อมการพัฒนา Java 8+ (IntelliJ IDEA, Eclipse, หรือ editor ใดก็ได้).  

## การตั้งค่า GroupDocs.Parser สำหรับ Java
### ใช้ Maven
Add the GroupDocs repository and dependency to your `pom.xml`:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

### ดาวน์โหลดโดยตรง
Alternatively, download the latest JAR from [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### ขั้นตอนการขอรับไลเซนส์
- **ทดลองใช้ฟรี:** ทดลอง 30‑วันพร้อมฟีเจอร์เต็ม.  
- **ไลเซนส์ชั่วคราว:** ขอคีย์ชั่วคราวสำหรับการประเมินระยะยาว.  
- **ซื้อ:** รับไลเซนส์เชิงพาณิชย์สำหรับการใช้งานในผลิตภัณฑ์.  

### การเริ่มต้นและตั้งค่าเบื้องต้น
Create a `Parser` instance that points to the PDF you want to analyze:

`Parser` is the core class in GroupDocs.Parser that represents a document and provides methods for extracting content such as text, tables, and barcodes.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## วิธีอ่าน QR code ใน PDF ด้วย Java โดยใช้ GroupDocs.Parser
Reading QR codes in Java PDFs with GroupDocs.Parser involves creating a parser instance, configuring barcode options to target QR types, invoking the barcode extraction method, and then handling the returned barcode objects. The process is straightforward, works on any PDF page, and returns the decoded values along with positional metadata for further processing.

### ขั้นตอนที่ 1: ตรวจสอบการสนับสนุนบาร์โค้ด
Before attempting extraction, confirm that the document format supports barcode scanning:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*คำอธิบาย:* การป้องกันนี้ช่วยหลีกเลี่ยงข้อผิดพลาดรันไทม์บนไฟล์ที่ไม่รองรับ.

### ขั้นตอนที่ 2: ตั้งค่า barcode options (อ่าน QR code ด้วย Java)
`BarcodeOptions` is a configuration object that lets you specify which barcode symbologies to detect, set the scanning quality mode, and fine‑tune parameters such as detection thresholds, ensuring optimal performance for the target QR codes.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*คำอธิบาย:* `QualityMode.Low` speeds up processing; switch to `High` if you need extra accuracy. The `"QR"` argument tells the engine to look for QR‑type barcodes only.

### ขั้นตอนที่ 3: ดึงข้อมูล QR
`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions` and returns a collection of `PageBarcodeArea` objects, each encapsulating the decoded QR value, the page number, and the exact coordinates of the barcode within the page, allowing precise downstream handling.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*คำอธิบาย:* `parser.getBarcodes` returns an iterable collection of `PageBarcodeArea` objects, each containing the decoded QR value and its location on the page.

## การส่งออกข้อมูลที่ดึงมาเป็น XML
### ขั้นตอนที่ 4: เริ่มต้น XmlExporter
`XmlExporter` is a utility class that transforms a collection of barcode objects into a well‑structured XML document, automatically generating elements for each barcode with attributes for page index, position, and decoded value, which can then be saved or streamed to other systems.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*คำอธิบาย:* The `XmlExporter` handles serialization of barcode objects into standard XML, ready for integration with ERP or inventory systems.

### ขั้นตอนที่ 5: เขียนไฟล์ XML
Save the extracted QR information to disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*คำอธิบาย:* The resulting `data.xml` contains one `<Barcode>` element per QR code, with attributes for page number, coordinates, and decoded value.

## การประยุกต์ใช้งานจริง
1. **การจัดการสินค้าคงคลัง:** เติมฐานข้อมูลสต็อกอัตโนมัติโดยอ่าน QR tag บน PDF การจัดส่งที่เข้ามา.  
2. **การมองเห็นห่วงโซ่อุปทาน:** ติดตามพัสดุแบบเรียลไทม์โดยดึง QR identifier ที่ฝังอยู่ในเอกสารโลจิสติกส์.  
3. **ใบเสร็จรับเงินของร้านค้า:** ดึงข้อมูลโปรโมชั่นหรือการรับประกันจาก QR code ที่พิมพ์บนใบเสร็จดิจิทัล.  

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **การจัดการหน่วยความจำ:** สำหรับ PDF ขนาดใหญ่มาก ให้ประมวลผลหน้าแบบสตรีมมิ่งแทนการโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ.  
- **การเลือก QualityMode:** ใช้ `Low` สำหรับการประมวลผลเป็นจำนวนมาก; เปลี่ยนเป็น `High` เมื่อทำงานกับสแกนความละเอียดต่ำ.  
- **การอัปเดตไลบรารี:** รักษา GroupDocs.Parser ให้เป็นเวอร์ชันล่าสุดเพื่อรับประโยชน์จากการปรับปรุงประสิทธิภาพและการแก้บั๊กล่าสุด.  

## ปัญหาทั่วไปและการแก้ไข
| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| ไม่พบบาร์โค้ด | ระบุประเภทบาร์โค้ดผิด | เปลี่ยน `"QR"` เป็นประเภทที่เหมาะสม (เช่น `"CODE_128"`). |
| เกิดข้อผิดพลาด Out‑of‑memory บน PDF ขนาดใหญ่ | โหลดเอกสารทั้งหมดพร้อมกัน | ประมวลผลหน้าแยกกันหรือเพิ่มขนาด heap ของ JVM (`-Xmx2g`). |
| ไฟล์ XML ว่างเปล่า | เรียก `exportBarcodes` ก่อนการดึงข้อมูล | ตรวจสอบว่า `parser.getBarcodes(options)` คืนค่าข้อมูลก่อนการส่งออก. |

## คำถามที่พบบ่อย
**Q: ฉันสามารถดึงบาร์โค้ดจากไฟล์รูปภาพโดยใช้ GroupDocs.Parser ได้ไหม?**  
A: ใช่, ไลบรารีรองรับการดึงบาร์โค้ดจากรูปภาพทั่วไป (PNG, JPEG, TIFF).

**Q: ฟอร์แมตบาร์โค้ดใดบ้างที่รองรับ?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417, และอื่น ๆ อีกมากมาย. ดูเอกสาร API เพื่อรายการเต็ม.

**Q: ฉันควรจัดการกับ PDF ที่มีรหัสผ่านอย่างไร?**  
A: ส่งรหัสผ่านไปยังคอนสตรัคเตอร์ `Parser`: `new Parser(filePath, "password")`.

**Q: เวอร์ชันทดลองเพียงพอสำหรับการทดสอบในสภาพการผลิตหรือไม่?**  
A: เวอร์ชันทดลองให้ฟังก์ชันเต็มแต่จะใส่ลายน้ำบนข้อมูลที่ดึงออกมา. สำหรับการผลิตควรซื้อไลเซนส์เชิงพาณิชย์.

**Q: ถ้า PDF ของฉันมีทั้ง QR และบาร์โค้ดเชิงเส้นควรทำอย่างไร?**  
A: สร้างหลายอินสแตนซ์ของ `BarcodeOptions` หรือส่งอาร์เรย์ของประเภทเพื่อสแกนทุกฟอร์แมตที่ต้องการในครั้งเดียว.

---

**อัปเดตล่าสุด:** 2026-10-12  
**ทดสอบด้วย:** GroupDocs.Parser 25.5  
**ผู้เขียน:** GroupDocs  

## แหล่งข้อมูล
- [เอกสาร GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [อ้างอิง API](https://reference.groupdocs.com/parser/java)
- [ดาวน์โหลด GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [ที่เก็บ GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/parser)
- [สมัครไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)

## บทแนะนำที่เกี่ยวข้อง

- [ดึงบาร์โค้ดจาก PDF ด้วย GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [วิธีโหลด PDF จาก URL ด้วย GroupDocs.Parser for Java](/parser/java/document-loading/)
- [ดึงข้อมูลฟอร์ม PDF ด้วย GroupDocs.Parser ใน Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)