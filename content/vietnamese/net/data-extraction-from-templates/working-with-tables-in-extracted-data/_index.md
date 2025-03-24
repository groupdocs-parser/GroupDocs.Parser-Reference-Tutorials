---
title: Làm việc với các bảng trong dữ liệu được trích xuất
linktitle: Làm việc với các bảng trong dữ liệu được trích xuất
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất dữ liệu bảng từ tài liệu bằng GroupDocs.Parser cho .NET. Phân tích cú pháp nội dung có cấu trúc một cách hiệu quả bằng các mẫu được xác định trước.
weight: 12
url: /vi/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất dữ liệu từ các bảng trong tài liệu. GroupDocs.Parser là một công cụ mạnh mẽ cho phép các nhà phát triển phân tích cú pháp và trích xuất văn bản, siêu dữ liệu và nội dung có cấu trúc từ nhiều định dạng tệp khác nhau như PDF, DOCX, XLSX, v.v. Cụ thể, chúng tôi sẽ tập trung vào việc trích xuất dữ liệu bảng một cách hiệu quả bằng cách sử dụng các mẫu được xác định trước.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có sẵn những điều sau:
- Visual Studio được cài đặt trên máy của bạn.
- Hiểu biết cơ bản về C# và .NET framework.
- Thư viện GroupDocs.Parser được cài đặt thông qua trình quản lý gói NuGet.

## Nhập không gian tên
Bắt đầu bằng cách nhập các không gian tên cần thiết để làm việc với GroupDocs.Parser và các chức năng liên quan.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Bước 1: Tạo mẫu bảng
Để trích xuất dữ liệu từ các bảng, trước tiên, hãy xác định một mẫu đại diện cho cấu trúc của bảng bạn muốn trích xuất. Chỉ định vị trí và kích thước của bảng trong tài liệu.
```csharp
// Xác định các tham số bảng (vị trí và kích thước)
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// Tạo mẫu bảng có tham số
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## Bước 2: Xác định mẫu
Tạo một mẫu bao gồm mẫu bảng bạn đã xác định. Mẫu này sẽ hướng dẫn trình phân tích cú pháp những gì cần tìm khi trích xuất dữ liệu bảng.
```csharp
// Tạo mẫu với bảng
Template template = new Template(new TemplateItem[] { table });
```
## Bước 3: Phân tích tài liệu và trích xuất dữ liệu bảng
Sử dụng lớp Parser từ GroupDocs.Parser để phân tích một tài liệu cụ thể bằng mẫu bạn đã xác định.
```csharp
// Chỉ định đường dẫn đến tệp mẫu của bạn
string filePath = "YourSampleFile.pdf";
// Tạo một thể hiện của lớp Parser
using (Parser parser = new Parser(filePath))
{
    // Phân tích tài liệu theo mẫu
    DocumentData data = parser.ParseByTemplate(template);
    // Lặp lại tất cả dữ liệu được trích xuất
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // Kiểm tra xem trường được trích xuất có phải là bảng không
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // Lặp lại các hàng của bảng
        for (int row = 0; row < area.RowCount; row++)
        {
            // Lặp lại các cột trong bảng
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // Lấy giá trị ô
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // In giá trị ô (hoặc chuỗi trống nếu null)
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // In khoảng cách tab giữa các cột
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            // Di chuyển đến dòng tiếp theo sau khi in từng hàng
            Console.WriteLine();
        }
    }
}
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất dữ liệu bảng từ tài liệu. Bằng cách xác định mẫu và sử dụng các phương pháp phân tích cú pháp, nhà phát triển có thể trích xuất dữ liệu có cấu trúc như bảng từ nhiều định dạng tệp khác nhau một cách hiệu quả.

## Câu hỏi thường gặp
### GroupDocs.Parser có tương thích với tất cả các định dạng tài liệu không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng tệp bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### Tôi có thể trích xuất dữ liệu từ các vùng cụ thể trong tài liệu không?
Hoàn toàn có thể, bạn có thể xác định các mẫu nhắm mục tiêu đến các khu vực cụ thể (như bảng) trong tài liệu để trích xuất.
### GroupDocs.Parser có phù hợp với các tài liệu lớn không?
Có, GroupDocs.Parser được tối ưu hóa để xử lý các tài liệu lớn một cách hiệu quả, cho phép các nhà phát triển trích xuất dữ liệu một cách liền mạch.
### GroupDocs.Parser có hỗ trợ trích xuất văn bản cùng với dữ liệu có cấu trúc không?
Có, ngoài việc trích xuất dữ liệu có cấu trúc (như bảng), GroupDocs.Parser có thể trích xuất văn bản thuần túy và siêu dữ liệu từ tài liệu.
### Làm cách nào tôi có thể nhận được hỗ trợ hoặc trợ giúp khi tích hợp GroupDocs.Parser?
 Để được hỗ trợ và thảo luận, hãy truy cập diễn đàn cộng đồng GroupDocs[đây](https://forum.groupdocs.com/c/parser/17).