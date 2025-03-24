---
title: แยกข้อความที่จัดรูปแบบออกจากหน้าเอกสาร
linktitle: แยกข้อความที่จัดรูปแบบออกจากหน้าเอกสาร
second_title: GroupDocs.Parser .NET API
description: แยกข้อความที่จัดรูปแบบออกจากหน้าเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET โซลูชันการแยกข้อความที่มีประสิทธิภาพและเชื่อถือได้
weight: 11
url: /th/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดกระบวนการแยกข้อความที่จัดรูปแบบแล้วออกจากหน้าเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ไลบรารีนี้ช่วยให้คุณสามารถแยกวิเคราะห์และแยกข้อความจากรูปแบบเอกสารต่างๆ เช่น PDF, Word, Excel และอื่นๆ ได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
-  GroupDocs.Parser สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/parser/net/).

## นำเข้าเนมสเปซ
ขั้นแรก ให้เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 เริ่มต้นด้วยการสร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์ตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสจะไปที่นี่
}
```
## ขั้นตอนที่ 2: ตรวจสอบว่ารองรับการแยกข้อความที่จัดรูปแบบแล้วหรือไม่
ก่อนดำเนินการแยกข้อความ ให้ตรวจสอบว่าเอกสารรองรับการแยกข้อความที่จัดรูปแบบหรือไม่
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## ขั้นตอนที่ 3: รับข้อมูลเอกสาร
ดึงข้อมูลเกี่ยวกับเอกสาร เช่น จำนวนหน้า
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## ขั้นตอนที่ 4: วนซ้ำหน้าเอกสารและแยกข้อความที่จัดรูปแบบ
วนซ้ำแต่ละหน้าของเอกสารและแยกข้อความที่จัดรูปแบบโดยใช้ตัวเลือกที่ระบุ (เช่น รูปแบบ Markdown)
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## บทสรุป
ตอนนี้คุณรู้วิธีแยกข้อความที่จัดรูปแบบออกจากหน้าเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET แล้ว ไลบรารีนี้เป็นโซลูชันที่มีประสิทธิภาพและใช้งานง่ายสำหรับการแยกข้อความจากไฟล์รูปแบบต่างๆ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถจัดการไฟล์รูปแบบต่างๆ ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### GroupDocs.Parser เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Parser รองรับ .NET Core และ .NET Framework
### GroupDocs.Parser รักษาการจัดรูปแบบข้อความในระหว่างการแตกไฟล์หรือไม่
ได้ GroupDocs.Parser สามารถคงการจัดรูปแบบ เช่น สไตล์และแบบอักษรไว้ได้เมื่อแยกข้อความ
### ฉันสามารถแยกรูปภาพและข้อมูลเมตาโดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser อนุญาตให้แยกรูปภาพ ข้อมูลเมตา และข้อความจากเอกสาร
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถรับการสนับสนุนจาก[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).