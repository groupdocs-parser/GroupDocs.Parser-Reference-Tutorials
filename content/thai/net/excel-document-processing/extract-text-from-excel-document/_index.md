---
title: แยกข้อความจากเอกสาร Excel
linktitle: แยกข้อความจากเอกสาร Excel
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสาร Excel โดยใช้ GroupDocs.Parser สำหรับ .NET ในขั้นตอนง่ายๆ
weight: 12
url: /th/net/excel-document-processing/extract-text-from-excel-document/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดกระบวนการแยกข้อความจากเอกสาร Excel โดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารี .NET ที่มีประสิทธิภาพ ซึ่งช่วยให้คุณสามารถแยกวิเคราะห์รูปแบบเอกสารต่างๆ รวมถึงไฟล์ Excel เพื่อแยกข้อความและข้อมูลเมตา
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการพัฒนาที่ตั้งค่าไว้สำหรับการพัฒนา .NET รวมถึง Visual Studio หรือ IDE ที่เข้ากันได้
2.  GroupDocs.Parser Library: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. ตัวอย่างเอกสาร Excel: เตรียมเอกสาร Excel ตัวอย่างที่คุณต้องการแยกข้อความ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโค้ด C# ของคุณเพื่อใช้ฟังก์ชัน GroupDocs.Parser
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ในการเริ่มต้น ให้สร้างอินสแตนซ์ของ`Parser`คลาสโดยระบุเส้นทางไปยังไฟล์ Excel ตัวอย่างของคุณ
```csharp
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // รหัสยังคงดำเนินต่อไป...
}
```
## ขั้นตอนที่ 2: แยกข้อความโดยใช้ TextReader
 ต่อไปให้ใช้`GetText()` วิธีการของ`Parser` คลาสเพื่อแยกข้อความจากเอกสาร Excel วิธีการนี้จะคืนค่า a`TextReader` วัตถุ.
```csharp
// แยกข้อความลงในเครื่องอ่าน
using (TextReader reader = parser.GetText())
{
    // รหัสยังคงดำเนินต่อไป...
}
```
## ขั้นตอนที่ 3: อ่านและพิมพ์ข้อความที่แยกออกมา
 ตอนนี้ใช้`ReadToEnd()` วิธีการของ`TextReader` วัตถุเพื่ออ่านข้อความที่แยกจากเอกสาร Excel และพิมพ์ไปยังคอนโซลหรือใช้ตามความจำเป็นในแอปพลิเคชันของคุณ
```csharp
// พิมพ์ข้อความที่แยกออกมา
Console.WriteLine(reader.ReadToEnd());
```

## บทสรุป
ในบทช่วยสอนนี้ คุณได้เรียนรู้วิธีแยกข้อความจากเอกสาร Excel โดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการทำตามขั้นตอนง่ายๆ เหล่านี้ คุณสามารถรวมความสามารถในการแยกข้อความในเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกข้อความจากรูปแบบเอกสารอื่นนอกเหนือจาก Excel ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, PowerPoint, PDF และอื่นๆ
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลด GroupDocs.Parser รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารสำหรับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถดูเอกสารประกอบโดยละเอียดสำหรับ GroupDocs.Parser[ที่นี่](https://tutorials.groupdocs.com/parser/net/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Parser ได้อย่างไร
สำหรับการสนับสนุนและความช่วยเหลือเกี่ยวกับ GroupDocs.Parser โปรดไปที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตสำหรับ GroupDocs.Parser ได้จาก[ที่นี่](https://purchase.groupdocs.com/buy).