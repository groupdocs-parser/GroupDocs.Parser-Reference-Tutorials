---
title: Trích xuất văn bản từ trang ở dạng PDF ở Chế độ thô
linktitle: Trích xuất văn bản từ trang ở dạng PDF ở Chế độ thô
second_title: API GroupDocs.Parser .NET
description: Trích xuất văn bản từ tệp PDF bằng GroupDocs.Parser trong C#. Tìm hiểu cách trích xuất văn bản PDF hiệu quả với thư viện .NET mạnh mẽ này.
type: docs
weight: 16
url: /vi/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ các trang trong tài liệu PDF bằng chế độ thô. GroupDocs.Parser là một công cụ mạnh mẽ cho phép các nhà phát triển làm việc với nhiều định dạng tài liệu khác nhau theo chương trình.
## Điều kiện tiên quyết
Trước khi bắt đầu hướng dẫn này, hãy đảm bảo bạn có những điều sau:
- Visual Studio được cài đặt trên máy của bạn.
- Kiến thức cơ bản về lập trình C#.
- GroupDocs.Parser cho thư viện .NET mà bạn có thể[tải xuống ở đây](https://releases.groupdocs.com/parser/net/).
- Một tệp PDF mẫu cho mục đích thử nghiệm.

## Nhập không gian tên
Trước tiên, hãy đảm bảo nhập các không gian tên cần thiết trong dự án C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Để bắt đầu, hãy khởi tạo`Parser`class bằng cách cung cấp đường dẫn đến tệp PDF mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã của bạn ở đây
}
```
## Bước 2: Nhận thông tin tài liệu và lặp lại các trang
Tiếp theo, lấy thông tin tài liệu và lặp lại từng trang để trích xuất văn bản.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Mã của bạn để trích xuất văn bản ở đây
}
```
## Bước 3: Trích xuất văn bản từ mỗi trang
 Trong vòng lặp, sử dụng`GetText` phương pháp trích xuất văn bản từ mỗi trang và in nó.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Phần kết luận
 Trong hướng dẫn này, chúng ta đã học cách trích xuất văn bản từ các trang PDF ở chế độ thô bằng GroupDocs.Parser cho .NET. Quá trình này bao gồm việc tạo ra một`Parser` chẳng hạn, lấy thông tin tài liệu, duyệt qua từng trang và trích xuất văn bản bằng cách sử dụng`GetText` phương pháp.

## Câu hỏi thường gặp
### GroupDocs.Parser cho .NET là gì?
GroupDocs.Parser cho .NET là API phân tích tài liệu cho phép các nhà phát triển trích xuất văn bản, siêu dữ liệu và thông tin khác từ các định dạng tệp khác nhau theo chương trình.
### Làm cách nào để tải xuống GroupDocs.Parser cho .NET?
 Bạn có thể tải xuống thư viện từ[Trang web GroupDocs](https://releases.groupdocs.com/parser/net/).
### Có bản dùng thử miễn phí không?
 Có, bạn có thể truy cập bản dùng thử miễn phí GroupDocs.Parser cho .NET từ[đây](https://releases.groupdocs.com/).
### Tôi có thể tìm hỗ trợ cho GroupDocs.Parser cho .NET ở đâu?
 Để được hỗ trợ kỹ thuật và hỗ trợ cộng đồng, hãy truy cập[diễn đàn GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Làm cách nào tôi có thể mua giấy phép GroupDocs.Parser cho .NET?
 Bạn có thể mua giấy phép từ[trang mua hàng](https://purchase.groupdocs.com/buy) hoặc có được giấy phép tạm thời[đây](https://purchase.groupdocs.com/temporary-license/).