---
title: Trích xuất văn bản được định dạng từ tài liệu
linktitle: Trích xuất văn bản được định dạng từ tài liệu
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất văn bản có định dạng từ tài liệu bằng GroupDocs.Parser cho .NET. Trích xuất văn bản đơn giản và hiệu quả cho các ứng dụng của bạn.
weight: 10
url: /vi/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản được định dạng từ nhiều loại tài liệu khác nhau. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển làm việc với các tài liệu một cách đơn giản và hiệu quả. Đến cuối hướng dẫn này, bạn sẽ có thể tích hợp liền mạch khả năng trích xuất văn bản vào các ứng dụng .NET của mình.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio trên hệ thống của mình.
-  GroupDocs.Parser cho .NET: Tải xuống và cài đặt thư viện GroupDocs.Parser từ[đây](https://releases.groupdocs.com/parser/net/).
- Mẫu tài liệu: Chuẩn bị tài liệu mẫu (ví dụ: PDF, DOCX) để trích xuất văn bản.
## Nhập không gian tên
Trước tiên, hãy bao gồm các không gian tên cần thiết trong mã C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Bắt đầu bằng cách khởi tạo một`Parser` object bằng đường dẫn đến tài liệu mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã trích xuất văn bản ở đây
}
```
 Thay thế`"YourSampleFile.pdf"` với đường dẫn đến tệp tài liệu của bạn.

## Bước 2: Trích xuất văn bản có định dạng
 Trong`using` chặn, sử dụng`GetFormattedText` phương pháp trích xuất văn bản được định dạng từ tài liệu. Chỉ định định dạng đầu ra mong muốn (ví dụ: HTML) bằng cách sử dụng`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Trích xuất văn bản đã định dạng vào đầu đọc
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Kiểm tra xem việc trích xuất có được hỗ trợ không
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Đọc và hiển thị văn bản được trích xuất
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Phần kết luận
Chúc mừng! Bạn đã học cách trích xuất văn bản có định dạng từ tài liệu bằng GroupDocs.Parser cho .NET. Thư viện đa năng này mở ra khả năng xử lý và phân tích văn bản trong ứng dụng của bạn.

## Câu hỏi thường gặp
### Câu hỏi: GroupDocs.Parser có thể trích xuất văn bản từ các tài liệu được bảo vệ bằng mật khẩu không?
Trả lời: Có, GroupDocs.Parser hỗ trợ trích xuất văn bản từ các tài liệu được bảo vệ bằng mật khẩu.
### Câu hỏi: GroupDocs.Parser hỗ trợ những định dạng tài liệu nào?
Đáp: GroupDocs.Parser hỗ trợ nhiều định dạng bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### Câu hỏi: Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Parser?
 Đáp: Bạn có thể xin giấy phép tạm thời từ[đây](https://purchase.groupdocs.com/temporary-license/).
### Câu hỏi: GroupDocs.Parser có hỗ trợ trích xuất hình ảnh từ tài liệu không?
Trả lời: Có, GroupDocs.Parser hỗ trợ trích xuất hình ảnh cùng với trích xuất văn bản.
### Câu hỏi: Tôi có thể tìm thêm hỗ trợ hoặc đặt câu hỏi về GroupDocs.Parser ở đâu?
 Đáp: Hãy ghé thăm[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)để được hỗ trợ và thảo luận.