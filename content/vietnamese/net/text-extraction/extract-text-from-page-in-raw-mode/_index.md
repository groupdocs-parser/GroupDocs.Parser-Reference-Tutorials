---
title: Trích xuất văn bản từ trang ở chế độ thô
linktitle: Trích xuất văn bản từ trang ở chế độ thô
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất văn bản hiệu quả từ các trang tài liệu bằng Groupdocs.Parser cho .NET trong hướng dẫn toàn diện này.
weight: 17
url: /vi/net/text-extraction/extract-text-from-page-in-raw-mode/
---

# Trích xuất văn bản từ trang ở chế độ thô

## Giới thiệu
Trong hướng dẫn này, bạn sẽ tìm hiểu cách sử dụng Groupdocs.Parser cho .NET để trích xuất văn bản từ các trang tài liệu ở chế độ thô. Thư viện này cung cấp các công cụ hiệu quả để phân tích và trích xuất nội dung từ các định dạng tệp khác nhau, cho phép các nhà phát triển kết hợp trích xuất văn bản tài liệu vào các ứng dụng .NET của họ.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
- Kiến thức cơ bản về lập trình C# và .NET
- Visual Studio được cài đặt trên máy của bạn
- Truy cập vào Groupdocs.Parser cho thư viện .NET
- Tệp tài liệu mẫu để thử nghiệm

## Nhập không gian tên
Bắt đầu bằng cách thêm các không gian tên cần thiết vào dự án C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Khởi tạo trình phân tích cú pháp
 Đầu tiên, tạo một thể hiện của`Parser` class bằng cách cung cấp đường dẫn đến tệp tài liệu mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã của bạn ở đây
}
```
## Bước 2: Truy xuất thông tin tài liệu
 Truy xuất thông tin về tài liệu bằng cách sử dụng`GetDocumentInfo()` phương pháp.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Bước 3: Lặp lại các trang và trích xuất văn bản
Lặp lại qua từng trang của tài liệu và trích xuất nội dung văn bản.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Trích xuất văn bản từ trang
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Phần kết luận
Bây giờ bạn đã học cách sử dụng Groupdocs.Parser cho .NET để trích xuất văn bản từ các trang tài liệu ở chế độ thô. Đây có thể là một tính năng mạnh mẽ dành cho các ứng dụng cần phân tích hoặc xử lý nội dung văn bản từ nhiều định dạng tệp khác nhau.

## Câu hỏi thường gặp
### Groupdocs.Parser cho .NET có tương thích với tất cả các định dạng tệp không?
Groupdocs.Parser hỗ trợ nhiều định dạng tệp bao gồm PDF, DOCX, XLSX, PPTX, EPUB, v.v.
### Tôi có thể trích xuất siêu dữ liệu cùng với văn bản bằng thư viện này không?
Có, Groupdocs.Parser cho phép bạn trích xuất cả văn bản và siêu dữ liệu từ tài liệu.
### Có phiên bản dùng thử để thử nghiệm không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ kỹ thuật cho Groupdocs.Parser?
 Để được hỗ trợ kỹ thuật, hãy truy cập[Diễn đàn Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Tôi có thể mua giấy phép Groupdocs.Parser cho .NET ở đâu?
 Bạn có thể mua giấy phép[đây](https://purchase.groupdocs.com/buy).