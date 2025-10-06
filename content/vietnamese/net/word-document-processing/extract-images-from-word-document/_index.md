---
title: Trích xuất hình ảnh từ tài liệu Word
linktitle: Trích xuất hình ảnh từ tài liệu Word
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất hình ảnh từ tài liệu Word bằng GroupDocs.Parser cho .NET. Hướng dẫn này cung cấp hướng dẫn từng bước để tích hợp hình ảnh vào .NET của bạn.
weight: 11
url: /vi/net/word-document-processing/extract-images-from-word-document/
type: docs
---
# Trích xuất hình ảnh từ tài liệu Word

## Giới thiệu
Trong hướng dẫn này, bạn sẽ tìm hiểu cách trích xuất hình ảnh từ tài liệu Word bằng GroupDocs.Parser cho .NET. GroupDocs.Parser là một thư viện .NET mạnh mẽ cho phép bạn phân tích và trích xuất văn bản, siêu dữ liệu, hình ảnh, v.v. từ nhiều định dạng tài liệu khác nhau bao gồm Word (DOCX).
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn đã thiết lập các điều kiện tiên quyết sau:
- Visual Studio được cài đặt trên máy của bạn.
- Kiến thức cơ bản về lập trình C#.
- Đã cài đặt thư viện GroupDocs.Parser cho .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/parser/net/).
## Nhập không gian tên
Trước tiên, bạn cần nhập các không gian tên cần thiết trong dự án C# của mình để sử dụng các chức năng GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Bây giờ, hãy chia nhỏ quá trình trích xuất hình ảnh từ tài liệu Word thành các bước đơn giản:
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Bạn sẽ bắt đầu bằng cách tạo một phiên bản của`Parser`lớp, cung cấp đường dẫn đến tài liệu Word của bạn làm đầu vào.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Mã để trích xuất hình ảnh ở đây
}
```
## Bước 2: Trích xuất hình ảnh từ tài liệu Word
 Tiếp theo, sử dụng`GetImages()` phương pháp của`Parser` đối tượng để trích xuất hình ảnh từ tài liệu.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Bước 3: Xác định các tùy chọn lưu ảnh
Chỉ định các tùy chọn để lưu hình ảnh được trích xuất. Ví dụ: bạn có thể chọn định dạng hình ảnh (ví dụ: PNG) và định cấu hình các cài đặt khác.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Bước 4: Lặp lại các hình ảnh được trích xuất và lưu
Lặp lại từng hình ảnh được trích xuất và lưu nó vào một tệp bằng các tùy chọn đã chỉ định.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Lưu hình ảnh vào tệp PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Phần kết luận
Trong hướng dẫn này, bạn đã học cách trích xuất hình ảnh từ tài liệu Word bằng GroupDocs.Parser cho .NET. Bằng cách làm theo các bước này, bạn có thể dễ dàng tích hợp khả năng phân tích tài liệu và trích xuất hình ảnh vào các ứng dụng .NET của mình.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất hình ảnh từ các định dạng tài liệu khác ngoài Word không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng tài liệu khác nhau bao gồm PDF, PowerPoint, Excel, v.v.
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Parser?
 Bạn có thể xin giấy phép tạm thời cho mục đích thử nghiệm từ[đây](https://purchase.groupdocs.com/temporary-license/).
### Tôi có thể tìm thêm tài liệu về GroupDocs.Parser cho .NET ở đâu?
 Bạn có thể tham khảo tài liệu đầy đủ[đây](https://tutorials.groupdocs.com/parser/net/).
### Có bản dùng thử miễn phí cho GroupDocs.Parser không?
 Có, bạn có thể khám phá các tính năng của GroupDocs.Parser với bản dùng thử miễn phí[đây](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ hoặc đặt câu hỏi liên quan đến GroupDocs.Parser?
 Bạn có thể đăng câu hỏi của mình lên[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).