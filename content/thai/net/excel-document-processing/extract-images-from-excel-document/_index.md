---
title: แยกรูปภาพจากเอกสาร Excel
linktitle: แยกรูปภาพจากเอกสาร Excel
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกรูปภาพจากเอกสาร Excel โดยใช้ GroupDocs.Parser สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด
type: docs
weight: 10
url: /th/net/excel-document-processing/extract-images-from-excel-document/
---
## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีแยกรูปภาพจากเอกสาร Excel โดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้คุณสามารถแยกวิเคราะห์และแยกข้อความ ข้อมูลเมตา และรูปภาพจากรูปแบบเอกสารต่างๆ รวมถึงไฟล์ Excel
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET ที่ต้องการ
2.  ไลบรารี GroupDocs.Parser: ดาวน์โหลดและอ้างอิงไลบรารี GroupDocs.Parser คุณสามารถรับห้องสมุดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. ไฟล์ Excel ตัวอย่าง: เตรียมไฟล์ Excel ตัวอย่างที่คุณต้องการแยกรูปภาพ
## นำเข้าเนมสเปซ
รวมเนมสเปซที่จำเป็นในโครงการของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
ทำตามขั้นตอนเหล่านี้เพื่อแยกรูปภาพจากเอกสาร Excel:
## ขั้นตอนที่ 1: สร้างอินสแตนซ์คลาส Parser
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์ Excel ของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // รหัสของคุณที่นี่...
}
```
## ขั้นตอนที่ 2: ดึงรูปภาพจากเอกสาร Excel
 ใช้`GetImages()` วิธีการดึงภาพจากไฟล์ Excel
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## ขั้นตอนที่ 3: กำหนดตัวเลือกการแยกรูปภาพ
ระบุรูปแบบภาพและตัวเลือกอื่นๆ สำหรับการบันทึกภาพที่แยกออกมา ตัวอย่างเช่น หากต้องการบันทึกรูปภาพในรูปแบบ PNG:
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## ขั้นตอนที่ 4: วนซ้ำและบันทึกรูปภาพ
วนซ้ำภาพที่แยกออกมาและบันทึกแต่ละภาพลงในไฟล์
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // บันทึกภาพเป็นไฟล์ PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## บทสรุป
ในบทช่วยสอนนี้ คุณได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกรูปภาพจากเอกสาร Excel ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมความสามารถในการแยกรูปภาพเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ถาม: GroupDocs.Parser สามารถแยกรูปภาพจากรูปแบบเอกสารอื่นนอกเหนือจาก Excel ได้หรือไม่
ตอบ: ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, PowerPoint, PDF และอื่นๆ
### ถาม: ฉันจะรับการสนับสนุนหรือความช่วยเหลือเกี่ยวกับการบูรณาการ GroupDocs.Parser ได้อย่างไร
 ตอบ: สำหรับการสนับสนุนและความช่วยเหลือ โปรดไปที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### ถาม: GroupDocs.Parser ใช้งานได้ฟรีหรือไม่
 ตอบ: GroupDocs.Parser ให้ทดลองใช้ฟรี แต่หากต้องการใช้งานต่อ คุณอาจต้องซื้อใบอนุญาต ตรวจสอบ[ราคาและใบอนุญาต](https://purchase.groupdocs.com/buy)รายละเอียด.
### ถาม: ฉันสามารถลองใช้ GroupDocs.Parser ก่อนซื้อใบอนุญาตได้หรือไม่
 ตอบ: ได้ คุณจะได้รับ[ทดลองฟรี](https://releases.groupdocs.com/) เพื่อประเมิน GroupDocs.Parser
### ถาม: ฉันจะหาเอกสารโดยละเอียดสำหรับ GroupDocs.Parser ได้ที่ไหน
 ตอบ: อ้างถึงเนื้อหาที่ครอบคลุม[เอกสารประกอบ](https://reference.groupdocs.com/parser/net/) สำหรับข้อมูลโดยละเอียดเกี่ยวกับการใช้ GroupDocs.Parser