---
title: ค้นหาข้อความด้วยคำสำคัญ
linktitle: ค้นหาข้อความด้วยคำสำคัญ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีค้นหาข้อความด้วยคำสำคัญในเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET แยกเนื้อหาที่เกี่ยวข้องอย่างมีประสิทธิภาพได้อย่างง่ายดาย
weight: 21
url: /th/net/text-extraction/search-text-by-keyword/
---

# ค้นหาข้อความด้วยคำสำคัญ

## การแนะนำ
ในบทช่วยสอนนี้ เราจะเจาะลึกเกี่ยวกับการใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความด้วยคำหลักภายในเอกสาร GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถดึงข้อความ ข้อมูลเมตา และข้อมูลอื่น ๆ จากรูปแบบไฟล์ต่างๆ เช่น PDF เอกสาร Microsoft Office และอื่นๆ การค้นหาคำสำคัญเฉพาะภายในเอกสารเหล่านี้อาจจำเป็นสำหรับแอปพลิเคชันที่เกี่ยวข้องกับข้อมูลข้อความจำนวนมาก
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ .NET IDE ที่ต้องการ
2.  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดไลบรารี่จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. การเข้าถึงไฟล์ตัวอย่าง: เตรียมไฟล์ตัวอย่าง (เช่น PDF, DOCX) เพื่อทดสอบฟังก์ชันการค้นหาคำหลัก

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องรวมเนมสเปซที่จำเป็นในโครงการของคุณ
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์คลาส Parser
 เริ่มต้นด้วยการสร้างอินสแตนซ์ของ`Parser` และระบุเส้นทางไปยังไฟล์ตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // ค้นหาคำสำคัญ
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // ทำซ้ำกับผลการค้นหา
    foreach (SearchResult result in searchResults)
    {
        //พิมพ์ดัชนีและข้อความที่พบ
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## ขั้นตอนที่ 2: ค้นหาคำสำคัญ
 ภายใน`using` บล็อค โทร`Search` วิธีการบน`parser` วัตถุผ่านคำหลักที่ต้องการเป็นอาร์กิวเมนต์
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 แทนที่`"test"` ด้วยคำสำคัญที่คุณต้องการค้นหาภายในเอกสาร
## ขั้นตอนที่ 3: วนซ้ำผลการค้นหา
 จากนั้น ทำซ้ำผลการค้นหาที่ได้รับจาก`Search` วิธีการใช้ก`foreach` วนซ้ำ
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 แต่ละ`SearchResult` วัตถุ`result` คุณสามารถเข้าถึงมันได้`Position` (ดัชนี) และ`Text` (ข้อความที่พบ)

## บทสรุป
 ในบทช่วยสอนนี้ เราได้สำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความด้วยคำหลักภายในเอกสารได้อย่างง่ายดาย การใช้ประโยชน์จาก`Search` วิธีการของ`Parser` คลาสช่วยให้สามารถดึงตัวอย่างข้อความที่เกี่ยวข้องได้อย่างมีประสิทธิภาพโดยอิงจากคำค้นหาเฉพาะ

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารต่าง ๆ หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ฉันสามารถดำเนินการแยกข้อความขั้นสูงโดยใช้ GroupDocs.Parser ได้หรือไม่
อย่างแน่นอน! นอกเหนือจากการค้นหาข้อความแล้ว GroupDocs.Parser ยังเปิดใช้งานการแยกข้อมูลเมตา การแยกข้อความที่มีโครงสร้าง และอื่นๆ อีกมากมาย
### ฉันจะหาเอกสารโดยละเอียดสำหรับ GroupDocs.Parser ได้ที่ไหน
สำรวจเอกสารฉบับสมบูรณ์[ที่นี่](https://tutorials.groupdocs.com/parser/net/).
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือเกี่ยวกับคำถามที่เกี่ยวข้องกับ GroupDocs.Parser ได้อย่างไร
 เยี่ยมชมฟอรัม GroupDocs เพื่อรับการสนับสนุนและการสนทนา[ที่นี่](https://forum.groupdocs.com/c/parser/17).
### มีเวอร์ชันทดลองใช้งานเพื่อประเมิน GroupDocs.Parser ก่อนซื้อหรือไม่
 ใช่ คุณสามารถเข้าถึงการทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).