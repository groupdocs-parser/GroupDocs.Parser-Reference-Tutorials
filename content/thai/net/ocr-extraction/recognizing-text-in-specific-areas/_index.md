---
title: การจดจำข้อความในพื้นที่เฉพาะ
linktitle: การจดจำข้อความในพื้นที่เฉพาะ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากพื้นที่เฉพาะในเอกสารที่มีความสามารถ OCR
type: docs
weight: 13
url: /th/net/ocr-extraction/recognizing-text-in-specific-areas/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อจดจำและแยกข้อความจากพื้นที่เฉพาะภายในเอกสาร GroupDocs.Parser เป็นไลบรารีการแยกวิเคราะห์เอกสารที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถทำงานกับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ โดยเฉพาะอย่างยิ่ง เราจะมุ่งเน้นไปที่การใช้ประโยชน์จากความสามารถ OCR (Optical Character Recognition) ของ GroupDocs.Parser เพื่อดึงข้อความจากพื้นที่ที่กำหนดภายในเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
1. Visual Studio IDE: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio บนเครื่องของคุณ
2.  GroupDocs.Parser for .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser for .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/parser/net/).
3. ตัวอย่างเอกสาร: เตรียมไฟล์ตัวอย่าง (เช่น PDF, DOCX) ที่คุณต้องการแยกข้อความ

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ:
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

มาแบ่งกระบวนการออกเป็นขั้นตอนโดยละเอียดโดยใช้ GroupDocs.Parser สำหรับ .NET:
## ขั้นตอนที่ 1: สร้างการตั้งค่า Parser ด้วย OCR Connector
 ขั้นแรก ให้สร้างอินสแตนซ์ของ`ParserSettings`คลาสและเริ่มต้นด้วยตัวเชื่อมต่อ OCR เช่น`AsposeOcrOnPremise`-
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## ขั้นตอนที่ 2: สร้างอินสแตนซ์ Parser ด้วยการตั้งค่า
 ถัดไป สร้างอินสแตนซ์ของ`Parser` คลาสโดยผ่านที่สร้างขึ้นก่อนหน้านี้`ParserSettings`-
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // ข้อมูลโค้ดดำเนินต่อไป...
}
```
 แทนที่`"YourSampleFile.pdf"` พร้อมเส้นทางไปยังเอกสารเป้าหมายของคุณ
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการแยกพื้นที่ข้อความ
 สร้างอินสแตนซ์ของ`PageTextAreaOptions` เพื่อเปิดใช้งานการแยกข้อความตาม OCR:
```csharp
PageTextAreaOptions options = new PageTextAreaOptions(true);
```
 ชุด`true` เพื่อเปิดใช้งาน OCR เพื่อการจดจำข้อความที่ดีขึ้น
## ขั้นตอนที่ 4: แยกพื้นที่ข้อความ
 วิงวอน`parser.GetTextAreas(options)` เพื่อแยกพื้นที่ข้อความออกจากเอกสาร:
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## ขั้นตอนที่ 5: ประมวลผลพื้นที่ข้อความที่แยกออกมา
วนซ้ำพื้นที่ข้อความที่แยกออกมาและดึงข้อมูลข้อความ ตำแหน่ง และขนาด:
```csharp
foreach (PageTextArea area in areas)
{
    Console.WriteLine(area.Text);
    Console.WriteLine($"\tPosition: ({area.Rectangle.Left}; {area.Rectangle.Top})");
    Console.WriteLine($"\tSize: ({area.Rectangle.Size.Width}; {area.Rectangle.Size.Height})");
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการแยกข้อความจากพื้นที่เฉพาะภายในเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ที่มีความสามารถ OCR เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถใช้ฟังก์ชันการแยกวิเคราะห์ของ GroupDocs.Parser ได้อย่างมีประสิทธิภาพเพื่อจัดการงานการแยกข้อความโดยทางโปรแกรม

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกข้อความจากเอกสารที่สแกนได้หรือไม่
ใช่ GroupDocs.Parser รองรับ OCR สำหรับการแยกข้อความจากรูปภาพที่สแกนภายในเอกสาร
### GroupDocs.Parser รองรับรูปแบบเอกสารใดบ้าง
GroupDocs.Parser รองรับรูปแบบที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX, TXT และอื่นๆ
### GroupDocs.Parser เหมาะสำหรับการประมวลผลเอกสารเป็นชุดหรือไม่
ใช่ GroupDocs.Parser สามารถจัดการงานการประมวลผลเป็นชุดสำหรับการแยกวิเคราะห์และแยกเอกสารได้อย่างมีประสิทธิภาพ
### ฉันสามารถปรับแต่งตัวเลือกการแยกข้อความด้วย GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser มีตัวเลือกมากมายในการปรับแต่งการแยกข้อความตามความต้องการเฉพาะ
### GroupDocs.Parser ให้การสนับสนุนในการแยกข้อมูลเมตาจากเอกสารหรือไม่
ใช่ GroupDocs.Parser อนุญาตให้แยกข้อมูลเมตา เช่น ผู้เขียน วันที่สร้าง และอื่นๆ จากรูปแบบเอกสารที่รองรับ