---
title: Trích xuất hình ảnh từ tài liệu
linktitle: Trích xuất hình ảnh từ tài liệu
second_title: API GroupDocs.Parser .NET
description: Trích xuất hình ảnh từ tài liệu một cách dễ dàng bằng GroupDocs.Parser cho .NET. Khả năng xử lý tài liệu của bạn và hợp lý hóa các tác vụ trích xuất hình ảnh một cách hiệu quả.
weight: 11
url: /vi/net/image-extraction/extract-images-from-document/
type: docs
---
# Trích xuất hình ảnh từ tài liệu

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách trích xuất hình ảnh từ tài liệu bằng GroupDocs.Parser cho .NET. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển trích xuất văn bản, siêu dữ liệu, hình ảnh, v.v. từ nhiều định dạng tài liệu khác nhau.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn đã thiết lập các điều kiện tiên quyết sau:
- Visual Studio: Cài đặt Visual Studio trên máy của bạn.
-  GroupDocs.Parser cho .NET: Tải xuống và cài đặt GroupDocs.Parser từ[trang tải xuống](https://releases.groupdocs.com/parser/net/).
- Tài liệu mẫu: Chuẩn bị một tài liệu mẫu (PDF, DOCX, v.v.) mà bạn muốn trích xuất hình ảnh.

## Nhập không gian tên
Bắt đầu bằng cách nhập các vùng tên cần thiết trong dự án C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Đầu tiên, tạo một thể hiện của`Parser` class bằng cách cung cấp đường dẫn đến tài liệu mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã của bạn ở đây
}
```
 Thay thế`"YourSampleFile.pdf"` với đường dẫn đến tệp tài liệu của bạn.
## Bước 2: Trích xuất hình ảnh từ tài liệu
 Tiếp theo, trích xuất hình ảnh từ tài liệu bằng cách sử dụng`GetImages()` phương pháp.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 Các`GetImages()` phương thức trả về một tập hợp`PageImageArea` các đối tượng đại diện cho hình ảnh được tìm thấy trong tài liệu.
## Bước 3: Kiểm tra hỗ trợ trích xuất hình ảnh
Trước khi lặp lại các hình ảnh, hãy kiểm tra xem tài liệu có hỗ trợ trích xuất hình ảnh hay không.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Bước này đảm bảo rằng tài liệu chứa hình ảnh có thể trích xuất được.
## Bước 4: Lặp lại các hình ảnh được trích xuất
Bây giờ, hãy lặp lại các hình ảnh được trích xuất để truy cập thông tin chi tiết về từng hình ảnh, chẳng hạn như chỉ mục trang, tọa độ hình chữ nhật và loại hình ảnh.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Vòng lặp này in ra thông tin về từng hình ảnh được trích xuất, bao gồm cả vị trí và loại của nó.

## Phần kết luận
Trong hướng dẫn này, chúng ta đã học cách sử dụng GroupDocs.Parser cho .NET để trích xuất hình ảnh từ tài liệu theo chương trình. Bằng cách làm theo các bước này, bạn có thể tích hợp chức năng trích xuất hình ảnh tài liệu vào các ứng dụng .NET của mình một cách liền mạch.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất hình ảnh từ tất cả các định dạng tài liệu không?
GroupDocs.Parser hỗ trợ trích xuất hình ảnh từ nhiều định dạng khác nhau, bao gồm PDF, DOCX, XLSX, v.v.
### Có bản dùng thử miễn phí cho GroupDocs.Parser không?
 Có, bạn có thể truy cập bản dùng thử miễn phí của GroupDocs.Parser từ[trang mạng](https://releases.groupdocs.com/).
### Tôi có thể tìm tài liệu về GroupDocs.Parser ở đâu?
 Tài liệu chi tiết về GroupDocs.Parser có thể được tìm thấy[đây](https://tutorials.groupdocs.com/parser/net/).
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Parser?
 Bạn có thể xin giấy phép tạm thời từ[trang giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/).
### Tôi có thể nhận hỗ trợ cho GroupDocs.Parser ở đâu?
 Để được hỗ trợ và trợ giúp kỹ thuật, hãy truy cập[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).