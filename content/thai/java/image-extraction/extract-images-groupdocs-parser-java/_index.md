---
date: '2026-01-16'
description: เรียนรู้วิธีบันทึกภาพจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ Java รวมถึงการตั้งค่า
  ตัวอย่างโค้ด และแนวปฏิบัติที่ดีที่สุดสำหรับการดึงภาพใน Java
keywords:
- extract images from documents
- GroupDocs.Parser for Java
- image extraction from documents
title: วิธีบันทึกภาพด้วย GroupDocs.Parser สำหรับ Java
type: docs
url: /th/java/image-extraction/extract-images-groupdocs-parser-java/
weight: 1
---

# วิธีบันทึกภาพด้วย GroupDocs.Parser สำหรับ Java

ต้องการวิธีที่เชื่อถือได้ในการบันทึกภาพโดยอัตโนมัติจากรูปแบบเอกสารต่าง ๆ หรือไม่? **GroupDocs.Parser for Java** มีความสามารถในการสกัดภาพที่ทรงพลังซึ่งทำให้ภารกิจนี้ง่ายขึ้น ในคู่มือนี้เราจะพาคุณผ่านการตั้งค่าห้องสมุด การสกัดภาพ และการบันทึกลงดิสก์—เหมาะสำหรับการวิเคราะห์ข้อมูล การนำเนื้อหาไปใช้ใหม่ หรือการเก็บถาวร

## คำตอบด่วน
- **“การบันทึกภาพ” หมายถึงอะไร?** ใช้ GroupDocs.Parser เพื่อสกัดรูปภาพที่ฝังอยู่และเขียนลงในโฟลเดอร์ในเครื่องของคุณ  
- **รูปแบบใดบ้างที่รองรับ?** PDFs, Word, Excel, PowerPoint, และรูปแบบเอกสารทั่วไปอื่น ๆ มากมาย  
- **ฉันต้องการไลเซนส์หรือไม่?** ทดลองใช้งานฟรีสำหรับการประเมิน; ต้องมีไลเซนส์เต็มสำหรับการใช้งานจริง  
- **ฉันสามารถประมวลผลชุดใหญ่ได้หรือไม่?** ได้—รวม API กับเครื่องมือความพร้อมของ Java เพื่อการสกัดแบบชุด  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า

## “การบันทึกภาพ” หมายถึงอะไรในบริบทของการแยกข้อมูลเอกสาร?
การบันทึกภาพหมายถึงการดึงรูปภาพแต่ละภาพที่ฝังอยู่ในเอกสารและเขียนข้อมูลไบต์ลงในไฟล์บนระบบไฟล์ของคุณ ซึ่งทำให้คุณสามารถนำภาพเหล่านั้นไปใช้ใหม่นอกไฟล์ต้นฉบับ เช่น สำหรับแกลเลอรีเว็บ รายงาน หรือสายงานการเรียนรู้ของเครื่อง

## ทำไมต้องใช้ GroupDocs.Parser สำหรับ Java เพื่อบันทึกภาพ?
- **Unified API** – อินเทอร์เฟซเดียวที่ทำงานข้ามรูปแบบหลายสิบแบบได้อย่างสอดคล้อง  
- **High fidelity** – สกัดภาพโดยไม่สูญเสียคุณภาพ  
- **Performance‑focused** – การสกัดแบบสตรีมช่วยลดการใช้หน่วยความจำ  
- **Easy integration** – รองรับ Maven/Gradle และคลาส Java ที่ชัดเจน

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK) 8+** ติดตั้งแล้ว  
- **Maven** สำหรับการจัดการ dependency  
- ความคุ้นเคยพื้นฐานกับแนวคิดการเขียนโปรแกรม Java

## การตั้งค่า GroupDocs.Parser สำหรับ Java

### ใช้ Maven
เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจากหน้า releases อย่างเป็นทางการ: [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### การรับไลเซนส์
- **Free Trial:** เริ่มต้นด้วยการทดลองเพื่อสำรวจฟีเจอร์  
- **Temporary License:** ขอทดลองต่ออายุเพื่อการทดสอบโดยไม่มีข้อจำกัด  
- **Purchase:** รับไลเซนส์เชิงพาณิชย์สำหรับการใช้งานในสภาพแวดล้อมการผลิต

### การเริ่มต้นพื้นฐาน
ยืนยันว่าห้องสมุดตั้งค่าอย่างถูกต้องโดยการสร้างอินสแตนซ์ `Parser`:

```java
import com.groupdocs.parser.Parser;

try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
    System.out.println("GroupDocs.Parser initialized successfully!");
} catch (Exception e) {
    e.printStackTrace();
}
```

## คู่มือการใช้งาน

เราจะครอบคลุมสองฟีเจอร์หลัก: **การสกัดภาพ** และ **การบันทึกภาพ**.

### สกัดภาพจากเอกสาร

**ภาพรวม:** ใช้ GroupDocs.Parser เพื่อดึงภาพทุกภาพออกจากเอกสาร.

#### ขั้นตอนที่ 1: นำเข้าแพ็กเกจที่จำเป็น
```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
```

#### ขั้นตอนที่ 2: เริ่มต้นอ็อบเจ็กต์ Parser
```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
    // Proceed with image extraction logic
} catch (Exception e) {
    e.printStackTrace();
}
```
*คลาส `Parser` ให้คุณเข้าถึงเนื้อหาภายในของเอกสาร. แทนที่ `"YOUR_DOCUMENT_DIRECTORY"` ด้วยเส้นทางจริงของไฟล์ของคุณ*

#### ขั้นตอนที่ 3: สกัดภาพ
```java
Iterable<PageImageArea> images = parser.getImages();
if (images == null) {
    System.out.println("Image extraction isn't supported.");
    return;
}
```
*หาก `getImages()` คืนค่า `null` หมายความว่ารูปแบบปัจจุบันไม่รองรับการสกัดภาพ*

#### ขั้นตอนที่ 4: วนลูปและดึงรายละเอียดของภาพ
```java
for (PageImageArea image : images) {
    int pageIndex = image.getPage().getIndex(); // Page index of the image
    String rectangle = image.getRectangle().toString(); // Bounding box coordinates
    String fileType = image.getFileType(); // File type of the image
}
```

### บันทึกภาพที่สกัดลงในไดเรกทอรีผลลัพธ์

**ภาพรวม:** เขียนภาพที่สกัดแต่ละภาพลงในโฟลเดอร์ที่คุณเลือก.

#### ขั้นตอนที่ 1: ตั้งค่าเส้นทางและสตรีมผลลัพธ์
```java
int imageNumber = 0;
for (PageImageArea image : parser.getImages()) {
    String outputFilePath = String.format("%s/image_%d.%s", "YOUR_OUTPUT_DIRECTORY", imageNumber++, image.getFileType());
    
    try (OutputStream outputStream = new FileOutputStream(outputFilePath)) {
        // Save the image
    } catch (Exception e) {
        e.printStackTrace();
    }
}
```
*แทนที่ `"YOUR_OUTPUT_DIRECTORY"` ด้วยโฟลเดอร์ที่คุณต้องการบันทึกภาพ*

#### ขั้นตอนที่ 2: เขียนข้อมูลภาพ
```java
try (OutputStream outputStream = new FileOutputStream(outputFilePath)) {
    image.save(outputStream);
}
```
*เมธอด `save` จะสตรีมไบต์ของภาพโดยตรงไปยังระบบไฟล์*

#### เคล็ดลับการแก้ไขปัญหา
- **File Permissions:** ตรวจสอบให้แน่ใจว่ากระบวนการมีสิทธิ์เขียนในโฟลเดอร์เป้าหมาย  
- **Invalid Paths:** ตรวจสอบเส้นทางต้นทางและปลายทางให้ไม่มีการพิมพ์ผิดหรือโฟลเดอร์หาย

## การประยุกต์ใช้งานจริง
การสกัดภาพมีคุณค่าในหลายสถานการณ์:
1. **Content Archiving:** เก็บรักษาสินทรัพย์ภาพจากเอกสารเก่า  
2. **Data Analysis:** ป้อนภาพที่สกัดเข้าสู่สายงานการจดจำภาพ  
3. **Document Conversion:** ย้ายเอกสารพร้อมรักษากราฟิกที่ฝังอยู่ทั้งหมด  
4. **Web Scraping Enhancements:** เพิ่มข้อมูลที่รวบรวมด้วยเนื้อหาภาพจากไฟล์ที่อัปโหลด

## การพิจารณาประสิทธิภาพ
- **Memory Management:** ปรับขนาด heap ของ JVM (`-Xmx`) เมื่อประมวลผลไฟล์ขนาดใหญ่มาก  
- **Efficient I/O:** เขียนเป็นชุดหรือใช้ buffered streams เพื่อลดการสั่นของดิสก์

## วิธีบันทึกภาพจากเอกสาร
ส่วนนี้เชื่อมโยงคีย์เวิร์ดหลักกับขั้นตอนที่อธิบายไว้ข้างต้นอย่างชัดเจน โดยทำตามขั้นตอนข้างต้น คุณจะรู้ **วิธีบันทึกภาพ** ที่สกัดด้วย GroupDocs.Parser ไม่ว่าจะเป็นเอกสารประเภทใดก็ตาม

## ปัญหาทั่วไปและวิธีแก้

| ปัญหา | วิธีแก้ |
|-------|----------|
| **OutOfMemoryError** บน PDF ขนาดใหญ่ | ประมวลผลหน้าแบบต่อเนื่องและปล่อย `PageImageArea` แต่ละอันหลังจากบันทึก |
| **Unsupported format** error | ตรวจสอบว่าประเภทเอกสารถูกระบุในรายการรูปแบบที่รองรับของ GroupDocs.Parser |
| **Corrupted output files** | ตรวจสอบให้แน่ใจว่า stream ผลลัพธ์ถูกปิดอย่างถูกต้อง; หลีกเลี่ยงการเขียนไฟล์ที่มีชื่อเดียวกันสองครั้ง |

## คำถามที่พบบ่อย

**Q: รูปแบบไฟล์ใดบ้างที่รองรับการสกัดภาพ?**  
A: PDFs, DOC/DOCX, PPT/PPTX, XLS/XLSX, และรูปแบบยอดนิยมอื่น ๆ อีกหลายแบบ

**Q: จะจัดการเอกสารขนาดใหญ่อย่างมีประสิทธิภาพได้อย่างไร?**  
A: ใช้การแบ่งหน้า—ประมวลผลส่วนย่อยของหน้าในแต่ละครั้งและปล่อยทรัพยากรก่อนย้ายไปยังชุดถัดไป

**Q: สามารถสกัดเมตาดาต้าพร้อมกับภาพได้หรือไม่?**  
A: ได้, GroupDocs.Parser มี API เมตาดาต้าที่ให้คุณดึงข้อมูลเช่นผู้เขียน, วันที่สร้าง ฯลฯ

**Q: การเขียนภาพไปยังไดรฟ์เครือข่ายปลอดภัยหรือไม่?**  
A: ใช้งานได้ดีตราบใดที่กระบวนการ Java มีสิทธิ์เครือข่ายที่จำเป็นและความหน่วงเวลายอมรับได้

**Q: GroupDocs.Parser รองรับการประมวลผลแบบขนานหรือไม่?**  
A: ไลบรารีเองเป็น thread‑safe; คุณสามารถรันหลายอินสแตนซ์ `Parser` พร้อมกันโดยใช้ `ExecutorService` ของ Java

## สรุป
คุณได้เรียนรู้ **วิธีบันทึกภาพ** จากเอกสารโดยใช้ GroupDocs.Parser สำหรับ Java แล้ว ความสามารถนี้เปิดประตูสู่การเก็บถาวรอัตโนมัติ, การวิเคราะห์ภาพ, และการย้ายเอกสารอย่างราบรื่น ขั้นต่อไปสำรวจการสกัดข้อความหรือการจัดการเมตาดาต้าตามต้องการเพื่อเพิ่มคุณค่าให้กับสายงานการประมวลผลเอกสารของคุณ

---

**อัปเดตล่าสุด:** 2026-01-16  
**ทดสอบด้วย:** GroupDocs.Parser 25.5 for Java  
**ผู้เขียน:** GroupDocs