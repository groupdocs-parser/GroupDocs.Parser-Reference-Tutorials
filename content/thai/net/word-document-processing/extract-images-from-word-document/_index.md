---
title: แยกรูปภาพออกจากเอกสาร Word
linktitle: แยกรูปภาพออกจากเอกสาร Word
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกรูปภาพจากเอกสาร Word โดยใช้ GroupDocs.Parser สำหรับ .NET บทช่วยสอนนี้ให้คำแนะนำทีละขั้นตอนสำหรับการรวมรูปภาพเข้ากับ .NET ของคุณ
weight: 11
url: /th/net/word-document-processing/extract-images-from-word-document/
type: docs
---
# แยกรูปภาพออกจากเอกสาร Word

## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีแยกรูปภาพจากเอกสาร Word โดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารี .NET ที่มีประสิทธิภาพ ซึ่งช่วยให้คุณสามารถแยกวิเคราะห์และแยกข้อความ ข้อมูลเมตา รูปภาพ และอื่นๆ จากรูปแบบเอกสารต่างๆ รวมถึง Word (DOCX)
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง GroupDocs.Parser สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณเพื่อใช้ฟังก์ชัน GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
ตอนนี้ เรามาแบ่งกระบวนการแยกรูปภาพจากเอกสาร Word ออกเป็นขั้นตอนง่ายๆ:
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 คุณจะเริ่มต้นด้วยการสร้างอินสแตนซ์ของ`Parser`คลาสโดยระบุเส้นทางไปยังเอกสาร Word ของคุณเป็นอินพุต
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสสำหรับการแยกภาพอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: แยกรูปภาพออกจากเอกสาร Word
 ต่อไปให้ใช้`GetImages()` วิธีการของ`Parser` วัตถุเพื่อแยกรูปภาพออกจากเอกสาร
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## ขั้นตอนที่ 3: กำหนดตัวเลือกการบันทึกรูปภาพ
ระบุตัวเลือกสำหรับการบันทึกภาพที่แยกออกมา ตัวอย่างเช่น คุณสามารถเลือกรูปแบบภาพ (เช่น PNG) และกำหนดการตั้งค่าอื่นๆ ได้
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## ขั้นตอนที่ 4: วนซ้ำรูปภาพที่แยกแล้วและบันทึก
วนซ้ำแต่ละภาพที่แยกออกมาและบันทึกลงในไฟล์โดยใช้ตัวเลือกที่ระบุ
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
ในบทช่วยสอนนี้ คุณได้เรียนรู้วิธีแยกรูปภาพจากเอกสาร Word โดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมความสามารถในการแยกวิเคราะห์เอกสารและการแยกรูปภาพเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกรูปภาพจากรูปแบบเอกสารอื่นนอกเหนือจาก Word ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, PowerPoint, Excel และอื่นๆ
### ฉันจะรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวเพื่อการทดสอบได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะหาเอกสารเพิ่มเติมเกี่ยวกับ GroupDocs.Parser for .NET ได้ที่ไหน
 คุณสามารถดูเอกสารฉบับสมบูรณ์ได้[ที่นี่](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถสำรวจคุณสมบัติของ GroupDocs.Parser พร้อมให้ทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนหรือถามคำถามที่เกี่ยวข้องกับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถโพสต์คำถามของคุณได้ที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).