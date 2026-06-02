---
date: '2026-01-19'
description: Tìm hiểu cách trích xuất hình ảnh từ tài liệu Word bằng GroupDocs.Parser
  cho Java và lưu hình ảnh Word dưới dạng PNG một cách hiệu quả.
keywords:
- extract images from Word documents
- GroupDocs.Parser for Java
- automate image extraction
title: Trích xuất hình ảnh từ Word bằng GroupDocs.Parser cho Java
type: docs
url: /vi/java/image-extraction/extract-images-word-docs-groupdocs-parser-java/
weight: 1
---

# Trích xuất hình ảnh từ Word bằng GroupDocs.Parser cho Java

Việc trích xuất hình ảnh từ các tệp Word một cách thủ công tốn thời gian và dễ gây lỗi. Trong hướng dẫn này, bạn sẽ khám phá **cách trích xuất hình ảnh từ Word** một cách tự động bằng GroupDocs.Parser cho Java, và sau đó **lưu hình ảnh Word dưới dạng PNG** để xử lý tiếp theo. Chúng tôi sẽ hướng dẫn qua quá trình cài đặt, mã nguồn và các mẹo thực hành tốt nhất để bạn có thể tích hợp việc trích xuất hình ảnh vào bất kỳ dự án Java nào.

## Câu trả lời nhanh
- **Thư viện làm gì?** Nó phân tích Word, PDF và nhiều định dạng khác để hiển thị văn bản, bảng và hình ảnh.  
- **Bao nhiêu dòng mã?** Khoảng 30 dòng Java, cộng thêm một vài dòng cấu hình.  
- **Có cần giấy phép không? trường sản xuất.  
- **Có thể trích xuất hình ảnh nhúng không? DOCX dưới dạng đối tượng `PageImageArea`. Điều này cho phép bạn lập trình để lấy ra mọi hình ảnh mà không cần mở tài liệu trong Microsoft Word.

## Tại sao nên sử dụng GroupDocs.Parser cho Java?
- **Tốc độ:** Phân tích thuần Java tránh được chi phí của COM hoặc tự động hóa Office.  
- **Độ tin cậy:** Hoạt động trên mọi nền tảng (Windows, Linux, macOS) và xử lý các tệp hỏng một cách nhẹ nhàng.  
- **Linh hoạt:** Hỗ trợ nhiều định dạng, vì vậy bạn có thể tái sử dụng cùng một đoạn mã cho PDF, PPTX, v.v.

## Yêu cầu trước
- **GroupDocs.Parser cho Java** (phiên bản 25.5 trở lên)  
- **JDK 8+**  
- Một IDE như IntelliJ IDEA, Eclipse hoặc NetBeans  

## Cài đặt GroupDocs.Parser cho Java

Thêm thư viện vào dự án Maven của bạn:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/parser/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-parser</artifactId>
      <version>25.5</version>
   </dependency>
</dependencies>
```

Hoặc tải phiên bản mới nhất trực tiếp từ [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Các bước lấy giấy phép
- **Bản dùng thử:** Bắt đầu với bản dùng thử miễn phí để khám phá các tính năng.  
- **Giấy phép tạm thời:** Nhận giấy phép tạm thời để thử nghiệm mở rộng nếu cần.  
- **Mua:** Mua giấy phép đầy đủ cho triển khai sản xuất.

## Hướng dẫn triển khai

Dưới đây là mã Java hoàn chỉnh, sẵn sàng chạy, **trích xuất hình ảnh từ Word** và lưu chúng dưới dạng tệp PNG.

### Bước 1: Khởi tạo Parser

```java
// Initialize the Parser with the document path.
try (Parser parser = new Parser(documentPath)) {
    // Proceed with image extraction...
}
```

### Bước 2: Trích xuất hình ảnh

```java
// Extract images from the document.
Iterable<PageImageArea> images = parser.getImages();
```

### Bước 3: Cấu hình tùy chọn hình ảnh

```java
// Set options to save images in PNG format.
ImageOptions options = new ImageOptions(ImageFormat.Png);
```

### Bước 4: Lưu mỗi hình ảnh

```java
int imageNumber = 0;
for (PageImageArea image : images) {
    String outputPath = YOUR_OUTPUT_DIRECTORY + "/" + imageNumber + ".png";
    image.save(outputPath, options);
    imageNumber++;
}
```

### Bước 5: Định nghĩa các phương thức trợ giúp cho đường dẫn

```java
public static String getDocumentDirectory() {
    return YOUR_DOCUMENT_DIRECTORY;
}

public static String getOutputDirectory() {
    return YOUR_OUTPUT_DIRECTORY;
}
```

Thay thế `YOUR_DOCUMENT_DIRECTORY` và `YOUR_OUTPUT_DIRECTORY` bằng các vị trí hệ thống tệp thực tế mà bạn dự định sử dụng.

## Cách trích xuất hình ảnh nhúng từ docx?
Lệnh `getImages()` tự động trả về **hình ảnh nhúng** từ tệp DOCX, bất kể chúng là nội tuyến, nổi hoặc là một phần của hình dạng. Không cần gọi API bổ sung.

## Cách trích xuất hình ảnh từ docx và lưu dưới dạng PNG?
Đối tượng `ImageOptions` được hiển thị trong **Bước 3** cấu hình định dạng đầu ra. Bằng cách truyền `ImageFormat.Png`, mỗi hình ảnh được trích xuất sẽ được lưu dưới dạng tệp PNG, đáp ứng yêu cầu **lưu hình ảnh Word dưới dạng PNG**.

## Ứng dụng thực tiễn
1. **Quản lý nội dung:** Lấy hình ảnh ra khỏi các tệp Word cũ để xây dựng thư viện tài sản kỹ thuật số.  
2. **Di chuyển dữ liệu:** Di chuyển đồ họa nhúng sang CMS mới mà không cần sao chép‑dán thủ công.  
3. **Lưu trữ tài liệu:** Lưu trữ hình ảnh riêng biệt để giảm kích thước lưu trữ và cải thiện khả năng tìm kiếm.  
4. **Xuất bản tự động:** Cung cấp các PNG đã trích xuất trực tiếp cho các công cụ tạo trang web hoặc mẫu email.

## Các cân nhắc về hiệu năng
- **Bộ nhớ:** Phân bổ heap đủ (`-Xmx2g` hoặc cao hơn) khi xử lý tài liệu lớn.  
- **Xử lý hàng loạt:** Lặp qua một thư mục các tệp và tái sử dụng một thể hiện `Parser` duy nhất cho mỗi tài liệu để giảm mức sử dụng lý tệp:** Khối try‑with‑resources đảm bảo parser được đóng kịp thời, ngăn ngừa rò rỉ thực sự chứa hình| **Định hướng hình ảnh không đúng** | Một số hình ảnh DOCX lưu trữ thông tin xoay EXIF; cần xử lý sau bằng thư viện ảnh nếu cần. |

## Câu hỏi thường gặp

**H: Định dạng tệp nào mà GroupDocs.Parser hỗ trợ để trích xuất hình ảnh?**  
Đ: Nó hỗ trợ DOC, DOCX, PDF, PPT, PPTX và nhiều định dạng khác, cung cấp hình ảnh thông qua cùng một phương thức `getImages()`.

**H: Tôi có thể trích xuất hình ảnh từ các tệp Word được bảo vệ bằng mật khẩu không?**  
Đ: Có—cung cấp mật khẩu cho hàm khởi tạo `Parser`, và thư viện sẽ giải mã tài liệu trước khi trích xuất.

**H: Có cách nào để chỉ trích xuất các loại hình ảnh cụ thể (ví dụ chỉ JPEG) không?**  
Đ: Sau khi lấy các đối tượng `PageImageArea`, kiểm tra `image.getFormat()` và lọc tương ứng trước khi lưu.

**H: Thư viện có hỗ trợ xử lý bất đồng bộ không?**  
Đ: Mặc dù API cốt lõi dụng `CompletableFuture` của Java để xử lý song song.

**H: Tôi có cần giấy phép thương mại cho việc sử dụng trong môi trường sản xuất không?**  
Đ: Bản dùng thử miễn phí đủ cho việc đánh giá, nhưng cần giấy phép trả phí cho triển khai thương mại.

## Kết luận
Bạn đã có một cho sản xuất để **cách trích xuất hình ảnh từ Word** bằng GroupDocs.Parser cho Java và **lưu hình ảnh Word dưới dạng PNG**. Hãy tích hợp đoạn mã này vào các quy trình hiện có, tự động hoá việc trích xuất hàng loạt và khai thác các tài sản hình ảnh ẩn trong các tệp Word của bạn.

---

**Cập nhật lần cuối:** 2026-01**Tài nguyên**
- **Tài liệu:** [GroupDocs Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- **Tham chiếu API:** [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)
- **Tải xuống:** [Latest Release](https://releases.groupdocs.com/parser/java/)
- **GitHub:** [Source Code on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- **Hỗ trợ miễn phí:** [GroupDocs Forum](https://forum.groupdocs.com/c/parser)
- **Giấy phép tạm thời:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)