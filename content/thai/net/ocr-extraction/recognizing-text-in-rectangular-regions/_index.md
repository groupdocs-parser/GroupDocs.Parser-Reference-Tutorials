---
title: การจดจำข้อความในพื้นที่สี่เหลี่ยม
linktitle: การจดจำข้อความในพื้นที่สี่เหลี่ยม
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีจดจำข้อความในพื้นที่เฉพาะของเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET พร้อมความสามารถ OCR
weight: 14
url: /th/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---

# การจดจำข้อความในพื้นที่สี่เหลี่ยม

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อจดจำข้อความภายในขอบเขตสี่เหลี่ยมเฉพาะของเอกสาร GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกข้อความ เมตาดาต้า และอื่นๆ จากไฟล์รูปแบบต่างๆ รวมถึง PDF, Word, Excel และ PowerPoint
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าต่อไปนี้:
-  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือ .NET IDE อื่น ๆ
- เอกสารตัวอย่าง: มีไฟล์ตัวอย่าง (เช่น PDF, DOCX) ที่มีข้อความที่จะจดจำ

## นำเข้าเนมสเปซ
ขั้นแรก คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโค้ด C# ของคุณ:
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
## ขั้นตอนที่ 1: เริ่มต้นการตั้งค่า Parser
 เริ่มต้นด้วยการตั้งค่า`ParserSettings` ด้วยขั้วต่อ OCR ที่นี่ เราจะใช้ตัวเชื่อมต่อ Aspose OCR ภายในองค์กร:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## ขั้นตอนที่ 2: สร้างอินสแตนซ์ Parser
 ถัดไป ยกตัวอย่าง`Parser` คลาสที่มีการตั้งค่าที่กำหนดไว้ก่อนหน้านี้:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // รหัสยังคงดำเนินต่อไปที่นี่
}
```
 แทนที่`"YourSampleFile.pdf"` พร้อมเส้นทางไปยังเอกสารของคุณ
## ขั้นตอนที่ 3: กำหนดสี่เหลี่ยมผืนผ้า OCR
 กำหนดสี่เหลี่ยมภายในเอกสารที่จะทำการจดจำข้อความ เช่น สี่เหลี่ยมเริ่มต้นที่`(0, 0)` มีความกว้าง`400` และความสูง`200`-
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## ขั้นตอนที่ 4: กำหนดค่าตัวเลือกการรู้จำข้อความ
 สร้าง`TextOptions` เพื่อระบุการใช้งาน OCR พร้อมกับสี่เหลี่ยมที่กำหนด:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## ขั้นตอนที่ 5: แยกข้อความโดยใช้ OCR
 ใช้`GetText` วิธีการของ`Parser` อินสแตนซ์ที่มีการกำหนดค่า`TextOptions`-
```csharp
using (TextReader reader = parser.GetText(options))
{
    // อ่านข้อความที่แยกออกมาหรือจัดการตัวพิมพ์ 'ไม่รองรับ'
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สาธิตวิธีใช้ประโยชน์จาก GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากขอบเขตสี่เหลี่ยมเฉพาะในเอกสารโดยใช้ OCR กระบวนการนี้สามารถปรับแต่งเพิ่มเติมและรวมเข้ากับแอปพลิเคชันต่างๆ สำหรับงานแยกข้อความอัตโนมัติ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกข้อความจากเอกสารที่สแกนได้หรือไม่
ใช่ GroupDocs.Parser รองรับ OCR (Optical Character Recognition) สำหรับการแยกข้อความจากเอกสารที่สแกน
### GroupDocs.Parser รองรับไฟล์รูปแบบใดบ้าง
GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ฉันจะจัดการเอกสารที่ไม่รองรับการแยกข้อความได้อย่างไร
 คุณสามารถตรวจสอบว่ารองรับการแยกข้อความหรือไม่`TextReader` ตัวอย่างที่ส่งคืนโดย`parser.GetText(options)`.
### GroupDocs.Parser เหมาะสำหรับงานแยกข้อความขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการออกแบบมาเพื่อจัดการงานแยกข้อความขนาดใหญ่ได้อย่างมีประสิทธิภาพ
### ฉันจะรับการสนับสนุนสำหรับปัญหาที่เกี่ยวข้องกับ GroupDocs.Parser ได้ที่ไหน
 สำหรับการสนับสนุนและการสนทนาโปรดไปที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).