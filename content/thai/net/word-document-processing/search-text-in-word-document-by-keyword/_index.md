---
title: ค้นหาข้อความในเอกสาร Word ด้วยคำสำคัญ
linktitle: ค้นหาข้อความในเอกสาร Word ด้วยคำสำคัญ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีค้นหาข้อความในเอกสาร Word โดยใช้ GroupDocs.Parser for .NET แยกคำหลักที่เฉพาะเจาะจงอย่างมีประสิทธิภาพ
weight: 18
url: /th/net/word-document-processing/search-text-in-word-document-by-keyword/
type: docs
---
# ค้นหาข้อความในเอกสาร Word ด้วยคำสำคัญ

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความเฉพาะภายในเอกสาร Word โดยใช้ C# GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกข้อความและข้อมูลเมตาจากเอกสารรูปแบบต่างๆ รวมถึงเอกสาร Word
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือ IDE อื่นที่เข้ากันได้
2.  ไลบรารี GroupDocs.Parser: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser สำหรับ .NET จาก[เว็บไซต์](https://releases.groupdocs.com/parser/net/).
3. ตัวอย่างเอกสาร Word: เตรียมเอกสาร Word ตัวอย่างเพื่อใช้สำหรับการค้นหาข้อความ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยส่งเส้นทางไปยังเอกสาร Word ตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสไปที่นี่
}
```
## ขั้นตอนที่ 2: ค้นหาคำสำคัญ
 ต่อไปให้ใช้`Search` วิธีการของ`Parser` คลาสเพื่อค้นหาคำสำคัญเฉพาะภายในเอกสาร
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 แทนที่`"keyword"` ด้วยข้อความที่คุณต้องการค้นหาภายในเอกสาร
## ขั้นตอนที่ 3: ทำซ้ำผลการค้นหา
 วนซ้ำผลการค้นหาโดยใช้`foreach` วนซ้ำเพื่อเข้าถึงแต่ละรายการ`SearchResult` วัตถุ.
```csharp
foreach (SearchResult result in searchResults)
{
    //รหัสสำหรับจัดการผลการค้นหาแต่ละรายการ
}
```
## ขั้นตอนที่ 4: เข้าถึงรายละเอียดผลการค้นหา
 ภายในลูป คุณสามารถเข้าถึงตำแหน่งและข้อความของผลการค้นหาแต่ละรายการได้โดยใช้`Position` และ`Text` คุณสมบัติของ`SearchResult` วัตถุ.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
ข้อมูลโค้ดนี้จะพิมพ์ดัชนี (`Position`) และข้อความที่พบ (`Text`) สำหรับผลการค้นหาแต่ละรายการไปยังคอนโซล

## บทสรุป
ในบทช่วยสอนนี้ คุณได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความเฉพาะภายในเอกสาร Word ไลบรารีนี้มอบวิธีที่สะดวกในการแยกและจัดการเนื้อหาจากรูปแบบเอกสารต่างๆ โดยทางโปรแกรม

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก Word ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### GroupDocs.Parser เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Parser เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอใบอนุญาตชั่วคราวได้จาก[หน้าการซื้อ GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะรับการสนับสนุนเพิ่มเติมหรือถามคำถามเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 เยี่ยมชม[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับการสนับสนุนและการอภิปรายของชุมชน
### ฉันสามารถทดลองใช้ GroupDocs.Parser ฟรีก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[หน้าเผยแพร่ GroupDocs](https://releases.groupdocs.com/).