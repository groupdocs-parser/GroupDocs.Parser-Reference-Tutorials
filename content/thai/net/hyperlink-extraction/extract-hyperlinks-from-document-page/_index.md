---
title: แยกไฮเปอร์ลิงก์ออกจากหน้าเอกสาร
linktitle: แยกไฮเปอร์ลิงก์ออกจากหน้าเอกสาร
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกไฮเปอร์ลิงก์ออกจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET คำแนะนำทีละขั้นตอนสำหรับการแยกไฮเปอร์ลิงก์ใน C#
weight: 11
url: /th/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
type: docs
---
# แยกไฮเปอร์ลิงก์ออกจากหน้าเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกไฮเปอร์ลิงก์จากเอกสารทีละขั้นตอน GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถแยกวิเคราะห์รูปแบบเอกสารต่างๆ และแยกข้อความ เมตาดาต้า และองค์ประกอบอื่นๆ ได้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio บนเครื่องพัฒนาของคุณ
-  ไลบรารี GroupDocs.Parser: ดาวน์โหลดและอ้างอิงไลบรารี GroupDocs.Parser คุณสามารถรับได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- เอกสารตัวอย่าง: เตรียมเอกสารตัวอย่าง (เช่น DOCX, PDF) ที่มีไฮเปอร์ลิงก์สำหรับการทดสอบ

## นำเข้าเนมสเปซ
ขั้นแรก ให้รวมเนมสเปซที่จำเป็นเพื่อใช้ฟังก์ชัน GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ Parser
 ยกตัวอย่าง`Parser` คลาสพร้อมพาธไปยังเอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสไปที่นี่...
}
```
## ขั้นตอนที่ 2: ตรวจสอบการสนับสนุนการแยกไฮเปอร์ลิงก์
ตรวจสอบให้แน่ใจว่าเอกสารรองรับการแยกไฮเปอร์ลิงก์ก่อนดำเนินการต่อ
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## ขั้นตอนที่ 3: ดึงข้อมูลเอกสาร
รับข้อมูลพื้นฐานเกี่ยวกับเอกสารและตรวจสอบว่ามีหน้าหรือไม่
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## ขั้นตอนที่ 4: วนซ้ำหน้าเอกสาร
วนซ้ำแต่ละหน้าของเอกสาร
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // แยกไฮเปอร์ลิงก์ออกจากหน้าปัจจุบัน
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // วนซ้ำไฮเปอร์ลิงก์ที่แยกออกมา
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // บรรทัดว่างเพื่อให้อ่านง่าย
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงพื้นฐานของการใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกไฮเปอร์ลิงก์จากเอกสาร คุณได้เรียนรู้วิธีการเริ่มต้น parser ตรวจสอบการสนับสนุนไฮเปอร์ลิงก์ ดึงข้อมูลเอกสาร และวนซ้ำหน้าเอกสารเพื่อแยกไฮเปอร์ลิงก์อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ฉันสามารถแยกไฮเปอร์ลิงก์จากรูปแบบเอกสารที่แตกต่างกันได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบต่างๆ เช่น DOCX, PDF, PPTX ฯลฯ สำหรับการแยกไฮเปอร์ลิงก์
### GroupDocs.Parser ง่ายต่อการรวมเข้ากับแอปพลิเคชัน .NET ที่มีอยู่หรือไม่
GroupDocs.Parser ได้รับการออกแบบมาให้ตรงไปตรงมาและสามารถรวมเข้ากับโครงการ .NET ของคุณได้อย่างง่ายดาย
### ฉันสามารถแยกข้อมูลเมตาอื่น ๆ พร้อมกับไฮเปอร์ลิงก์โดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ นอกจากไฮเปอร์ลิงก์แล้ว คุณยังสามารถแยกข้อความ รูปภาพ และข้อมูลเมตาจากเอกสารโดยใช้ไลบรารีนี้ได้
### GroupDocs.Parser จัดการเอกสารที่เข้ารหัสหรือป้องกันด้วยรหัสผ่านหรือไม่
GroupDocs.Parser สามารถแยกวิเคราะห์เอกสารที่มีการป้องกันด้วยรหัสผ่านได้หากมีการระบุรหัสผ่าน
### มีเวอร์ชันทดลองให้ทดสอบก่อนซื้อหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).