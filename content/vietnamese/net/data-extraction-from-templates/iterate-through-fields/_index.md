---
title: Lặp lại qua các trường
linktitle: Lặp lại qua các trường
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất dữ liệu có cấu trúc từ tài liệu bằng GroupDocs.Parser cho .NET. Nâng cao các ứng dụng .NET của bạn với khả năng trích xuất dữ liệu tài liệu.
weight: 11
url: /vi/net/data-extraction-from-templates/iterate-through-fields/
type: docs
---
# Lặp lại qua các trường

## Giới thiệu
GroupDocs.Parser cho .NET là một thư viện mạnh mẽ cho phép các nhà phát triển trích xuất dữ liệu từ nhiều định dạng tài liệu khác nhau như PDF, Microsoft Word, Excel và PowerPoint. Hướng dẫn này sẽ hướng dẫn bạn trong quá trình sử dụng GroupDocs.Parser để lặp qua các trường tài liệu và trích xuất dữ liệu cụ thể bằng cách sử dụng các mẫu. Đến cuối hướng dẫn này, bạn sẽ có thể trích xuất dữ liệu có cấu trúc từ các tài liệu trong ứng dụng .NET của mình một cách hiệu quả.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã thiết lập các điều kiện tiên quyết sau:
- Kiến thức cơ bản về lập trình C#.
- Visual Studio được cài đặt trên máy của bạn.
- Thư viện GroupDocs.Parser cho .NET được cài đặt và tham chiếu trong dự án của bạn.

## Nhập không gian tên
Để bắt đầu, hãy thêm các vùng tên cần thiết vào tệp C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Hãy chia nhỏ quy trình thành các hướng dẫn từng bước.
## Bước 1: Xác định trường mẫu
Đầu tiên, xác định các trường bạn muốn trích xuất từ tài liệu bằng cách sử dụng biểu thức thông thường.
```csharp
// Xác định trường "giá"
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Xác định trường "email"
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Tạo mẫu với các trường được xác định
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
Trong bước này, chúng tôi đã xác định hai trường: một trường để trích xuất giá (được xác định bằng ký hiệu đô la và chữ số) và một trường khác để trích xuất địa chỉ email.
## Bước 2: Phân tích tài liệu
 Tiếp theo, sử dụng`Parser` lớp để phân tích tài liệu bằng cách sử dụng mẫu đã xác định.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Phân tích tài liệu theo mẫu
    DocumentData data = parser.ParseByTemplate(template);
    // Lặp lại thông qua dữ liệu được trích xuất
    for (int i = 0; i < data.Count; i++)
    {
        // Tên trường in
        Console.Write(data[i].Name + ": ");
        // Kiểm tra xem vùng được trích xuất có phải là văn bản không
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Ở đây, chúng ta khởi tạo`Parser` bằng đường dẫn đến tài liệu mẫu của bạn và sau đó phân tích cú pháp tài liệu bằng mẫu đã xác định. Sau đó, chúng tôi lặp qua dữ liệu được trích xuất và in tên trường cùng với văn bản được trích xuất.
## Phần kết luận
Trong hướng dẫn này, chúng ta đã khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất dữ liệu cụ thể từ các tài liệu bằng cách sử dụng các mẫu. Bằng cách tận dụng các biểu thức và mẫu thông thường, bạn có thể trích xuất thông tin có cấu trúc từ các định dạng tài liệu khác nhau một cách hiệu quả. Thử nghiệm với các mẫu và loại tài liệu khác nhau để phù hợp với nhu cầu trích xuất cụ thể của bạn.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất dữ liệu từ các tài liệu được quét không?
Có, GroupDocs.Parser có thể trích xuất văn bản và siêu dữ liệu từ cả tài liệu PDF được quét và có thể tìm kiếm.
### GroupDocs.Parser có tương thích với các ứng dụng .NET Core không?
Có, GroupDocs.Parser hỗ trợ .NET Core cùng với .NET Framework.
### GroupDocs.Parser hỗ trợ những định dạng tài liệu nào?
GroupDocs.Parser hỗ trợ nhiều định dạng bao gồm PDF, Microsoft Word, Excel, PowerPoint, v.v.
### Làm cách nào tôi có thể xử lý các tài liệu lớn bằng GroupDocs.Parser?
GroupDocs.Parser cung cấp các tùy chọn để trích xuất dữ liệu từ các trang hoặc phần cụ thể của tài liệu lớn, đảm bảo xử lý hiệu quả.
### Tôi có thể sử dụng GroupDocs.Parser chỉ để trích xuất văn bản không?
Có, bạn có thể trích xuất nội dung văn bản thuần túy từ tài liệu bằng GroupDocs.Parser mà không cần định dạng phức tạp.