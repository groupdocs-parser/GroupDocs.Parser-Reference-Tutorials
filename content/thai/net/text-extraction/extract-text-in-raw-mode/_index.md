---
title: แยกข้อความในโหมด Raw
linktitle: แยกข้อความในโหมด Raw
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET การแยกข้อความที่ง่าย มีประสิทธิภาพ และราบรื่นภายในแอปพลิเคชัน .NET ของคุณ
weight: 19
url: /th/net/text-extraction/extract-text-in-raw-mode/
---

# แยกข้อความในโหมด Raw

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากรูปแบบเอกสารต่างๆ ได้อย่างมีประสิทธิภาพ GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถดึงข้อความและข้อมูลเมตาจากเอกสาร เช่น PDF, Word, Excel, PowerPoint และอื่นๆ อีกมากมาย ช่วยให้งานแยกข้อความภายในแอปพลิเคชัน .NET ง่ายขึ้น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET อื่น ๆ ที่ติดตั้งบนเครื่องของคุณ
- ความรู้พื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
- เข้าถึง GroupDocs.Parser สำหรับไลบรารี .NET

## นำเข้าเนมสเปซ
ขั้นแรก ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นสำหรับ GroupDocs.Parser ในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: เริ่มต้น GroupDocs.Parser
 หากต้องการเริ่มต้นการแยกข้อความ ให้สร้างอินสแตนซ์ของ`Parser`คลาสผ่านเส้นทางไปยังเอกสารตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile"))
{
    // ดำเนินการแยกข้อความต่อที่นี่
}
```
## ขั้นตอนที่ 2: แยกข้อความดิบ
 ภายใน`using` บล็อกให้ใช้`GetText` วิธีการด้วย`TextOptions` เพื่อแยกข้อความดิบออกจากเอกสาร:
```csharp
using (TextReader reader = parser.GetText(new TextOptions(true)))
{
    // อ่านข้อความจากเอกสารต่อไป
}
```
## ขั้นตอนที่ 3: อ่านข้อความจากเอกสาร
 ตอนนี้ใช้`TextReader` วัตถุเพื่ออ่านข้อความที่แยกออกมาจากเอกสาร:
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## บทสรุป
ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถแยกข้อความดิบจากเอกสารโดยใช้ GroupDocs.Parser for .NET ได้อย่างมีประสิทธิภาพ บทช่วยสอนนี้ให้คำแนะนำพื้นฐานในการใช้ประโยชน์จากไลบรารีนี้ภายในแอปพลิเคชัน .NET ของคุณเพื่อการแยกข้อความที่ราบรื่น

## คำถามที่พบบ่อย
### GroupDocs.Parser รองรับไฟล์รูปแบบใดบ้าง
GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, Microsoft Word, Excel, PowerPoint และอื่นๆ
### ฉันสามารถแยกข้อมูลเมตาพร้อมกับข้อความโดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser อนุญาตให้แยกทั้งข้อความและข้อมูลเมตาจากรูปแบบเอกสารที่รองรับ
### GroupDocs.Parser เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Parser เข้ากันได้กับ .NET Core พร้อมกับ .NET Framework แบบดั้งเดิม
### GroupDocs.Parser จัดการเอกสารที่มีการป้องกันด้วยรหัสผ่านหรือไม่
ใช่ GroupDocs.Parser สามารถประมวลผลเอกสารที่มีการป้องกันด้วยรหัสผ่านได้หากระบุรหัสผ่านที่ถูกต้อง
### ฉันสามารถรวม GroupDocs.Parser เข้ากับเว็บแอปพลิเคชันของฉันได้หรือไม่
แน่นอนว่า GroupDocs.Parser สามารถรวมเข้ากับเว็บแอปพลิเคชันที่พัฒนาโดยใช้เทคโนโลยี .NET ได้อย่างราบรื่น