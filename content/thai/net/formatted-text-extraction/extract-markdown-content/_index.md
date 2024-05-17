---
title: แยกเนื้อหา Markdown
linktitle: แยกเนื้อหา Markdown
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกเนื้อหา Markdown จากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET บทช่วยสอนนี้ให้คำแนะนำทีละขั้นตอนสำหรับการแยกข้อความอย่างราบรื่น
type: docs
weight: 13
url: /th/net/formatted-text-extraction/extract-markdown-content/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกเนื้อหา Markdown ออกจากเอกสาร GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกวิเคราะห์และแยกข้อความจากไฟล์รูปแบบต่างๆ ได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio บนระบบของคุณ
-  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ความเข้าใจพื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ยกตัวอย่าง`Parser` คลาสพร้อมพาธไปยังไฟล์ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสไปที่นี่...
}
```
## ขั้นตอนที่ 2: แยกข้อความที่จัดรูปแบบ Markdown
 ข้างใน`using`บล็อกใช้`GetFormattedText` วิธีการแยกข้อความที่จัดรูปแบบเป็น Markdown:
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Markdown)))
{
    // รหัสไปที่นี่...
}
```
## ขั้นตอนที่ 3: อ่านและส่งออกเนื้อหาที่แยกออกมา
 อ่านเนื้อหา Markdown ที่แยกมาจาก`TextReader`-
```csharp
string markdownContent = reader == null ? "Formatted text extraction isn't supported" : reader.ReadToEnd();
Console.WriteLine(markdownContent);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีแยกเนื้อหา Markdown จากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้กระบวนการแยกวิเคราะห์และแยกข้อความง่ายขึ้น ช่วยให้นักพัฒนาสามารถทำงานได้อย่างมีประสิทธิภาพกับรูปแบบไฟล์ต่างๆ
## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถจัดการไฟล์รูปแบบต่างๆ ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง DOCX, PDF, PPTX, XLSX และอื่นๆ
### GroupDocs.Parser เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Parser รองรับทั้ง .NET Framework และ .NET Core
### ฉันจะรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser ให้การสนับสนุนนักพัฒนาหรือไม่
 ใช่ คุณสามารถรับการสนับสนุนจากนักพัฒนาได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตได้[ที่นี่](https://purchase.groupdocs.com/buy).