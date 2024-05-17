---
title: การจัดการ OCR
linktitle: การจัดการ OCR
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีจัดการ OCR โดยใช้ GroupDocs.Parser สำหรับ .NET แยกข้อความจากรูปภาพและเอกสารที่สแกนได้อย่างมีประสิทธิภาพ
type: docs
weight: 11
url: /th/net/ocr-extraction/handling-ocr/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อจัดการงาน Optical Character Recognition (OCR) ได้อย่างมีประสิทธิภาพ ไลบรารีนี้มีเครื่องมืออันทรงพลังในการแยกข้อความจากเอกสาร และด้วย OCR คุณสามารถแยกข้อความจากรูปภาพหรือเอกสารที่สแกนได้ มาดำดิ่งสู่กระบวนการทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าดังต่อไปนี้:
- GroupDocs.Parser สำหรับ .NET Library: ดาวน์โหลดไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ไฟล์ตัวอย่างของคุณ: เตรียมไฟล์ตัวอย่าง (เอกสารหรือรูปภาพ) ที่คุณต้องการแยกข้อความ
- ความรู้พื้นฐานเกี่ยวกับสภาพแวดล้อม C# และ .NET

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อใช้ฟังก์ชัน GroupDocs.Parser ในแอปพลิเคชัน .NET ของคุณ
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างการตั้งค่า Parser ด้วย OCR Connector
 เริ่มต้น`ParserSettings` คลาสที่มีขั้วต่อ OCR ตัวอย่างเช่น การใช้ Aspose OCR ภายในองค์กร
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## ขั้นตอนที่ 2: กำหนดค่าตัวเลือก OCR
 ตั้งค่าอัน`OcrEventHandler` เพื่อจัดการคำเตือนระหว่างการประมวลผล OCR
```csharp
OcrEventHandler handler = new OcrEventHandler();
OcrOptions ocrOptions = new OcrOptions(handler);
```
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการแยกข้อความ
 สร้าง`TextOptions` เพื่อเปิดใช้งานการแยกข้อความตาม OCR
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## ขั้นตอนที่ 4: แยกข้อความโดยใช้ OCR
 ยกตัวอย่าง`Parser` คลาสด้วยการตั้งค่าและแยกข้อความโดยใช้ OCR
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    using (TextReader reader = parser.GetText(options))
    {
        if (reader == null)
        {
            Console.WriteLine("Text extraction isn't supported.");
        }
        else
        {
            Console.WriteLine(reader.ReadToEnd());
        }
    }
    if (handler.HasWarnings)
    {
        Console.WriteLine("The following warnings occurred during text recognition:");
        foreach (string w in handler.Warnings)
        {
            Console.WriteLine("\t* " + w);
        }
    }
    else
    {
        Console.WriteLine("Text recognition was performed without any warnings.");
    }
}
```

## บทสรุป
ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถใช้ประโยชน์จาก GroupDocs.Parser สำหรับ .NET เพื่อจัดการงาน OCR ภายในแอปพลิเคชันของคุณได้อย่างมีประสิทธิภาพ การแยกข้อความออกจากรูปภาพหรือเอกสารที่สแกนจะราบรื่นด้วยความสามารถอันทรงพลังที่นำเสนอโดยไลบรารีนี้

## คำถามที่พบบ่อย
### GroupDocs.Parser for .NET เข้ากันได้กับรูปแบบไฟล์ที่แตกต่างกันหรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, DOCX, PPTX, XLSX, รูปภาพ (JPEG, PNG, TIFF) และอื่นๆ
### ฉันสามารถใช้ GroupDocs.Parser สำหรับ .NET ในโครงการเชิงพาณิชย์ของฉันได้หรือไม่
ได้ คุณสามารถรวม GroupDocs.Parser สำหรับ .NET เข้ากับแอปพลิเคชันเชิงพาณิชย์ของคุณได้หลังจากซื้อใบอนุญาตแล้ว
### GroupDocs.Parser จัดการไฟล์ที่เข้ารหัสหรือป้องกันด้วยรหัสผ่านหรือไม่
GroupDocs.Parser สามารถแยกและแยกข้อความจากเอกสาร PDF ที่มีการป้องกันด้วยรหัสผ่าน
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Parser สำหรับ .NET หรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนหรือถามคำถามที่เกี่ยวข้องกับ GroupDocs.Parser for .NET ได้ที่ไหน
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับข้อสงสัยหรือการสนทนาการสนับสนุน