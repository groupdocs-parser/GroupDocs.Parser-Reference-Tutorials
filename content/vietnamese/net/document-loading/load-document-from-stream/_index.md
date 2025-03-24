---
title: Tải tài liệu từ luồng
linktitle: Tải tài liệu từ luồng
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất văn bản từ các định dạng tài liệu khác nhau trong .NET bằng GroupDocs.Parser. Hướng dẫn từng bước với các ví dụ về mã.
weight: 12
url: /vi/net/document-loading/load-document-from-stream/
---
## Giới thiệu
Trong lĩnh vực xử lý tài liệu trong các ứng dụng .NET, việc trích xuất văn bản từ các định dạng tệp khác nhau là một yêu cầu chung. GroupDocs.Parser cho .NET cung cấp một giải pháp mạnh mẽ để phân tích cú pháp và trích xuất văn bản từ nhiều loại tài liệu khác nhau một cách liền mạch. Hướng dẫn này sẽ hướng dẫn bạn qua quy trình sử dụng GroupDocs.Parser để trích xuất văn bản từ tài liệu theo từng bước.
## Điều kiện tiên quyết
Trước khi bắt đầu sử dụng GroupDocs.Parser cho .NET, hãy đảm bảo bạn đã thiết lập sau:
- Môi trường phát triển: Visual Studio hoặc bất kỳ môi trường phát triển .NET nào khác.
-  Gói GroupDocs.Parser cho .NET: Tải xuống và cài đặt thư viện GroupDocs.Parser cho .NET từ[đây](https://releases.groupdocs.com/parser/net/).
- Mẫu tài liệu: Chuẩn bị sẵn tài liệu mẫu để trích xuất văn bản.
## Nhập không gian tên
Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án .NET của bạn để truy cập các chức năng GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Các bước sau đây trình bày cách trích xuất văn bản từ tài liệu bằng GroupDocs.Parser từ một luồng.
## Bước 1: Tải tài liệu từ luồng
```csharp
// Tạo luồng
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Tạo một thể hiện của lớp Parser với luồng
    using (Parser parser = new Parser(stream))
    {
        // Trích xuất văn bản vào đầu đọc
        using (TextReader reader = parser.GetText())
        {
            // In văn bản từ tài liệu
            // Nếu trích xuất văn bản không được hỗ trợ, trình đọc sẽ không có giá trị
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
Trong ví dụ này:
- Chúng tôi mở một luồng tệp cho tệp tài liệu (`YourSampleFile.docx`).
-  Khởi tạo một`Parser` ví dụ với luồng.
-  Sử dụng`parser.GetText()` để lấy một`TextReader` chứa văn bản được trích xuất.
- In văn bản hoặc tin nhắn được trích xuất nếu định dạng tài liệu không hỗ trợ trích xuất văn bản.
## Phần kết luận
GroupDocs.Parser dành cho .NET đơn giản hóa việc trích xuất văn bản từ các định dạng tài liệu khác nhau, cho phép các nhà phát triển xử lý và sử dụng hiệu quả nội dung văn bản trong ứng dụng của họ. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tích hợp liền mạch khả năng trích xuất văn bản tài liệu vào các dự án .NET của mình.

## Câu hỏi thường gặp
### Những định dạng tài liệu nào được GroupDocs.Parser hỗ trợ cho .NET?
GroupDocs.Parser hỗ trợ nhiều định dạng tài liệu bao gồm DOCX, PDF, XLSX, PPTX, EPUB, v.v.
### GroupDocs.Parser có thể trích xuất hình ảnh hoặc siêu dữ liệu từ tài liệu không?
Có, GroupDocs.Parser có thể trích xuất hình ảnh, siêu dữ liệu và văn bản từ nhiều loại tài liệu khác nhau.
### GroupDocs.Parser có tương thích với các ứng dụng .NET Core không?
Có, GroupDocs.Parser tương thích với cả ứng dụng .NET Framework và .NET Core.
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Parser?
 Bạn có thể xin giấy phép tạm thời từ[đây](https://purchase.groupdocs.com/temporary-license/).
### Tôi có thể tìm thêm hỗ trợ hoặc tài liệu cho GroupDocs.Parser ở đâu?
 Để được hỗ trợ thêm, hãy truy cập[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) hoặc tham khảo[tài liệu](https://tutorials.groupdocs.com/parser/net/).
