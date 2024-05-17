---
title: แยกข้อความจากเอกสาร Word เป็น HTML
linktitle: แยกข้อความจากเอกสาร Word เป็น HTML
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากเอกสาร Word และบันทึกเป็น HTML บทช่วยสอนทีละขั้นตอนพร้อมตัวอย่างโค้ด
type: docs
weight: 16
url: /th/net/word-document-processing/extract-text-from-word-document-as-html/
---
## การแนะนำ
GroupDocs.Parser for .NET เป็นไลบรารีการแยกวิเคราะห์เอกสารที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถแยกข้อความและเมตาดาต้าจากไฟล์รูปแบบต่างๆ ได้อย่างราบรื่น ในบทช่วยสอนนี้ เราจะเน้นไปที่การใช้ประโยชน์จาก GroupDocs.Parser เพื่อแยกข้อความจากเอกสาร Word และบันทึกเป็น HTML กระบวนการนี้จำเป็นสำหรับงานต่างๆ เช่น การวิเคราะห์เนื้อหา การทำดัชนี หรือการแปลงเอกสารเป็นรูปแบบที่เหมาะกับเว็บ ในตอนท้ายของคู่มือนี้ คุณจะมีความเข้าใจที่ชัดเจนเกี่ยวกับวิธีการใช้ GroupDocs.Parser อย่างมีประสิทธิภาพในแอปพลิเคชัน .NET ของคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนเครื่องพัฒนาของคุณ
-  GroupDocs.Parser สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- เข้าถึงตัวอย่างเอกสาร Word เพื่อการทดสอบ
## นำเข้าเนมสเปซ
ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
ทำตามขั้นตอนโดยละเอียดเหล่านี้เพื่อแยกข้อความจากเอกสาร Word และบันทึกเป็น HTML โดยใช้ GroupDocs.Parser สำหรับ .NET:
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังเอกสาร Word ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // ดำเนินการต่อไปยังขั้นตอนที่ 2...
}
```
 แทนที่`"YourSampleFile.docx"`พร้อมเส้นทางไปยังเอกสาร Word ของคุณ
## ขั้นตอนที่ 2: แยกข้อความที่จัดรูปแบบเป็น HTML
 ต่อไปให้ใช้`GetFormattedText` วิธีการไปด้วย`FormattedTextOptions`เพื่อแยกข้อความในรูปแบบ HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // แยกข้อความที่จัดรูปแบบลงในเครื่องอ่าน
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // ดำเนินการต่อไปยังขั้นตอนที่ 3...
    }
}
```
## ขั้นตอนที่ 3: อ่านและส่งออก HTML ที่แยกออกมา
 สุดท้าย อ่านเนื้อหา HTML ที่แยกออกมาจากไฟล์`TextReader` และพิมพ์ไปที่คอนโซล:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // แยกข้อความที่จัดรูปแบบลงในเครื่องอ่าน
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // พิมพ์ข้อความที่จัดรูปแบบเป็น HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากเอกสาร Word และบันทึกเป็น HTML ไลบรารีนี้นำเสนอวิธีที่ตรงไปตรงมาและมีประสิทธิภาพในการแยกวิเคราะห์เนื้อหาเอกสาร ทำให้เป็นเครื่องมืออันล้ำค่าสำหรับงานการประมวลผลเอกสารในแอปพลิเคชัน .NET

## คำถามที่พบบ่อย
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะหาเอกสารเพิ่มเติมสำหรับ GroupDocs.Parser ได้ที่ไหน
 มีเอกสารรายละเอียดให้[ที่นี่](https://reference.groupdocs.com/parser/net/).
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Parser ได้อย่างไร
 เยี่ยมชมฟอรั่มการสนับสนุน[ที่นี่](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser รองรับเอกสารประเภทใดบ้าง
GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, PDF, Excel, PowerPoint และอื่นๆ