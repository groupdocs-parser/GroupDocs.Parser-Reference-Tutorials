---
date: '2026-02-19'
description: เรียนรู้วิธีอ่าน QR code ในไฟล์ PDF ของ Java ด้วย GroupDocs.Parser และส่งออกข้อมูลบาร์โค้ดเป็น
  XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: วิธีอ่าน QR Code ในไฟล์ PDF ของ Java ด้วย GroupDocs.Parser
type: docs
url: /th/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# วิธีอ่าน QR Code ใน PDF ของ Java ด้วย GroupDocs.Parser

ในกระบวนการทำงานของธุรกิจสมัยใหม่, **วิธีอ่าน QR** code จากเอกสาร PDF สามารถสร้างความแตกต่างระหว่างคอขวดการป้อนข้อมูลด้วยมือและสายงานอัตโนมัติเต็มรูปแบบ ไม่ว่าคุณจะจัดการกับรายการจัดส่ง, ใบเสร็จรับเงินของร้านค้า, หรือแคตาล็อกสินค้า การสกัดข้อมูล QR อย่างรวดเร็วและเชื่อถือได้เป็นสิ่งสำคัญ คู่มือนี้จะพาคุณผ่านการใช้ **GroupDocs.Parser for Java** เพื่ออ่าน QR code (และบาร์โค้ดอื่น) จาก PDF และส่งออกผลลัพธ์เป็นไฟล์ XML ที่สะอาดซึ่งระบบต่อไปสามารถนำไปใช้ได้.

## คำตอบสั้น
- **GroupDocs.Parser for Java ทำอะไร?** มันอ่านไฟล์ PDF และสกัดข้อมูลโครงสร้างเช่นบาร์โค้ด.  
- **วิธีสกัด QR code?** โดยกำหนดค่า `BarcodeOptions` ให้เป็นประเภท QR และเรียก `parser.getBarcodes()`.  
- **ฉันสามารถอ่าน QR code ด้วย Java ได้หรือไม่?** ใช่—ตั้งค่าชนิดบาร์โค้ดเป็น `"QR"` ในตัวเลือก.  
- **ต้องการไลเซนส์หรือไม่?** เวอร์ชันทดลองทำงานสำหรับการทดสอบ; ต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานจริง.  
- **ต้องการเวอร์ชัน Java ใด?** แนะนำให้ใช้ Java 8 หรือสูงกว่า.

## “วิธีอ่าน QR” คืออะไรในบริบทของการประมวลผล PDF?
การอ่าน QR code จาก PDF หมายถึงการสแกนแต่ละหน้าเพื่อค้นหากราฟิกที่เข้ารหัสเป็น QR, ถอดรหัสข้อมูลที่ฝังอยู่, และส่งคืนในรูปแบบที่โปรแกรมสามารถใช้งานได้ GroupDocs.Parser ทำหน้าที่แยกการวิเคราะห์ภาพระดับต่ำออก เพื่อให้คุณมุ่งเน้นที่ตรรกะธุรกิจแทนการจัดการพิกเซล.

## ทำไมต้องใช้ GroupDocs.Parser สำหรับการสกัด QR?
- **ความแม่นยำสูง:** อัลกอริธึมการประมวลผลภาพในตัวจัดการสแกนที่ความละเอียดต่ำ.  
- **ตัวเลือกประสิทธิภาพ:** เลือก `QualityMode.Low` เพื่อความเร็วหรือ `QualityMode.High` เพื่อความแม่นยำสูงสุด.  
- **รองรับหลายรูปแบบ:** ทำงานกับ PDF, ภาพ, และแม้กระทั่งเอกสาร Office, ทำให้คุณสามารถใช้โค้ดฐานเดียวกันสำหรับไฟล์ประเภทต่างๆ.

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Parser for Java** (เวอร์ชัน 25.5 หรือใหม่กว่า).  
- Maven หรือดาวน์โหลด JAR ด้วยตนเอง.  
- สภาพแวดล้อมการพัฒนา Java 8+ (IntelliJ IDEA, Eclipse, หรือเครื่องมือแก้ไขใดก็ได้).

## การตั้งค่า GroupDocs.Parser สำหรับ Java
### ใช้ Maven
เพิ่ม repository ของ GroupDocs และ dependency ลงใน `pom.xml` ของคุณ:

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
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### ขั้นตอนการรับไลเซนส์
- **ทดลองใช้ฟรี:** ทดลองใช้ 30 วันพร้อมฟีเจอร์ทั้งหมด.  
- **ไลเซนส์ชั่วคราว:** ขอคีย์ชั่วคราวสำหรับการประเมินระยะยาว.  
- **ซื้อ:** รับไลเซนส์เชิงพาณิชย์สำหรับการใช้งานในสภาพแวดล้อมจริง.

### การเริ่มต้นและตั้งค่าเบื้องต้น
สร้างอินสแตนซ์ `Parser` ที่ชี้ไปยัง PDF ที่คุณต้องการวิเคราะห์:

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

## วิธีอ่าน QR code ใน PDF ของ Java ด้วย GroupDocs.Parser
### ขั้นตอนที่ 1: ตรวจสอบการสนับสนุนบาร์โค้ด
ก่อนทำการสกัดข้อมูล, ยืนยันว่าแบบฟอร์มเอกสารสนับสนุนการสแกนบาร์โค้ด:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*คำอธิบาย:* การตรวจสอบนี้ป้องกันข้อผิดพลาดเวลารันบนไฟล์ประเภทที่ไม่รองรับ.

### ขั้นตอนที่ 2: ตั้งค่าตัวเลือกบาร์โค้ด (อ่าน QR code ด้วย Java)
กำหนดคุณภาพการสแกนและระบุว่าคุณต้องการ QR code:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*คำอธิบาย:* `QualityMode.Low` เร่งการประมวลผล; เปลี่ยนเป็น `High` หากต้องการความแม่นยำเพิ่มขึ้น. อาร์กิวเมนต์ `"QR"` บอกเอนจินให้มองหาเฉพาะบาร์โค้ดประเภท QR.

### ขั้นตอนที่ 3: สกัดข้อมูล QR
ดึงข้อมูลบาร์โค้ดจากทุกหน้าของ PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*คำอธิบาย:* `parser.getBarcodes` คืนคอลเลกชันที่สามารถวนได้ของอ็อบเจ็กต์ `PageBarcodeArea`, แต่ละอ็อบเจ็กต์มีค่าที่ถอดรหัสของ QR และตำแหน่งบนหน้า.

## การส่งออกข้อมูลที่สกัดเป็น XML
### ขั้นตอนที่ 4: เริ่มต้น XML Exporter
สร้าง exporter ที่จะแปลงคอลเลกชันบาร์โค้ดเป็นไฟล์ XML ที่มีโครงสร้างดี:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*คำอธิบาย:* `XmlExporter` จัดการการแปลงอ็อบเจ็กต์บาร์โค้ดเป็น XML มาตรฐาน, พร้อมสำหรับการรวมกับระบบ ERP หรือระบบสินค้าคงคลัง.

### ขั้นตอนที่ 5: เขียนไฟล์ XML
บันทึกข้อมูล QR ที่สกัดลงดิสก์:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*คำอธิบาย:* `data.xml` ที่ได้จะมีองค์ประกอบ `<Barcode>` หนึ่งรายการต่อ QR code, พร้อมแอตทริบิวต์สำหรับหมายเลขหน้า, พิกัด, และค่าที่ถอดรหัส.

## การประยุกต์ใช้งานจริง
1. **การจัดการสินค้าคงคลัง:** เติมฐานข้อมูลสต็อกอัตโนมัติโดยอ่าน QR tag บน PDF การจัดส่งที่เข้ามา.  
2. **การมองเห็นซัพพลายเชน:** ติดตามพัสดุแบบเรียลไทม์โดยสกัดตัวระบุ QR ที่ฝังอยู่ในเอกสารโลจิสติกส์.  
3. **ใบเสร็จรับเงินของร้านค้า:** ดึงข้อมูลโปรโมชั่นหรือการรับประกันจาก QR code ที่พิมพ์บนใบเสร็จดิจิทัล.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **การจัดการหน่วยความจำ:** สำหรับ PDF ขนาดใหญ่มาก, ประมวลผลหน้าแบบสตรีมแทนการโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ.  
- **การเลือก QualityMode:** ใช้ `Low` สำหรับการประมวลผลจำนวนมาก; เปลี่ยนเป็น `High` เมื่อทำงานกับสแกนความละเอียดต่ำ.  
- **อัปเดตไลบรารี:** รักษา GroupDocs.Parser ให้เป็นเวอร์ชันล่าสุดเพื่อรับประโยชน์จากการปรับปรุงประสิทธิภาพและการแก้ไขบั๊กล่าสุด.

## ปัญหาทั่วไปและการแก้ไขข้อผิดพลาด
| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ไข |
|---------|--------------|-----|
| ไม่มีบาร์โค้ดที่คืนค่า | ระบุประเภทบาร์โค้ดผิด | เปลี่ยน `"QR"` เป็นประเภทที่เหมาะสม (เช่น `"CODE_128"`). |
| ข้อผิดพลาดหน่วยความจำเต็มบน PDF ขนาดใหญ่ | โหลดเอกสารทั้งหมดพร้อมกัน | ประมวลผลหน้าแยกกันหรือเพิ่มขนาด heap ของ JVM (`-Xmx2g`). |
| ไฟล์ XML ว่าง | `exportBarcodes` ถูกเรียกก่อนการสกัด | ตรวจสอบให้ `parser.getBarcodes(options)` คืนข้อมูลก่อนการส่งออก. |

## คำถามที่พบบ่อย
**ถาม: ฉันสามารถสกัดบาร์โค้ดจากไฟล์รูปภาพโดยใช้ GroupDocs.Parser ได้หรือไม่?**  
**ตอบ:** ใช่, ไลบรารีรองรับการสกัดบาร์โค้ดจากรูปแบบภาพทั่วไป (PNG, JPEG, TIFF).

**ถาม: ฟอร์แมตบาร์โค้ดใดบ้างที่รองรับ?**  
**ตอบ:** QR, Code 39, Code 128, DataMatrix, PDF417, และอื่น ๆ อีกมากมาย ดูเอกสาร API สำหรับรายการเต็ม.

**ถาม: ควรจัดการกับ PDF ที่มีการป้องกันด้วยรหัสผ่านอย่างไร?**  
**ตอบ:** ส่งรหัสผ่านไปยังคอนสตรัคเตอร์ `Parser`: `new Parser(filePath, "password")`.

**ถาม: เวอร์ชันทดลองเพียงพอสำหรับการทดสอบในสภาพแวดล้อมการผลิตหรือไม่?**  
**ตอบ:** เวอร์ชันทดลองให้ฟังก์ชันเต็มแต่จะใส่ลายน้ำบนข้อมูลที่สกัด. สำหรับการผลิตควรซื้อไลเซนส์เชิงพาณิชย์.

**ถาม: ถ้า PDF ของฉันมีทั้ง QR และบาร์โค้ดเชิงเส้นจะทำอย่างไร?**  
**ตอบ:** สร้างหลายอินสแตนซ์ของ `BarcodeOptions` หรือส่งอาร์เรย์ของประเภทเพื่อสแกนทุกฟอร์แมตที่ต้องการในครั้งเดียว.

---

**อัปเดตล่าสุด:** 2026-02-19  
**ทดสอบด้วย:** GroupDocs.Parser 25.5  
**ผู้เขียน:** GroupDocs  

## แหล่งข้อมูล
- [เอกสาร GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [อ้างอิง API](https://reference.groupdocs.com/parser/java)
- [ดาวน์โหลด GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [ที่เก็บ GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/parser)
- [แบบฟอร์มขอไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)