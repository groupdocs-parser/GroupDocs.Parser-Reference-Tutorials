---
title: กำลังโหลดรูปแบบไฟล์เฉพาะ
linktitle: กำลังโหลดรูปแบบไฟล์เฉพาะ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากรูปแบบไฟล์ต่างๆ ใน .NET โดยใช้ GroupDocs.Parser บทช่วยสอนทีละขั้นตอนเพื่อการประมวลผลเอกสารอย่างมีประสิทธิภาพ
weight: 14
url: /th/net/document-loading/loading-specific-file-formats/
---
## การแนะนำ
ในโลกของการพัฒนา .NET การแยกวิเคราะห์และการแยกข้อความจากรูปแบบไฟล์ต่างๆ ถือเป็นข้อกำหนดทั่วไป GroupDocs.Parser สำหรับ .NET มีเครื่องมืออันทรงพลังเพื่อทำให้งานนี้ง่ายขึ้น บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับการใช้ GroupDocs.Parser เพื่อโหลดและแยกข้อความจากรูปแบบไฟล์เฉพาะทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการพัฒนา C# และ .NET
- ติดตั้ง Visual Studio หรือ IDE อื่นสำหรับการพัฒนา .NET แล้ว
-  GroupDocs.Parser สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ไฟล์ตัวอย่างในรูปแบบใดรูปแบบหนึ่งที่รองรับ (เช่น Word, PDF, Markdown)

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการเพิ่มเนมสเปซที่จำเป็นลงในไฟล์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```

ทำตามขั้นตอนเหล่านี้เพื่อโหลดและแยกข้อความจากรูปแบบไฟล์เฉพาะ:
## ขั้นตอนที่ 1: เปิดสตรีมไฟล์
ขั้นแรก ให้เปิดสตรีมไปยังไฟล์ตัวอย่างของคุณ:
```csharp
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // ดำเนินการขั้นตอนต่อไป
}
```
 แทนที่`"YourSampleFile.docx"` พร้อมเส้นทางไปยังไฟล์ตัวอย่างของคุณ
## ขั้นตอนที่ 2: สร้างอินสแตนซ์ Parser
 ยกตัวอย่าง`Parser` คลาสที่มีสตรีมที่เปิดอยู่และระบุรูปแบบไฟล์:
```csharp
using (Parser parser = new Parser(stream, new LoadOptions(FileFormat.Docx)))
{
    // ดำเนินการขั้นตอนต่อไป
}
```
 แทนที่`FileFormat.Docx` ด้วยการแจงนับรูปแบบไฟล์ที่เหมาะสมตามไฟล์ตัวอย่างของคุณ (เช่น`FileFormat.Pdf`, `FileFormat.Markup` สำหรับมาร์กดาวน์)
## ขั้นตอนที่ 3: ตรวจสอบการสนับสนุนการแยกข้อความ
ตรวจสอบว่ารองรับการแยกข้อความสำหรับรูปแบบไฟล์ที่โหลดหรือไม่:
```csharp
if (!parser.Features.Text)
{
    Console.WriteLine("Text extraction isn't supported.");
    return;
}
```
## ขั้นตอนที่ 4: แยกข้อความออกจากเอกสาร
 ใช้`parser.GetText()` ที่จะได้รับ`TextReader` ตัวอย่างและอ่านข้อความที่แยกออกมา:
```csharp
using (TextReader reader = parser.GetText())
{
    string extractedText = reader.ReadToEnd();
    Console.WriteLine(extractedText);
}
```

## บทสรุป
GroupDocs.Parser for .NET ช่วยให้การแยกข้อความจากไฟล์รูปแบบต่างๆ ง่ายขึ้น ช่วยให้สามารถประมวลผลเอกสารในแอปพลิเคชัน C# ได้อย่างมีประสิทธิภาพ เมื่อทำตามบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีโหลดรูปแบบไฟล์เฉพาะและแยกข้อความโดยใช้ GroupDocs.Parser

## คำถามที่พบบ่อย
### GroupDocs.Parser สำหรับ .NET ใช้งานได้ฟรีหรือไม่
GroupDocs.Parser สำหรับ .NET เสนอตัวเลือกใบอนุญาตทั้งแบบฟรีและแบบชำระเงิน คุณสามารถสำรวจพวกเขาได้[ที่นี่](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser for .NET รองรับไฟล์รูปแบบใดบ้าง
 GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง Word, PDF, Excel, PowerPoint, Markdown และอื่นๆ โปรดดูเอกสารประกอบ[ที่นี่](https://tutorials.groupdocs.com/parser/net/) สำหรับรายการทั้งหมด
### ฉันสามารถลองใช้ GroupDocs.Parser สำหรับ .NET ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนหรือถามคำถามเกี่ยวกับ GroupDocs.Parser for .NET ได้ที่ไหน
 เยี่ยมชมฟอรัม GroupDocs.Parser[ที่นี่](https://forum.groupdocs.com/c/parser/17) สำหรับข้อสงสัยหรือความต้องการการสนับสนุน
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser สำหรับ .NET ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).