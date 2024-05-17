---
title: ค้นหาข้อความในเอกสาร Word ด้วยนิพจน์ปกติ
linktitle: ค้นหาข้อความในเอกสาร Word ด้วยนิพจน์ปกติ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีค้นหาข้อความในเอกสาร Word โดยใช้นิพจน์ทั่วไปด้วย GroupDocs.Parser for .NET แยกเนื้อหาเฉพาะได้อย่างมีประสิทธิภาพ
type: docs
weight: 19
url: /th/net/word-document-processing/search-text-in-word-document-by-regular-expression/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากเอกสาร Word โดยใช้นิพจน์ทั่วไป คำแนะนำทีละขั้นตอนนี้จะช่วยคุณในการนำคุณลักษณะนี้ไปใช้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- เข้าถึงเอกสาร Word เพื่อการทดสอบ

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อใช้ GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: ดาวน์โหลดและติดตั้ง GroupDocs.Parser สำหรับ .NET
 ในการเริ่มต้น ให้ดาวน์โหลดและติดตั้ง GroupDocs.Parser สำหรับ .NET จาก[หน้าเผยแพร่](https://releases.groupdocs.com/parser/net/).
## ขั้นตอนที่ 2: การเข้าถึงข้อความด้วยนิพจน์ปกติ
ตอนนี้ เรามาดำเนินการแยกข้อความโดยใช้นิพจน์ทั่วไปกัน:
```csharp
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ค้นหาด้วยนิพจน์ทั่วไปพร้อมการจับคู่ตัวพิมพ์
    IEnumerable<SearchResult> searchResults = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
    
    // ทำซ้ำกับผลการค้นหา
    foreach (SearchResult result in searchResults)
    {
        //พิมพ์ดัชนีและข้อความที่พบ
        Console.WriteLine(string.Format("At {0}: {1}", result.Position, result.Text));
    }
}
```
## อธิบายขั้นตอน
1. ดาวน์โหลด GroupDocs.Parser: เริ่มต้นด้วยการดาวน์โหลดไลบรารี GroupDocs.Parser จากลิงก์ที่ให้มา และติดตั้งในโครงการของคุณ
2. นำเข้าเนมสเปซที่จำเป็น: นำเข้าเนมสเปซที่จำเป็น (`GroupDocs.Parser` และ`GroupDocs.Parser.Options`เพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs.Parser
3.  การเข้าถึงข้อความด้วยนิพจน์ทั่วไป: สร้าง`Parser` อินสแตนซ์ที่มีเส้นทางไฟล์ของเอกสาร Word ของคุณ ใช้`Search` วิธีการที่มีการแสดงออกปกติที่ระบุ (`"\\sthe\\s"`) และตัวเลือกการค้นหาเพื่อค้นหาข้อความที่ตรงกับรูปแบบ
4.  วนซ้ำผลการค้นหา: วนซ้ำผ่าน`SearchResult` คอลเลกชันเพื่อดึงและแสดงตำแหน่งและข้อความของการแข่งขันแต่ละรายการ

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการค้นหาข้อความภายในเอกสาร Word โดยใช้นิพจน์ทั่วไปด้วย GroupDocs.Parser สำหรับ .NET ไลบรารีนี้มีความสามารถในการแยกข้อความที่มีประสิทธิภาพ ช่วยให้นักพัฒนาทำงานกับเนื้อหาเอกสารได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารต่าง ๆ หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, XLSX, PPTX และอื่นๆ
### ฉันสามารถใช้ GroupDocs.Parser ในโครงการเชิงพาณิชย์ของฉันได้หรือไม่
 ใช่ GroupDocs.Parser เสนอใบอนุญาตเชิงพาณิชย์สำหรับนักพัฒนา คุณสามารถซื้อใบอนุญาตได้[ที่นี่](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser รองรับการแยกรูปภาพจากเอกสารหรือไม่
ใช่ GroupDocs.Parser อนุญาตให้แยกทั้งข้อความและรูปภาพจากรูปแบบเอกสารที่รองรับ
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Parser ได้ที่ไหน
 สำหรับความช่วยเหลือด้านเทคนิคและการสนทนา โปรดไปที่ฟอรัม GroupDocs.Parser[ที่นี่](https://forum.groupdocs.com/c/parser/17).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับการทดสอบได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวเพื่อการทดสอบได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).