---
title: แยกโครงสร้างข้อความ
linktitle: แยกโครงสร้างข้อความ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกโครงสร้างข้อความจากเอกสารรูปแบบต่างๆ โดยใช้ GroupDocs.Parser สำหรับ .NET บทช่วยสอนทีละขั้นตอนพร้อมตัวอย่างโค้ด
weight: 20
url: /th/net/text-extraction/extract-text-structure/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกโครงสร้างข้อความจากรูปแบบเอกสารต่างๆ GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกเนื้อหาข้อความที่มีโครงสร้างออกจากเอกสาร เช่น PDF, เอกสาร Word, ชีต Excel และอื่นๆ บทช่วยสอนนี้จะแนะนำคุณตลอดขั้นตอนการตั้งค่า GroupDocs.Parser การนำเข้าเนมสเปซที่จำเป็น และการแยกโครงสร้างข้อความทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ความเข้าใจพื้นฐานเกี่ยวกับการพัฒนา C# และ .NET
-  GroupDocs.Parser สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ไฟล์ตัวอย่างของคุณ (เช่น PDF, DOCX, XLSX) สำหรับการแยกข้อความ
## นำเข้าเนมสเปซ
หากต้องการเริ่มใช้ GroupDocs.Parser ในโปรเจ็กต์ C# ของคุณ ให้ทำตามขั้นตอนเหล่านี้เพื่อนำเข้าเนมสเปซที่จำเป็น:

ในไฟล์ C# ของคุณ ให้นำเข้าเนมสเปซที่จำเป็น:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Xml;
```
ตอนนี้เรามาดูการแยกโครงสร้างข้อความโดยใช้ GroupDocs.Parser กันดีกว่า ทำตามขั้นตอนเหล่านี้:
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ Parser
เริ่มต้นอินสแตนซ์ Parser ด้วยพาธไฟล์ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // ดำเนินการต่อด้วยขั้นตอนการสกัด...
}
```
## ขั้นตอนที่ 2: แยกโครงสร้างข้อความ
 ใช้`GetStructure()` วิธีการแยกโครงสร้างข้อความไปยังโปรแกรมอ่าน XML:
```csharp
using (XmlReader reader = parser.GetStructure())
{
    if (reader == null)
    {
        Console.WriteLine("Text structure extraction isn't supported.");
        return;
    }
    // อ่านและประมวลผลเอกสาร XML ต่อ...
}
```
## ขั้นตอนที่ 3: ประมวลผลโครงสร้างที่แยกออกมา
อ่านเอกสาร XML เพื่อค้นหาองค์ประกอบเฉพาะ เช่น ไฮเปอร์ลิงก์:
```csharp
while (reader.Read())
{
    if (reader.NodeType == XmlNodeType.Element && reader.IsStartElement() && reader.Name.ToLowerInvariant() == "hyperlink")
    {
        string value = reader.GetAttribute("link");
        if (value != null)
        {
            Console.WriteLine(value);
        }
    }
}
```
## บทสรุป
ในบทช่วยสอนนี้ คุณได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกโครงสร้างข้อความจากเอกสารอย่างมีประสิทธิภาพ ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถรวมความสามารถในการแยกข้อความเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### ฉันสามารถแยกข้อความจาก PDF ที่เข้ารหัสโดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกข้อความจาก PDF ที่เข้ารหัสตราบใดที่คุณให้ข้อมูลประจำตัวที่จำเป็น
### GroupDocs.Parser รองรับรูปแบบเอกสารใดบ้าง
GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ฉันจะรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser จัดการการแยกรูปภาพจากเอกสารหรือไม่
ใช่ GroupDocs.Parser สามารถแยกเนื้อหาทั้งข้อความและรูปภาพจากรูปแบบเอกสารที่รองรับ
### ฉันจะรับการสนับสนุนเพิ่มเติมหรือถามคำถามเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 เยี่ยมชม[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับการสนับสนุนและการอภิปรายในชุมชน