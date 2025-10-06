---
title: Trích xuất văn bản từ các khu vực cụ thể bằng tùy chọn
linktitle: Trích xuất văn bản từ các khu vực cụ thể bằng tùy chọn
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất văn bản từ các vùng cụ thể trong tài liệu bằng GroupDocs.Parser cho .NET. Khám phá các tùy chọn trích xuất văn bản nâng cao với hướng dẫn này.
weight: 14
url: /vi/net/text-extraction/extract-text-from-specific-areas-with-options/
type: docs
---
# Trích xuất văn bản từ các khu vực cụ thể bằng tùy chọn

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ các vùng cụ thể trong tài liệu bằng các tùy chọn có thể tùy chỉnh. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển phân tích cú pháp và trích xuất văn bản từ nhiều định dạng tài liệu khác nhau một cách dễ dàng.
## Điều kiện tiên quyết
Trước khi chúng ta đi sâu vào mã hóa, hãy đảm bảo bạn có những điều sau:
1. Môi trường phát triển: Cài đặt Visual Studio hoặc bất kỳ IDE phát triển .NET nào khác.
2.  Thư viện GroupDocs.Parser: Tải xuống và cài đặt GroupDocs.Parser cho .NET từ[đây](https://releases.groupdocs.com/parser/net/).
3. Tệp mẫu: Chuẩn bị một tài liệu mẫu (ví dụ: PDF, DOCX, v.v.) để trích xuất văn bản từ đó.

## Nhập không gian tên
Trước tiên, bạn sẽ cần nhập các vùng tên cần thiết để truy cập các lớp và phương thức GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Khởi tạo một thể hiện của`Parser` class bằng cách cung cấp đường dẫn đến tệp mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã để trích xuất vùng văn bản sẽ ở đây
}
```
## Bước 2: Xác định các tùy chọn trích xuất vùng văn bản
 Tạo nên`PageTextAreaOptions` để chỉ định các tiêu chí để trích xuất văn bản.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
Trong ví dụ này:
- `"\\s[a-z]{2}\\s"` là mẫu biểu thức chính quy để khớp với các vùng văn bản chỉ chứa chữ cái viết thường.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` xác định hình chữ nhật (vị trí và kích thước) trên trang để trích xuất văn bản.
## Bước 3: Trích xuất vùng văn bản
Sử dụng các tùy chọn đã xác định để trích xuất các vùng văn bản đáp ứng tiêu chí đã chỉ định.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Bước 4: Kiểm tra và lặp lại các vùng văn bản được trích xuất
Kiểm tra xem việc trích xuất vùng văn bản có được hỗ trợ hay không rồi lặp lại các vùng được trích xuất.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã đề cập đến cách trích xuất văn bản từ các vùng cụ thể trong tài liệu bằng GroupDocs.Parser cho .NET. Thư viện này cung cấp các khả năng mở rộng để phân tích các định dạng tài liệu khác nhau, khiến nó trở thành một công cụ có giá trị cho các tác vụ trích xuất văn bản.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất văn bản từ các tài liệu được quét không?
Có, GroupDocs.Parser hỗ trợ trích xuất văn bản dựa trên OCR cho các tài liệu được quét.
### GroupDocs.Parser có tương thích với nhiều định dạng tài liệu không?
Có, nó có thể phân tích và trích xuất văn bản từ PDF, DOCX, XLSX, PPTX và các định dạng phổ biến khác.
### GroupDocs.Parser có hỗ trợ .NET Core không?
Có, GroupDocs.Parser tương thích với .NET Core cũng như .NET Framework.
### Tôi có thể trích xuất siêu dữ liệu cùng với văn bản bằng GroupDocs.Parser không?
Có, bạn có thể trích xuất cả nội dung văn bản và siêu dữ liệu từ tài liệu.
### Có phiên bản dùng thử cho GroupDocs.Parser không?
 Có, bạn có thể dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).