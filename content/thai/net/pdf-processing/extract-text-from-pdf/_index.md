---
title: แยกข้อความจาก PDF
linktitle: แยกข้อความจาก PDF
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสาร PDF โดยใช้ GroupDocs.Parser สำหรับ .NET บทช่วยสอนทีละขั้นตอนสำหรับนักพัฒนา
weight: 14
url: /th/net/pdf-processing/extract-text-from-pdf/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีแยกข้อความจากเอกสาร PDF โดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกข้อความ เมตาดาต้า และข้อมูลที่มีโครงสร้างจากรูปแบบเอกสารต่างๆ รวมถึง PDF, Microsoft Office และอื่นๆ
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
-  ติดตั้ง GroupDocs.Parser สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ขั้นแรก ให้เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโค้ด C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ยกตัวอย่าง`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์ PDF ตัวอย่างของคุณ:
```csharp
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: แยกข้อความจาก PDF
 ภายใน`Parser` เช่น ใช้`GetText()` วิธีการแยกข้อความจาก PDF:
```csharp
// แยกข้อความลงในเครื่องอ่าน
using (TextReader reader = parser.GetText())
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: อ่านและพิมพ์ข้อความที่แยกออกมา
 ตอนนี้อ่านข้อความที่แยกมาจาก`TextReader` และพิมพ์มัน:
```csharp
// พิมพ์ข้อความที่แยกออกมา
Console.WriteLine(reader.ReadToEnd());
```

## บทสรุป
 ในบทช่วยสอนนี้ เราได้กล่าวถึงพื้นฐานของการแยกข้อความจากเอกสาร PDF โดยใช้ GroupDocs.Parser สำหรับ .NET คุณได้เรียนรู้วิธีการเริ่มต้นไฟล์`Parser` แยกข้อความ และพิมพ์เนื้อหาที่แยกออกมา API นี้มอบวิธีที่ตรงไปตรงมาในการจัดการ PDF และรูปแบบเอกสารอื่นๆ โดยทางโปรแกรม

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบที่หลากหลาย รวมถึง DOCX, XLSX, PPTX และอื่นๆ
### ฉันสามารถลองใช้ GroupDocs.Parser ก่อนซื้อใบอนุญาตได้หรือไม่
 ใช่ คุณสามารถรับเวอร์ชันทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารสำหรับ GroupDocs.Parser ได้ที่ไหน
 มีเอกสารรายละเอียดให้[ที่นี่](https://tutorials.groupdocs.com/parser/net/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอความช่วยเหลือได้ในฟอรัมสนับสนุน[ที่นี่](https://forum.groupdocs.com/c/parser/17).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 สามารถรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).