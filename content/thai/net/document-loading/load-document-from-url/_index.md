---
title: โหลดเอกสารจาก URL
linktitle: โหลดเอกสารจาก URL
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET บทช่วยสอนนี้ครอบคลุมถึงการโหลดเอกสารจาก URL และการแยกข้อความทีละขั้นตอน
weight: 13
url: /th/net/document-loading/load-document-from-url/
---

# โหลดเอกสารจาก URL

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากเอกสาร GroupDocs.Parser เป็นเครื่องมืออันทรงพลังสำหรับการแยกข้อความ ข้อมูลเมตา และข้อมูลอื่น ๆ จากรูปแบบเอกสารต่าง ๆ เช่น PDF, Word, Excel และอื่น ๆ เราจะกล่าวถึงกระบวนการโหลดเอกสารจาก URL และแยกเนื้อหาข้อความทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio บนระบบของคุณ
2.  GroupDocs.Parser for .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser for .NET จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/parser/net/).
3. ความเข้าใจพื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นในโค้ด C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

ขั้นแรก เราจะสาธิตวิธีการโหลดเอกสารจาก URL และแยกเนื้อหาข้อความออกจากนั้น
## ขั้นตอนที่ 1: ระบุ URL ของเอกสาร
ระบุ URL ของเอกสารที่คุณต้องการแยกข้อความจาก:
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## ขั้นตอนที่ 2: สร้างอินสแตนซ์ Parser
 ยกตัวอย่าง`Parser` คลาสที่มี URL เอกสาร:
```csharp
using (Parser parser = new Parser(uri))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: แยกข้อความออกจากเอกสาร
 ข้างใน`using`บล็อกใช้`parser.GetText()` เพื่อแยกข้อความออกจากเอกสาร:
```csharp
using (TextReader reader = parser.GetText())
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 4: แสดงข้อความที่แยกออกมา
อ่านและพิมพ์ข้อความที่แยกออกมาจากเอกสาร:
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงพื้นฐานของการแยกข้อความจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมความสามารถในการแยกข้อความเอกสารเข้ากับแอปพลิเคชัน C# ของคุณได้อย่างง่ายดาย

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารต่าง ๆ หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ
### ฉันสามารถแยกข้อมูลเมตาพร้อมกับข้อความโดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser ช่วยให้คุณสามารถแยกข้อมูลเมตา ข้อความ และข้อมูลอื่นๆ ออกจากเอกสารได้
### มีรุ่นทดลองใช้งานสำหรับ GroupDocs.Parser หรือไม่
 ใช่ คุณสามารถรับ GroupDocs.Parser เวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารสำหรับ GroupDocs.Parser ได้ที่ไหน
 มีเอกสารประกอบโดยละเอียดสำหรับ GroupDocs.Parser[ที่นี่](https://tutorials.groupdocs.com/parser/net/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Parser ได้อย่างไร
คุณสามารถขอการสนับสนุนด้านเทคนิคและถามคำถามได้ในฟอรัม GroupDocs.Parser[ที่นี่](https://forum.groupdocs.com/c/parser/17).