---
title: แยกข้อความจากเพจในโหมด Raw
linktitle: แยกข้อความจากเพจในโหมด Raw
second_title: GroupDocs.Parser .NET API
description: เรียนรู้การแยกข้อความอย่างมีประสิทธิภาพจากหน้าเอกสารโดยใช้ Groupdocs.Parser สำหรับ .NET ในบทช่วยสอนที่ครอบคลุมนี้
type: docs
weight: 17
url: /th/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีใช้ Groupdocs.Parser สำหรับ .NET เพื่อแยกข้อความจากหน้าเอกสารในโหมด Raw ไลบรารีนี้มีเครื่องมือที่มีประสิทธิภาพในการแยกวิเคราะห์และแยกเนื้อหาจากรูปแบบไฟล์ต่างๆ ช่วยให้นักพัฒนาสามารถรวมการแยกข้อความในเอกสารเข้ากับแอปพลิเคชัน .NET ของตนได้
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และ .NET
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- เข้าถึง Groupdocs.Parser สำหรับไลบรารี .NET
- ไฟล์เอกสารตัวอย่างสำหรับการทดสอบ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: เริ่มต้น Parser
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์เอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสของคุณที่นี่
}
```
## ขั้นตอนที่ 2: ดึงข้อมูลเอกสาร
 รับข้อมูลเกี่ยวกับเอกสารโดยใช้`GetDocumentInfo()` วิธี.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## ขั้นตอนที่ 3: วนซ้ำหน้าต่างๆ และแยกข้อความ
วนซ้ำแต่ละหน้าของเอกสารและแยกเนื้อหาข้อความ
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // แยกข้อความออกจากหน้า
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## บทสรุป
ตอนนี้คุณได้เรียนรู้วิธีใช้ Groupdocs.Parser สำหรับ .NET เพื่อแยกข้อความจากหน้าเอกสารในโหมด Raw แล้ว นี่อาจเป็นคุณสมบัติที่มีประสิทธิภาพสำหรับแอปพลิเคชันที่ต้องการวิเคราะห์หรือประมวลผลเนื้อหาข้อความจากรูปแบบไฟล์ต่างๆ

## คำถามที่พบบ่อย
### Groupdocs.Parser สำหรับ .NET เข้ากันได้กับไฟล์ทุกรูปแบบหรือไม่
Groupdocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX, EPUB และอื่นๆ
### ฉันสามารถแยกข้อมูลเมตาพร้อมกับข้อความโดยใช้ไลบรารีนี้ได้หรือไม่
ใช่ Groupdocs.Parser ช่วยให้คุณสามารถแยกทั้งข้อความและข้อมูลเมตาจากเอกสารได้
### มีรุ่นทดลองให้ทดสอบหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ Groupdocs.Parser ได้อย่างไร
 สำหรับความช่วยเหลือทางเทคนิค โปรดไปที่[ฟอรัม Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).
### ฉันจะซื้อใบอนุญาตสำหรับ Groupdocs.Parser สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตได้[ที่นี่](https://purchase.groupdocs.com/buy).