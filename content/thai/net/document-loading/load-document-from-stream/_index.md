---
title: โหลดเอกสารจากสตรีม
linktitle: โหลดเอกสารจากสตรีม
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสารรูปแบบต่างๆ ใน .NET โดยใช้ GroupDocs.Parser คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด
weight: 12
url: /th/net/document-loading/load-document-from-stream/
---
## การแนะนำ
ในขอบเขตของการประมวลผลเอกสารในแอปพลิเคชัน .NET การแยกข้อความจากรูปแบบไฟล์ต่างๆ ถือเป็นข้อกำหนดทั่วไป GroupDocs.Parser สำหรับ .NET นำเสนอโซลูชั่นอันทรงพลังในการแยกวิเคราะห์และแยกข้อความจากเอกสารที่หลากหลายได้อย่างราบรื่น บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการใช้ GroupDocs.Parser เพื่อแยกข้อความจากเอกสารทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มใช้ GroupDocs.Parser สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าต่อไปนี้:
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET อื่น ๆ
-  แพ็คเกจ GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ตัวอย่างเอกสาร: เตรียมเอกสารตัวอย่างให้พร้อมสำหรับการแยกข้อความ
## การนำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ .NET ของคุณเพื่อเข้าถึงฟังก์ชัน GroupDocs.Parser
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

ขั้นตอนต่อไปนี้สาธิตวิธีการแยกข้อความจากเอกสารโดยใช้ GroupDocs.Parser จากสตรีม
## ขั้นตอนที่ 1: โหลดเอกสารจากสตรีม
```csharp
// สร้างกระแส
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // สร้างอินสแตนซ์ของคลาส Parser ด้วยสตรีม
    using (Parser parser = new Parser(stream))
    {
        // แยกข้อความเข้าสู่เครื่องอ่าน
        using (TextReader reader = parser.GetText())
        {
            // พิมพ์ข้อความจากเอกสาร
            // หากไม่รองรับการแยกข้อความ โปรแกรมอ่านจะเป็นโมฆะ
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
ในตัวอย่างนี้:
- เราเปิดสตรีมไฟล์สำหรับไฟล์เอกสาร (`YourSampleFile.docx`-
-  เริ่มต้นก`Parser` อินสแตนซ์กับสตรีม
-  ใช้`parser.GetText()` เพื่อดึงข้อมูล`TextReader` มีข้อความที่แยกออกมา
- พิมพ์ข้อความที่แยกออกมาหรือข้อความ หากรูปแบบเอกสารไม่รองรับการแยกข้อความ
## บทสรุป
GroupDocs.Parser สำหรับ .NET ช่วยให้การแยกข้อความจากรูปแบบเอกสารต่างๆ ง่ายขึ้น ช่วยให้นักพัฒนาสามารถประมวลผลและใช้เนื้อหาที่เป็นข้อความภายในแอปพลิเคชันของตนได้อย่างมีประสิทธิภาพ ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมความสามารถในการแยกข้อความเอกสารเข้ากับโปรเจ็กต์ .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### GroupDocs.Parser for .NET รองรับรูปแบบเอกสารใดบ้าง
GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, XLSX, PPTX, EPUB และอื่นๆ
### GroupDocs.Parser สามารถแยกรูปภาพหรือข้อมูลเมตาจากเอกสารได้หรือไม่
ใช่ GroupDocs.Parser สามารถดึงรูปภาพ ข้อมูลเมตา และข้อความจากเอกสารประเภทต่างๆ ได้
### GroupDocs.Parser เข้ากันได้กับแอปพลิเคชัน .NET Core หรือไม่
ใช่ GroupDocs.Parser เข้ากันได้กับทั้งแอปพลิเคชัน .NET Framework และ .NET Core
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะหาการสนับสนุนหรือเอกสารเพิ่มเติมสำหรับ GroupDocs.Parser ได้ที่ไหน
 สำหรับการสนับสนุนเพิ่มเติม โปรดไปที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) หรืออ้างถึง[เอกสารประกอบ](https://tutorials.groupdocs.com/parser/net/).
