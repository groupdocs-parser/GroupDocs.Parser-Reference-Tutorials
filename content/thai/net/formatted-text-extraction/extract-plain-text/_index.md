---
title: แยกข้อความธรรมดา
linktitle: แยกข้อความธรรมดา
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความธรรมดาจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ขั้นตอนง่ายๆ สำหรับการรวมการแยกข้อความในแอปพลิเคชันของคุณ
weight: 14
url: /th/net/formatted-text-extraction/extract-plain-text/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการแยกข้อความธรรมดาจากรูปแบบเอกสารต่างๆ โดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาทำงานกับเอกสารได้อย่างราบรื่น แยกข้อความและข้อมูลเมตาได้อย่างมีประสิทธิภาพ คู่มือนี้จะอธิบายขั้นตอนที่จำเป็นในการผสานรวมและใช้ไลบรารีนี้ภายในแอปพลิเคชัน .NET ของคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio บนเครื่องพัฒนาของคุณ
2.  GroupDocs.Parser Library: ดาวน์โหลดและติดตั้ง GroupDocs.Parser สำหรับ .NET จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/parser/net/).
3. เอกสารตัวอย่าง: เตรียมเอกสารตัวอย่าง (เช่น DOCX, PDF, TXT) สำหรับการแยกข้อความ

## นำเข้าเนมสเปซ
ขั้นแรก รวมเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: เริ่มต้น Parser
 สร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังเอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    // รหัสสำหรับการแยกข้อความอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: แยกข้อความที่จัดรูปแบบ
 ภายใน`using` บล็อกของ`Parser`ให้แยกข้อความที่จัดรูปแบบโดยใช้ไฟล์`GetFormattedText` วิธีการด้วย`PlainText` โหมด.
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    // รหัสเพื่ออ่านและประมวลผลข้อความที่แยกออกมา
}
```
## ขั้นตอนที่ 3: อ่านข้อความที่แยกออกมา
 ใช้`TextReader` อินสแตนซ์เพื่ออ่านและส่งออกข้อความธรรมดาที่แยกออกมา
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงพื้นฐานของการแยกข้อความธรรมดาจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถรวมความสามารถในการแยกข้อความเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับเอกสารหลายรูปแบบหรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, TXT และอื่นๆ
### ฉันสามารถแยกข้อมูลเมตาพร้อมกับข้อความโดยใช้ GroupDocs.Parser ได้หรือไม่
แน่นอน GroupDocs.Parser อนุญาตให้แยกทั้งเนื้อหาข้อความและข้อมูลเมตา เช่น ผู้แต่ง วันที่สร้าง ฯลฯ
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง GroupDocs.Parser รุ่นทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Parser ได้ที่ไหน
 สำหรับความช่วยเหลือทางเทคนิค โปรดไปที่ GroupDocs.Parser[ฟอรั่ม](https://forum.groupdocs.com/c/parser/17).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 หากต้องการรับใบอนุญาตชั่วคราว โปรดไปที่ GroupDocs.Parser[หน้าใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).