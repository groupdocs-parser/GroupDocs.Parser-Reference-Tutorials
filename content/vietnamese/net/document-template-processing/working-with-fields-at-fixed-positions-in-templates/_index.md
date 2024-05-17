---
title: Làm việc với các trường ở vị trí cố định trong mẫu
linktitle: Làm việc với các trường ở vị trí cố định trong mẫu
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất dữ liệu từ tài liệu bằng GroupDocs.Parser cho .NET. Hướng dẫn toàn diện với các ví dụ về mã.
type: docs
weight: 11
url: /vi/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách làm việc với các trường ở vị trí cố định trong các mẫu bằng GroupDocs.Parser cho .NET. GroupDocs.Parser là thư viện phân tích cú pháp tài liệu mạnh mẽ cho phép các nhà phát triển trích xuất dữ liệu từ nhiều định dạng tài liệu khác nhau như PDF, Word, Excel, v.v. Cụ thể, chúng tôi sẽ tập trung vào việc xác định và sử dụng các trường mẫu để trích xuất thông tin được nhắm mục tiêu dựa trên vị trí cố định của chúng.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Hiểu biết cơ bản về phát triển C# và .NET.
- Visual Studio được cài đặt trên hệ thống của bạn.
- Đã cài đặt thư viện GroupDocs.Parser cho .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/parser/net/).
- Các tập tin tài liệu mẫu để thử nghiệm.

## Nhập không gian tên
Bắt đầu bằng cách thêm các không gian tên cần thiết vào dự án C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Bước 1: Xác định trường mẫu
Đầu tiên, xác định trường có vị trí cố định trong mẫu. Trường này đại diện cho khu vực mà dữ liệu sẽ được trích xuất.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Đây:
- `Rectangle` xác định vị trí và kích thước của trường.
- `Point(35, 135)` đại diện cho tọa độ góc trên bên trái.
- `Size(100, 10)` xác định chiều rộng và chiều cao của trường.
- `"FromCompany"` là tên được gán cho trường này.
## Bước 2: Tạo mẫu
Xây dựng một mẫu bằng cách sử dụng trường được xác định.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 Các`Template` đối tượng chứa các trường được xác định.
## Bước 3: Phân tích tài liệu bằng mẫu
 Khởi tạo`Parser` class bằng đường dẫn tài liệu đích rồi phân tích cú pháp tài liệu bằng mẫu đã tạo.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Lặp lại thông qua dữ liệu được trích xuất
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Đây:
- `Parser` được khởi tạo với đường dẫn tệp tài liệu mẫu.
- `ParseByTemplate` phương pháp được sử dụng để trích xuất dữ liệu dựa trên mẫu được cung cấp.
-  Dữ liệu được trích xuất được truy cập bằng cách sử dụng`DocumentData`trong đó mỗi mục tương ứng với một trường được xác định.

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã đề cập đến quá trình làm việc với các trường ở vị trí cố định trong mẫu bằng GroupDocs.Parser cho .NET. Bằng cách xác định các mẫu với các vị trí trường cụ thể, nhà phát triển có thể trích xuất chính xác dữ liệu được nhắm mục tiêu từ các định dạng tài liệu khác nhau.

## Câu hỏi thường gặp
### GroupDocs.Parser có tương thích với tất cả các định dạng tài liệu không?
 GroupDocs.Parser hỗ trợ nhiều định dạng tệp, bao gồm PDF, Microsoft Word, Excel, PowerPoint, v.v. Tham khảo đến[tài liệu](https://reference.groupdocs.com/parser/net/) để biết danh sách chi tiết.
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Parser?
 Bạn có thể nhận được giấy phép tạm thời cho mục đích thử nghiệm từ[đây](https://purchase.groupdocs.com/temporary-license/).
### Tôi có thể tìm hỗ trợ cho GroupDocs.Parser ở đâu?
 Để được hỗ trợ kỹ thuật và thảo luận, hãy truy cập[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Tôi có thể dùng thử GroupDocs.Parser trước khi mua không?
 Có, bạn có thể khám phá thư viện với bản dùng thử miễn phí[đây](https://releases.groupdocs.com/).
### Làm cách nào để mua giấy phép cho GroupDocs.Parser?
 Để mua giấy phép, hãy truy cập[trang mua hàng](https://purchase.groupdocs.com/buy).