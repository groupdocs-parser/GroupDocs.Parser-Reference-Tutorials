---
title: แยกข้อความจากเอกสาร Excel เป็น HTML
linktitle: แยกข้อความจากเอกสาร Excel เป็น HTML
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสาร Excel และแปลงเป็น HTML โดยใช้ GroupDocs.Parser สำหรับ .NET
weight: 13
url: /th/net/excel-document-processing/extract-text-from-excel-document-as-html/
type: docs
---
# แยกข้อความจากเอกสาร Excel เป็น HTML

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากเอกสาร Excel และแปลงเป็นรูปแบบ HTML GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสารรูปแบบต่างๆ แยกข้อความและข้อมูลเมตาได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
-  ไลบรารี GroupDocs.Parser สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
## นำเข้าเนมสเปซ
เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณเพื่อเข้าถึงฟังก์ชัน GroupDocs.Parser
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ขั้นแรก ให้ยกตัวอย่าง`Parser` คลาสโดยระบุเส้นทางไปยังเอกสาร Excel ของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // รหัสเพิ่มเติมจะไปที่นี่
}
```
 แทนที่`"YourSampleFile.xlsx"` พร้อมเส้นทางไปยังไฟล์ Excel ของคุณ
## ขั้นตอนที่ 2: แยกข้อความเป็น HTML
 ภายใน`using` บล็อกของ`Parser` เช่น ใช้`GetFormattedText` วิธีการแยกข้อความที่จัดรูปแบบในโหมด HTML
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // รหัสเพิ่มเติมจะไปที่นี่
    }
}
```
## ขั้นตอนที่ 3: อ่านและพิมพ์ข้อความ HTML ที่แยกออกมา
 จากนั้น อ่านข้อความ HTML ที่แยกมาจากไฟล์`TextReader` และพิมพ์ไปที่คอนโซล
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
เมื่อดำเนินการแล้ว โค้ดนี้จะแยกข้อความจากเอกสาร Excel และแสดงเป็นรูปแบบ HTML ในคอนโซล
## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากเอกสาร Excel และแปลงเป็นรูปแบบ HTML ไลบรารีนี้มอบวิธีที่ตรงไปตรงมาในการทำงานกับรูปแบบเอกสารต่างๆ ช่วยให้นักพัฒนาสามารถจัดการงานการแยกข้อความในแอปพลิเคชันของตนได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก Excel ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, Word, PowerPoint และอื่นๆ
### GroupDocs.Parser เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Parser เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### GroupDocs.Parser รักษาการจัดรูปแบบในระหว่างการแยกข้อความหรือไม่
ได้ GroupDocs.Parser สามารถรักษาการจัดรูปแบบ เช่น แบบอักษร สไตล์ และเค้าโครงในระหว่างการแยกข้อความได้
### ฉันสามารถดึงข้อมูลเมตาจากเอกสารโดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser อนุญาตให้แยกข้อมูลเมตา เช่น ผู้เขียน วันที่สร้าง และอื่นๆ จากประเภทเอกสารที่รองรับ
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).