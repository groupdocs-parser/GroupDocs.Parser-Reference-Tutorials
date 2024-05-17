---
title: Tải tài liệu từ đĩa cục bộ
linktitle: Tải tài liệu từ đĩa cục bộ
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất văn bản từ các định dạng tài liệu khác nhau bằng GroupDocs.Parser cho .NET. Trích xuất văn bản dễ dàng và hiệu quả với C#.
type: docs
weight: 11
url: /vi/net/document-loading/load-document-from-local-disk/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ tài liệu. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển phân tích cú pháp các định dạng tài liệu khác nhau và trích xuất nội dung văn bản theo chương trình. Chúng tôi sẽ đề cập đến các bước cần thiết để bắt đầu trích xuất văn bản bằng thư viện này.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã cài đặt các điều kiện tiên quyết sau:
- Visual Studio được cài đặt trên hệ thống của bạn.
- Kiến thức cơ bản về ngôn ngữ lập trình C#.
-  Đã cài đặt thư viện GroupDocs.Parser cho .NET (tải xuống[đây](https://releases.groupdocs.com/parser/net/)).

## Nhập không gian tên
Trước tiên, bạn cần nhập các không gian tên cần thiết vào dự án C# của mình:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Bước 1: Tải tài liệu từ đĩa cục bộ
 Bắt đầu bằng cách tải tài liệu từ đĩa cục bộ của bạn. Thay thế`"Your Sample File"` với đường dẫn đến tài liệu đích của bạn.
```csharp
// Đặt đường dẫn tệp
string filePath = "Your Sample File";
// Tạo một thể hiện của lớp Parser với filePath
using (Parser parser = new Parser(filePath))
{
    // Trích xuất văn bản vào đầu đọc
    using (TextReader reader = parser.GetText())
    {
        //In văn bản được trích xuất từ tài liệu
        // Nếu trích xuất văn bản không được hỗ trợ, trình đọc sẽ không có giá trị
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Giải thích các bước
1. Đặt đường dẫn tệp: Bắt đầu bằng cách chỉ định đường dẫn đến tài liệu bạn muốn trích xuất văn bản từ (`filePath` Biến đổi).
2.  Tạo phiên bản trình phân tích cú pháp: Khởi tạo`Parser` lớp học bằng cách vượt qua`filePath`.
3.  Trích xuất văn bản: Sử dụng`GetText()` phương pháp của`Parser` ví dụ để có được một`TextReader` đối tượng chứa văn bản được trích xuất từ tài liệu.
4.  Đọc văn bản đã trích: Sử dụng`ReadToEnd()` phương pháp của`TextReader` để lấy toàn bộ nội dung văn bản được trích xuất từ tài liệu.
5.  Xử lý các định dạng không được hỗ trợ: Nếu định dạng tài liệu không hỗ trợ trích xuất văn bản,`reader` đối tượng sẽ là`null`và bạn có thể xử lý tình huống này một cách phù hợp.

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã trình bày các bước ban đầu để trích xuất văn bản từ tài liệu bằng GroupDocs.Parser cho .NET. Thư viện này cung cấp các tính năng mở rộng để phân tích cú pháp tài liệu, cho phép các nhà phát triển làm việc hiệu quả với nhiều định dạng tệp khác nhau trong ứng dụng của họ.

## Câu hỏi thường gặp
### GroupDocs.Parser có tương thích với tất cả các định dạng tài liệu không?
GroupDocs.Parser hỗ trợ nhiều định dạng bao gồm PDF, tài liệu Microsoft Office (Word, Excel, PowerPoint), v.v.
### Tôi có thể trích xuất siêu dữ liệu cùng với văn bản bằng GroupDocs.Parser không?
Có, GroupDocs.Parser cho phép trích xuất cả nội dung văn bản và siêu dữ liệu từ các định dạng tài liệu được hỗ trợ.
### Tôi có thể tìm thêm tài nguyên và hỗ trợ cho GroupDocs.Parser ở đâu?
 Tham quan[Tài liệu GroupDocs.Parser](https://reference.groupdocs.com/parser/net/) để tham khảo API chi tiết và khám phá[Diễn đàn GroupDocs](https://forum.groupdocs.com/c/parser/17) để hỗ trợ cộng đồng.
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Parser?
 Bạn có thể yêu cầu một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) cho mục đích đánh giá và thử nghiệm.
### Có bản dùng thử miễn phí cho GroupDocs.Parser không?
 Có, bạn có thể tải xuống một[dùng thử miễn phí](https://releases.groupdocs.com/) phiên bản GroupDocs.Parser.