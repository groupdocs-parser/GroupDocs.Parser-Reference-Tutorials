---
title: แยกข้อความจากแผ่นงาน Excel
linktitle: แยกข้อความจากแผ่นงาน Excel
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากชีต Excel โดยใช้ GroupDocs.Parser สำหรับ .NET ขั้นตอนง่ายๆ เพื่อการแยกข้อความอย่างมีประสิทธิภาพ
weight: 14
url: /th/net/excel-document-processing/extract-text-from-excel-sheet/
type: docs
---
# แยกข้อความจากแผ่นงาน Excel

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีแยกข้อความจากชีต Excel โดยใช้ไลบรารี GroupDocs.Parser สำหรับ .NET เครื่องมืออันทรงพลังนี้ช่วยให้เราแยกวิเคราะห์และวิเคราะห์รูปแบบเอกสารต่าง ๆ ได้อย่างมีประสิทธิภาพ รวมถึงสเปรดชีต Excel เพื่อแยกข้อมูลที่เป็นข้อความ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET ที่เข้ากันได้
-  GroupDocs.Parser Library: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ไฟล์ Excel ตัวอย่าง: เตรียมไฟล์ Excel ตัวอย่างที่คุณจะใช้สำหรับการแยกข้อความ

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้เพิ่มเนมสเปซที่จำเป็นให้กับโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser`คลาสโดยระบุเส้นทางไปยังไฟล์ Excel ตัวอย่างของคุณ
```csharp
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //ดำเนินการสกัดต่อ...
}
```
## ขั้นตอนที่ 2: ดึงข้อมูลเอกสาร
 ดึงข้อมูลเอกสารโดยใช้`GetDocumentInfo` วิธี.
```csharp
// รับข้อมูลเอกสาร
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## ขั้นตอนที่ 3: วนซ้ำชีตและแยกข้อความ
 วนซ้ำแต่ละแผ่นงานในไฟล์ Excel และแยกข้อความโดยใช้`GetText` วิธี.
```csharp
// ทำซ้ำบนแผ่นงาน
for (int p = 0; p < documentInfo.PageCount; p++)
{
    // พิมพ์หมายเลขหน้า
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    // แยกข้อความเข้าสู่เครื่องอ่าน
    using (TextReader reader = parser.GetText(p))
    {
        // พิมพ์ข้อความจากสเปรดชีต
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สาธิตวิธีการแยกข้อความจากแผ่นงาน Excel โดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมความสามารถในการแยกวิเคราะห์เอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### ฉันสามารถแยกเขตข้อมูลเฉพาะจาก Excel โดยใช้ GroupDocs.Parser ได้หรือไม่
ได้ คุณสามารถแยกเขตข้อมูลเฉพาะได้โดยใช้ตรรกะที่กำหนดเองเพื่อแยกวิเคราะห์และวิเคราะห์ข้อความที่แยกออกมา
### GroupDocs.Parser รองรับรูปแบบเอกสารอื่นนอกเหนือจาก Excel หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, PowerPoint และอื่นๆ
### ฉันสามารถจัดการไฟล์ Excel ขนาดใหญ่อย่างมีประสิทธิภาพด้วย GroupDocs.Parser ได้หรือไม่
GroupDocs.Parser ได้รับการปรับให้เหมาะสมเพื่อประสิทธิภาพและสามารถจัดการไฟล์ขนาดใหญ่ได้อย่างมีประสิทธิภาพ
### GroupDocs.Parser เหมาะสำหรับการประมวลผลไฟล์ Excel หลายไฟล์เป็นชุดหรือไม่
ได้ คุณสามารถใช้ GroupDocs.Parser สำหรับการประมวลผลเป็นชุดเพื่อแยกข้อความจากไฟล์ Excel หลายไฟล์พร้อมกันได้
### GroupDocs.Parser ให้การสนับสนุนหรือความช่วยเหลือสำหรับนักพัฒนาหรือไม่
 ใช่ นักพัฒนาสามารถขอรับการสนับสนุนหรือความช่วยเหลือได้จากฟอรัมชุมชน GroupDocs[ที่นี่](https://forum.groupdocs.com/c/parser/17).