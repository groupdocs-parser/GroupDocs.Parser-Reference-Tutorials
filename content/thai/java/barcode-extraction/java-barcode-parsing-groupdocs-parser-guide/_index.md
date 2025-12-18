---
date: '2025-12-16'
description: เรียนรู้วิธีอ่าน QR code ด้วย Java โดยใช้ GroupDocs.Parser และทำให้การสกัดข้อมูลบาร์โค้ดมีประสิทธิภาพในแอปพลิเคชัน
  Java ของคุณ
keywords:
- Java barcode parsing
- GroupDocs.Parser for Java
- barcode data extraction
title: อ่าน QR Code ด้วย Java – เชี่ยวชาญการแยกบาร์โค้ดด้วย GroupDocs.Parser
type: docs
url: /th/java/barcode-extraction/java-barcode-parsing-groupdocs-parser-guide/
weight: 1
---

# อ่าน QR Code Java – การแยกวิเคราะห์บาร์โค้ดขั้นสูงด้วย GroupDocs.Parser

ในสภาพแวดล้อมธุรกิจที่เคลื่อนที่อย่างรวดเร็วในปัจจุบัน ความสามารถในการ **read QR code java** อย่างเร็วและแม่นยำสามารถทำให้กระบวนการทำงานที่ขับเคลื่อนด้วยข้อมูลเป็นไปอย่างราบรื่นอย่างมาก ไม่ว่าคุณจะกำลังประมวลผลใบแจ้งหนี้, ใบกำกับการจัดส่ง, หรือรายการสินค้าคงคลัง การดึงข้อมูลบาร์โค้ดโดยตรงจากเอกสารช่วยประหยัดเวลาและลดข้อผิดพลาดจากการป้อนข้อมูลด้วยมือ คู่มือนี้จะแสดงขั้นตอนโดยละเอียดว่าตั้งค่า GroupDocs.Parser สำหรับ Java อย่างไร, กำหนดเทมเพลตบาร์โค้ด, และแยก QR Code อย่างมีประสิทธิภาพ

## คำตอบสั้น
- **ไลบรารีใดที่ทำให้ฉัน read QR code java?** GroupDocs.Parser สำหรับ Java  
- **ต้องมีลิขสิทธิ์หรือไม่?** มีรุ่นทดลองฟรีสำหรับการประเมิน; ต้องมีลิขสิทธิ์เต็มสำหรับการใช้งานจริง  
- **ประเภทเอกสารที่รองรับมีอะไรบ้าง?** PDF, DOCX, XLSX, รูปภาพ, และอื่น ๆ  
- **สามารถดึงบาร์โค้ดหลายรายการพร้อมกันได้หรือไม่?** ได้ – ตัว parser รองรับบาร์โค้ดหลายรายการต่อเอกสาร  
- **ต้องใช้ Java เวอร์ชันใด?** Java 8 หรือสูงกว่า  

## read QR code java คืออะไร?
การอ่าน QR Code ใน Java หมายถึงการใช้ไลบรารีที่สามารถค้นหา, ถอดรหัส, และคืนค่าข้อมูลที่ฝังอยู่ในภาพบาร์โค้ดภายในเอกสาร GroupDocs.Parser มี API ที่ง่ายต่อการกำหนดฟิลด์บาร์โค้ด, ใช้เทมเพลต, และดึงค่าที่ต้องการโดยไม่ต้องเขียนโค้ดประมวลผลภาพระดับล่าง

## ทำไมต้องใช้ GroupDocs.Parser สำหรับการดึงข้อมูลบาร์โค้ด?
- **ความแม่นยำสูง** – การจดจำบาร์โค้ดในตัวทำงานได้กับรูปแบบหลากหลาย  
- **รองรับเอกสารหลายประเภท** – แยกบาร์โค้ดจาก PDF, ไฟล์ Word, สเปรดชีต, และรูปภาพ  
- **ขับเคลื่อนด้วยเทมเพลต** – กำหนดตำแหน่งและประเภทบาร์โค้ดอย่างแม่นยำ ลดผลบวกเท็จ  
- **ขยายได้** – ประมวลผลไฟล์เดี่ยวหรือชุดเอกสารขนาดใหญ่เป็นชุด  

## ข้อกำหนดเบื้องต้น
- **ไลบรารีและการพึ่งพา**: GroupDocs.Parser สำหรับ Java (เวอร์ชัน 25.5 หรือใหม่กว่า)  
- **สภาพแวดล้อม**: ติดตั้ง Java Development Kit (JDK 8+) แล้ว  
- **ความรู้พื้นฐาน**: การเขียนโปรแกรม Java เบื้องต้นและการตั้งค่าโครงการ Maven  

## การตั้งค่า GroupDocs.Parser สำหรับ Java
เพื่อเริ่มใช้ GroupDocs.Parser ให้เพิ่มเข้าไปในโครงการ Maven ของคุณ

### ใช้ Maven
เพิ่มการกำหนดค่าต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

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
หรือดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/)

#### การจัดหาลิขสิทธิ์
- **รุ่นทดลองฟรี** – เริ่มต้นด้วยรุ่นทดลองเพื่อสำรวจฟีเจอร์  
- **ลิขสิทธิ์ชั่วคราว** – ขอรับลิขสิทธิ์ชั่วคราวสำหรับการเข้าถึงต่อเนื่อง  
- **การซื้อ** – ซื้อสมาชิกเพื่อใช้ความสามารถเต็มรูปแบบ  

## คู่มือการใช้งาน
เราจะพาคุณผ่านสองฟีเจอร์หลัก: การกำหนดและแยกเทมเพลตบาร์โค้ด, และการสร้างอินสแตนซ์ parser ที่นำกลับมาใช้ใหม่ได้

### ฟีเจอร์ 1: กำหนดและแยกเทมเพลตบาร์โค้ด
ส่วนนี้แสดงวิธีตั้งค่าเทมเพลต QR‑code และดึงค่าที่ได้

#### ขั้นตอนที่ 1: กำหนดฟิลด์บาร์โค้ด
ระบุตำแหน่ง, ขนาด, และประเภทของบาร์โค้ด:

```java
// Define a barcode field with its position and type
TemplateBarcode barcode = new TemplateBarcode(
        new Rectangle(new Point(405, 55), new Size(100, 50)),
        "QR");
```

#### ขั้นตอนที่ 2: สร้างเทมเพลต
ใส่ฟิลด์บาร์โค้ดไว้ในอ็อบเจ็กต์เทมเพลต:

```java
// Create a template containing the barcode field
template = new Template(Arrays.asList(new TemplateItem[]{barcode}));
```

#### ขั้นตอนที่ 3: แยกเอกสารด้วย Parser
เปิดโฟลเดอร์เอกสาร, ใช้เทมเพลต, แล้วอ่านค่าของ QR‑code:

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
    DocumentData data = parser.parseByTemplate(template);

    // Iterate through extracted data and print barcode values
    for (int i = 0; i < data.getCount(); i++) {
        PageArea pageArea = data.get(i).getPageArea();
        if (pageArea instanceof PageBarcodeArea) {
            PageBarcodeArea area = (PageBarcodeArea) pageArea;
            System.out.println(data.get(i).getName() + ": " + area.getValue());
        } else {
            System.out.println(data.get(i).getName() + ": Not a template barcode field");
        }
    }
}
```

Parser จะสแกนแต่ละหน้า, จับคู่กับพื้นที่ QR‑code, และคืนสตริงที่ถอดรหัสแล้ว

### ฟีเจอร์ 2: สร้างและใช้ Document Parser
หลังจากกำหนดเทมเพลตแล้ว คุณมักต้องการอินสแตนซ์ parser สำหรับการทำงานอื่น ๆ เช่น การดึงข้อความหรือการสแกนบาร์โค้ดเพิ่มเติม

#### ขั้นตอนที่ 1: สร้างอินสแตนซ์ Parser
สร้างอ็อบเจ็กต์ `Parser` ที่ชี้ไปยังแหล่งเอกสารของคุณ:

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
    System.out.println("Document parser created and ready to use.");
}
```

ตอนนี้ parser พร้อมสำหรับการทำงานต่อ เช่น การประมวลผลหลายไฟล์ในลูป  

## การประยุกต์ใช้งานจริง
ต่อไปนี้เป็นสามสถานการณ์ที่ **read QR code java** มีประโยชน์อย่างยิ่ง

1. **การจัดการสินค้าคงคลัง** – ดึงรหัสสินค้าอัตโนมัติจาก PDF การจัดส่ง  
2. **การดำเนินงานด้านค้าปลีก** – สแกน QR Code บนใบเสร็จเพื่อเชื่อมโยงการซื้อกับโปรแกรมสะสมคะแนน  
3. **การติดตามห่วงโซ่อุปทาน** – ตรวจสอบการเคลื่อนย้ายสินค้าโดยดึงบาร์โค้ดจากเอกสารศุลกากร  

## พิจารณาด้านประสิทธิภาพ
- **ใช้ parser ซ้ำ** เมื่อประมวลผลไฟล์จำนวนมากเพื่อลดภาระการสร้างอ็อบเจ็กต์ใหม่  
- **จำกัดขนาดเทมเพลต** ให้เป็นพื้นที่ที่เล็กที่สุดที่ยังจับบาร์โค้ดได้อย่างเชื่อถือได้  
- **วัดการใช้หน่วยความจำ** ด้วยเครื่องมืออย่าง VisualVM เพื่อหลีกเลี่ยงการรั่วไหลในบริการที่ทำงานต่อเนื่อง  

## ปัญหาที่พบบ่อยและวิธีแก้
| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|-------|-----|
| ไม่ได้ค่าบาร์โค้ด | พิกัดสี่เหลี่ยมไม่ถูกต้อง | ตรวจสอบตำแหน่งบาร์โค้ดโดยใช้เครื่องมือวัดของ PDF viewer |
| Parser ขว้าง `IOException` | เส้นทางไฟล์ไม่ถูกหรือเข้าถึงไม่ได้ | ตรวจสอบให้แอปมีสิทธิ์อ่านและเส้นทางเป็นแบบ absolute หรือ resolve อย่างถูกต้อง |
| ประมวลผลช้าใน PDF ขนาดใหญ่ | สร้าง Parser ใหม่ทุกหน้า | ใช้ Parser ตัวเดียวกันหลายหน้า หรือประมวลผลไฟล์เป็นชุด |

## คำถามที่พบบ่อย
**ถาม: จะจัดการกับรูปแบบเอกสารที่ไม่รองรับอย่างไร?**  
ตอบ: ตรวจสอบให้แน่ใจว่าคุณใช้เวอร์ชัน GroupDocs.Parser ที่ระบุรูปแบบนั้นเป็นที่รองรับ หากไม่มี ให้แปลงเป็น PDF หรือรูปภาพก่อน

**ถาม: สามารถแยกบาร์โค้ดจากรูปภาพได้หรือไม่?**  
ตอบ: ได้, GroupDocs.Parser สามารถดึงข้อมูลบาร์โค้ดจากไฟล์ภาพเช่น PNG, JPEG, และ TIFF

**ถาม: จุดบกพร่องทั่วไปเมื่อกำหนดเทมเพลตคืออะไร?**  
ตอบ: สี่เหลี่ยมไม่ตรงตำแหน่ง, ประเภทบาร์โค้ดผิด (เช่น “QR” vs. “CODE_128”), และลืมใส่ฟิลด์บาร์โค้ดในรายการของเทมเพลต

**ถาม: มีขีดจำกัดจำนวนบาร์โค้ดที่สามารถแยกพร้อมกันได้หรือไม่?**  
ตอบ: ไลบรารีออกแบบให้รองรับหลายบาร์โค้ด, แต่ประสิทธิภาพขึ้นกับทรัพยากรระบบและขนาดเอกสาร

**ถาม: จะขอความช่วยเหลือเมื่อเจอปัญหาได้จากที่ไหน?**  
ตอบ: โพสต์คำถามใน [GroupDocs Support Forum](https://forum.groupdocs.com/c/parser) หรือดูเอกสารอย่างเป็นทางการ  

## ขั้นตอนต่อไป
สำรวจฟีเจอร์ลึกของ GroupDocs.Parser โดยอ่าน [documentation](https://docs.groupdocs.com/parser/java/) ทดลองใช้รูปแบบเทมเพลตต่าง ๆ, ประเภทบาร์โค้ด, และการประมวลผลเป็นชุดเพื่อปรับให้เข้ากับเวิร์กโฟลว์ของคุณ

## แหล่งข้อมูล
- **Documentation**: คู่มือเต็มที่ [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/)  
- **API Reference**: รายละเอียด API ที่ [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)  
- **Download**: ดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs Downloads](https://releases.groupdocs.com/parser/java/)  
- **GitHub Repository**: ดูซอร์สโค้ดและร่วมพัฒนาได้ที่ [GroupDocs on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- **Free Support**: เข้าร่วมชุมชนที่ [GroupDocs Forum](https://forum.groupdocs.com/c/parser)  
- **Temporary License**: ขอรับลิขสิทธิ์ทดลองที่ [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license/)  

---

**อัปเดตล่าสุด:** 2025-12-16  
**ทดสอบกับ:** GroupDocs.Parser 25.5 (Java)  
**ผู้เขียน:** GroupDocs  

---