---
title: แยกรูปภาพจาก PDF
linktitle: แยกรูปภาพจาก PDF
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกรูปภาพจากเอกสาร PDF โดยใช้ GroupDocs.Parser สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด
type: docs
weight: 12
url: /th/net/pdf-processing/extract-images-from-pdf/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกรูปภาพจากเอกสาร PDF GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, PPTX และอื่นๆ ในสภาพแวดล้อม .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถแยกรูปภาพจากไฟล์ PDF ได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
-  GroupDocs.Parser สำหรับไลบรารี .NET (ดาวน์โหลดไฟล์[ที่นี่](https://releases.groupdocs.com/parser/net/-)

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้รวมเนมสเปซที่จำเป็นในไฟล์โค้ด C# ของคุณ
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser`คลาสโดยระบุเส้นทางไปยังไฟล์ PDF ตัวอย่างของคุณ
```csharp
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสในการแยกภาพจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: แยกรูปภาพจาก PDF
 ภายใน`using` บล็อก ใช้`GetImages` วิธีการของ`Parser` อินสแตนซ์เพื่อดึงชุดรูปภาพจากเอกสาร PDF
```csharp
// แยกรูปภาพออกจาก PDF
IEnumerable<PageImageArea> images = parser.GetImages();
```
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการบันทึกรูปภาพ
กำหนดตัวเลือกเพื่อระบุวิธีการบันทึกภาพที่แยกออกมา ที่นี่เราจะบันทึกภาพในรูปแบบ PNG
```csharp
// สร้างตัวเลือกในการบันทึกภาพในรูปแบบ PNG
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## ขั้นตอนที่ 4: วนซ้ำรูปภาพที่แยกแล้วและบันทึก
 วนซ้ำแต่ละภาพใน`images` รวบรวมและบันทึกเป็นไฟล์ PNG ตามลำดับ
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
ในบทช่วยสอนนี้ เราได้สาธิตวิธีการแยกรูปภาพจากเอกสาร PDF โดยใช้ GroupDocs.Parser สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถรวมฟังก์ชันการแยกรูปภาพเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารอื่นหรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ฉันสามารถแก้ไขตัวเลือกการแยกภาพได้หรือไม่?
อย่างแน่นอน! GroupDocs.Parser มีตัวเลือกมากมายในการปรับแต่งการแยกรูปภาพ เช่น รูปแบบรูปภาพ และการตั้งค่าคุณภาพ
### GroupDocs.Parser ต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์หรือไม่
 ใช่ จำเป็นต้องมีใบอนุญาตเชิงพาณิชย์เพื่อใช้ GroupDocs.Parser ในสภาพแวดล้อมการผลิต เรียนรู้เพิ่มเติม[ที่นี่](https://purchase.groupdocs.com/buy).
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือเพิ่มเติมได้จากที่ไหน?
 ไปที่ GroupDocs.Parser[ฟอรั่ม](https://forum.groupdocs.com/c/parser/17) สำหรับการสนับสนุนและคำแนะนำจากชุมชน
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถขอรับการทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/) เพื่อสำรวจคุณสมบัติของ GroupDocs.Parser