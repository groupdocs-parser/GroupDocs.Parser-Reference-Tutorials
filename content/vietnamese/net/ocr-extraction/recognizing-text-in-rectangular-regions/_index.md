---
title: Nhận dạng văn bản trong vùng hình chữ nhật
linktitle: Nhận dạng văn bản trong vùng hình chữ nhật
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách nhận dạng văn bản ở các vùng tài liệu cụ thể bằng GroupDocs.Parser cho .NET có khả năng OCR.
weight: 14
url: /vi/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để nhận dạng văn bản trong các vùng tài liệu hình chữ nhật cụ thể. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển trích xuất văn bản, siêu dữ liệu, v.v. từ nhiều định dạng tệp khác nhau, bao gồm PDF, Word, Excel và PowerPoint.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã thiết lập sau:
-  GroupDocs.Parser for .NET: Tải xuống và cài đặt thư viện từ[đây](https://releases.groupdocs.com/parser/net/).
- Môi trường phát triển: Visual Studio hoặc bất kỳ .NET IDE nào khác.
- Tài liệu mẫu: Có tệp mẫu (ví dụ: PDF, DOCX) chứa văn bản cần nhận dạng.

## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết vào mã C# của mình:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Khởi tạo cài đặt trình phân tích cú pháp
 Bắt đầu bằng cách thiết lập`ParserSettings` với đầu nối OCR. Ở đây, chúng tôi sẽ sử dụng trình kết nối tại chỗ Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Bước 2: Tạo phiên bản trình phân tích cú pháp
 Tiếp theo, khởi tạo`Parser` lớp với các cài đặt được xác định trước đó:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Mã tiếp tục ở đây
}
```
 Thay thế`"YourSampleFile.pdf"` với đường dẫn đến tài liệu của bạn.
## Bước 3: Xác định hình chữ nhật OCR
 Xác định một hình chữ nhật trong tài liệu nơi nhận dạng văn bản sẽ được thực hiện. Ví dụ: một hình chữ nhật bắt đầu từ`(0, 0)` với chiều rộng`400` và chiều cao`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Bước 4: Định cấu hình tùy chọn nhận dạng văn bản
 Tạo nên`TextOptions` để chỉ định cách sử dụng OCR cùng với hình chữ nhật đã xác định:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Bước 5: Trích xuất văn bản bằng OCR
 Sử dụng`GetText` phương pháp của`Parser` ví dụ với cấu hình`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Đọc văn bản được trích xuất hoặc xử lý trường hợp 'không được hỗ trợ'
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã trình bày cách tận dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ các vùng hình chữ nhật cụ thể trong tài liệu bằng OCR. Quá trình này có thể được tùy chỉnh và tích hợp thêm vào các ứng dụng khác nhau để thực hiện các tác vụ trích xuất văn bản tự động.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất văn bản từ các tài liệu được quét không?
Có, GroupDocs.Parser hỗ trợ OCR (Nhận dạng ký tự quang học) để trích xuất văn bản từ tài liệu được quét.
### GroupDocs.Parser hỗ trợ những định dạng tệp nào?
GroupDocs.Parser hỗ trợ nhiều định dạng tệp, bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### Làm cách nào để xử lý các tài liệu không được hỗ trợ trích xuất văn bản?
 Bạn có thể kiểm tra xem việc trích xuất văn bản có được hỗ trợ hay không bằng cách sử dụng`TextReader` dụ được trả về bởi`parser.GetText(options)`.
### GroupDocs.Parser có phù hợp với các tác vụ trích xuất văn bản quy mô lớn không?
Có, GroupDocs.Parser được thiết kế để xử lý hiệu quả các tác vụ trích xuất văn bản quy mô lớn.
### Tôi có thể nhận hỗ trợ ở đâu cho các vấn đề liên quan đến GroupDocs.Parser?
 Để được hỗ trợ và thảo luận, hãy truy cập[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).