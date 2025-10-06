---
title: แยกข้อความจากพื้นที่เฉพาะพร้อมตัวเลือก
linktitle: แยกข้อความจากพื้นที่เฉพาะพร้อมตัวเลือก
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากพื้นที่เฉพาะในเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET สำรวจตัวเลือกการแยกข้อความขั้นสูงด้วยบทช่วยสอนนี้
weight: 14
url: /th/net/text-extraction/extract-text-from-specific-areas-with-options/
type: docs
---
# แยกข้อความจากพื้นที่เฉพาะพร้อมตัวเลือก

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากพื้นที่เฉพาะภายในเอกสารโดยใช้ตัวเลือกที่ปรับแต่งได้ GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกวิเคราะห์และแยกข้อความจากเอกสารรูปแบบต่างๆ ได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกเรื่องการเขียนโค้ด ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือ IDE การพัฒนา .NET อื่น ๆ
2.  GroupDocs.Parser Library: ดาวน์โหลดและติดตั้ง GroupDocs.Parser สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. ไฟล์ตัวอย่าง: เตรียมเอกสารตัวอย่าง (เช่น PDF, DOCX ฯลฯ) เพื่อดึงข้อความออกมา

## นำเข้าเนมสเปซ
ขั้นแรก คุณจะต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการของ GroupDocs.Parser
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 เริ่มต้นอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์ตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสสำหรับการแยกพื้นที่ข้อความจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: กำหนดตัวเลือกการแยกพื้นที่ข้อความ
 สร้าง`PageTextAreaOptions` เพื่อระบุเกณฑ์ในการแยกข้อความ
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
ในตัวอย่างนี้:
- `"\\s[a-z]{2}\\s"` เป็นรูปแบบนิพจน์ทั่วไปเพื่อจับคู่พื้นที่ข้อความที่มีเฉพาะตัวอักษรพิมพ์เล็กเท่านั้น
- `new Rectangle(new Point(0, 0), new Size(300, 100))` กำหนดสี่เหลี่ยม (ตำแหน่งและขนาด) บนเพจที่จะแยกข้อความ
## ขั้นตอนที่ 3: แยกพื้นที่ข้อความ
ใช้ตัวเลือกที่กำหนดไว้เพื่อแยกพื้นที่ข้อความที่ตรงตามเกณฑ์ที่ระบุ
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## ขั้นตอนที่ 4: ตรวจสอบและวนซ้ำพื้นที่ข้อความที่แยกออกมา
ตรวจสอบว่ารองรับการแยกพื้นที่ข้อความหรือไม่ จากนั้นทำซ้ำในพื้นที่ที่แยกออกมา
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการแยกข้อความจากพื้นที่เฉพาะภายในเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ไลบรารีนี้มีความสามารถที่ครอบคลุมสำหรับการแยกวิเคราะห์รูปแบบเอกสารต่างๆ ทำให้เป็นเครื่องมือที่มีค่าสำหรับงานแยกข้อความ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกข้อความจากเอกสารที่สแกนได้หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกข้อความที่ใช้ OCR สำหรับเอกสารที่สแกน
### GroupDocs.Parser เข้ากันได้กับเอกสารหลายรูปแบบหรือไม่
ใช่ สามารถแยกวิเคราะห์และแยกข้อความจาก PDF, DOCX, XLSX, PPTX และรูปแบบยอดนิยมอื่นๆ ได้
### GroupDocs.Parser ให้การสนับสนุน .NET Core หรือไม่
ใช่ GroupDocs.Parser เข้ากันได้กับ .NET Core และ .NET Framework
### ฉันสามารถแยกข้อมูลเมตาพร้อมกับข้อความโดยใช้ GroupDocs.Parser ได้หรือไม่
ได้ คุณสามารถแยกทั้งเนื้อหาที่เป็นข้อความและข้อมูลเมตาจากเอกสารได้
### มีรุ่นทดลองใช้งานสำหรับ GroupDocs.Parser หรือไม่
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).