---
title: แยกข้อความจากหน้าเฉพาะในรูปแบบ PDF
linktitle: แยกข้อความจากหน้าเฉพาะในรูปแบบ PDF
second_title: GroupDocs.Parser .NET API
description: แยกข้อความจาก PDF โดยใช้ GroupDocs.Parser สำหรับ .NET ดึงข้อมูลเนื้อหาเฉพาะหน้าได้อย่างง่ายดายด้วยไลบรารีอันทรงพลังนี้
weight: 15
url: /th/net/pdf-processing/extract-text-from-specific-page-in-pdf/
type: docs
---
# แยกข้อความจากหน้าเฉพาะในรูปแบบ PDF

## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากหน้าใดหน้าหนึ่งภายในเอกสาร PDF GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสารรูปแบบต่างๆ รวมถึง PDF, Microsoft Word, Excel และอื่นๆ อีกมากมาย ทำตามขั้นตอนเหล่านี้เพื่อรวมการแยกข้อความเข้ากับแอปพลิเคชัน .NET ของคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- Visual Studio: สภาพแวดล้อมการพัฒนาแบบรวม (IDE) สำหรับการพัฒนา .NET
-  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดไลบรารี่จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ความรู้เกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
- ไฟล์ PDF ตัวอย่าง: เอกสาร PDF สำหรับแยกข้อความ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโค้ด C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ยกตัวอย่าง`Parser`คลาสโดยระบุเส้นทางไปยังไฟล์ PDF ตัวอย่างของคุณ
```csharp
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสของคุณที่นี่
}
```
## ขั้นตอนที่ 2: รับข้อมูลเอกสาร
 รับข้อมูลเกี่ยวกับเอกสาร PDF โดยใช้`GetDocumentInfo()` วิธี.
```csharp
// รับข้อมูลเอกสาร
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## ขั้นตอนที่ 3: วนซ้ำหน้าต่างๆ
วนซ้ำแต่ละหน้าของเอกสารเพื่อเลือกหน้าเฉพาะสำหรับการแยกข้อความ
```csharp
// ทำซ้ำบนหน้าต่างๆ
for (int p = 0; p < documentInfo.PageCount; p++)
{
    // รหัสของคุณที่นี่
}
```
## ขั้นตอนที่ 4: แยกข้อความออกจากหน้า
 แยกข้อความจากหน้าที่ต้องการโดยใช้`GetText(int pageIndex)` วิธี.
```csharp
// แยกข้อความลงในเครื่องอ่าน
using (TextReader reader = parser.GetText(pageIndex))
{
    // รหัสของคุณที่นี่
    string extractedText = reader.ReadToEnd();
    Console.WriteLine(extractedText); // ส่งออกข้อความที่แยกออกมา
}
```

## บทสรุป
ตอนนี้คุณได้เรียนรู้วิธีแยกข้อความจากหน้าใดหน้าหนึ่งในไฟล์ PDF โดยใช้ GroupDocs.Parser สำหรับ .NET แล้ว กระบวนการนี้เกี่ยวข้องกับการเริ่มต้น parser การดึงข้อมูลเอกสาร การวนซ้ำหน้า และการแยกข้อความออกจากหน้าที่ต้องการ รวมขั้นตอนเหล่านี้เข้ากับแอปพลิเคชัน .NET ของคุณเพื่อจัดการการแยกข้อความ PDF ได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สำหรับ .NET เข้ากันได้กับ .NET Framework ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Parser สำหรับ .NET รองรับ .NET Framework เวอร์ชัน 4.5 ขึ้นไป
### GroupDocs.Parser สามารถแยกข้อความจากไฟล์ PDF ที่เข้ารหัสได้หรือไม่
ไม่ GroupDocs.Parser ไม่รองรับการแยกข้อความจากไฟล์ PDF ที่เข้ารหัสหรือป้องกันด้วยรหัสผ่าน
### GroupDocs.Parser จัดการกับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบที่หลากหลาย รวมถึง Microsoft Word, Excel, PowerPoint และอื่นๆ
### มีรุ่นทดลองใช้งานสำหรับ GroupDocs.Parser หรือไม่
 ใช่ คุณสามารถเข้าถึง GroupDocs.Parser รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถค้นหาการสนับสนุนด้านเทคนิคและมีส่วนร่วมกับชุมชนได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).