---
title: การรับรู้ข้อความ
linktitle: การรับรู้ข้อความ
second_title: GroupDocs.Parser .NET API
description: แยกข้อความจากเอกสารรูปแบบต่างๆ ได้อย่างมีประสิทธิภาพด้วย GroupDocs.Parser for .NET บูรณาการได้ง่ายและความสามารถ OCR อันทรงพลัง
type: docs
weight: 12
url: /th/net/ocr-extraction/recognizing-text/
---
## การแนะนำ
ในขอบเขตของการพัฒนา .NET การแยกข้อความที่มีประสิทธิภาพจากรูปแบบเอกสารต่างๆ เป็นสิ่งสำคัญยิ่ง GroupDocs.Parser for .NET มอบโซลูชันที่มีประสิทธิภาพในการแยกข้อความได้อย่างราบรื่น ในบทช่วยสอนนี้ เราจะเจาะลึกการใช้ GroupDocs.Parser ทีละขั้นตอนเพื่อจดจำและแยกข้อความจากเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกเรื่องการใช้ GroupDocs.Parser ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- การเข้าถึงอินเทอร์เน็ตเพื่อดาวน์โหลดแพ็คเกจและอ้างอิงเอกสาร

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นเพื่อใช้ประโยชน์จากฟังก์ชัน GroupDocs.Parser:
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
## ขั้นตอนที่ 1: ติดตั้ง GroupDocs.Parser
 ขั้นแรก ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser คุณสามารถรับมันได้จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/parser/net/).
## ขั้นตอนที่ 2: รับใบอนุญาตชั่วคราว
 หากต้องการใช้ GroupDocs.Parser ให้ขอรับใบอนุญาตชั่วคราวจาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
## ขั้นตอนที่ 3: การเริ่มต้น ParserSettings
 สร้างอินสแตนซ์ของ`ParserSettings`เพื่อกำหนดการตั้งค่าการแยกข้อความ รวมถึงตัวเชื่อมต่อ OCR หากจำเป็น
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## ขั้นตอนที่ 4: การใช้ Parser เพื่อแยกข้อความ
 ตอนนี้สร้างอินสแตนซ์ของ`Parser` คลาสที่มีการตั้งค่าที่กำหนดไว้
```csharp
using (Parser parser = new Parser("YourSampleFile.docx", settings))
{
    // กำหนดค่า TextOptions สำหรับการใช้งาน OCR
    TextOptions options = new TextOptions(false, true);
    // แยกข้อความโดยใช้ OCR
    using (TextReader reader = parser.GetText(options))
    {
        // แสดงข้อความที่แยกออกมาหรือข้อความ 'ไม่รองรับ'
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
ในตัวอย่างนี้:
-  แทนที่`"YourSampleFile.docx"` พร้อมเส้นทางไปยังเอกสารเป้าหมายของคุณ
- `TextOptions` ได้รับการกำหนดค่าให้เปิดใช้งาน OCR และเพิ่มประสิทธิภาพการแยกข้อความ

## บทสรุป
 ยินดีด้วย! คุณได้เรียนรู้วิธีรวม GroupDocs.Parser สำหรับ .NET เข้ากับโครงการของคุณเพื่อแยกข้อความอย่างมีประสิทธิภาพ สำรวจอย่างกว้างขวาง[เอกสารประกอบ](https://reference.groupdocs.com/parser/net/) สำหรับคุณสมบัติขั้นสูงและการเพิ่มประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser เหมาะสำหรับการแยกข้อความจากไฟล์ PDF หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกข้อความจากรูปแบบต่างๆ รวมถึง PDF
### ฉันสามารถรวม GroupDocs.Parser เข้ากับแอปพลิเคชัน ASP.NET ของฉันได้หรือไม่
GroupDocs.Parser สามารถรวมเข้ากับแอปพลิเคชัน ASP.NET ได้อย่างราบรื่น
### GroupDocs.Parser ต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์หรือไม่
ใช่ จำเป็นต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์ รับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser รองรับรูปแบบเอกสารใดบ้าง
GroupDocs.Parser รองรับรูปแบบที่หลากหลาย รวมถึง DOCX, PDF, XLSX และอื่นๆ
### ฉันจะขอความช่วยเหลือหรือถามคำถามที่เกี่ยวข้องกับ GroupDocs.Parser ได้อย่างไร
 เยี่ยมชม[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)สำหรับการสนับสนุนและการอภิปราย