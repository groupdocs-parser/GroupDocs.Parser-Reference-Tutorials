---
date: '2025-12-29'
description: Tìm hiểu cách trích xuất hình ảnh từ tài liệu và cách lọc tài nguyên
  bằng GroupDocs.Parser cho Java. Hướng dẫn này bao gồm cấu hình, trình xử lý tùy
  chỉnh và các ví dụ thực tế.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: Trích xuất hình ảnh từ tài liệu bằng GroupDocs.Parser Java – Hướng dẫn
type: docs
url: /vi/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Trích xuất hình ảnh từ tài liệu và lọc tài nguyên với GroupDocs.Parser Java

Việc trích xuất hình ảnh từ tài liệu là một yêu cầu phổ biến khi xây dựng các pipeline xử lý tài liệu. Trong hướng dẫn này, bạn sẽ khám phá **cách trích xuất hình ảnh từ tài liệu** bằng GroupDocs.Parser cho Java, đồng thời học **cách lọc tài nguyên** để chỉ tải những tệp bạn cần. Chúng tôi sẽ hướng dẫn cách thiết lập thư viện, tạo một `ExternalResourceHandler` tùy chỉnh, và áp dụng logic lọc để giữ cho ứng dụng của bạn nhanh và an toàn.

## Câu trả lời nhanh
- **GroupDocs.Parser làm gì?** Nó phân tích nhiều định dạng tài liệu và cung cấp cho bạn quyền truy cập vào văn bản, hình ảnh và các tài nguyên nhúng khác.  
- **Tôi có thể bỏ qua các hình ảnh không mong muốn không?** Có — bằng cách triển khai một `ExternalResourceHandler` tùy chỉnh, bạn có thể quyết định tải tài nguyên nào.  
- **Phiên bản Maven nào được yêu cầu?** Sử dụng GroupDocs.Parser Java 25.5 hoặc mới hơn.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc đánh giá; giấy phép vĩnh viễn cần thiết cho môi trường sản xuất.  
- **Cách tiếp cận này có an toàn với đa luồng không?** Các đối tượng Parser không được chia sẻ giữa các luồng; tạo một thể hiện `Parser` mới cho mỗi luồng.

## “Trích xuất hình ảnh từ tài liệu” là gì?
Khi một tài liệu chứa các hình ảnh, biểu đồ hoặc phương tiện nhúng khác, “trích xuất hình ảnh từ tài liệu” có nghĩa là lấy các tệp nhị phân này một cách lập trình để bạn có thể lưu trữ, hiển thị hoặc xử lý tiếp bên ngoài tệp gốc.

## Tại sao phải lọc tài nguyên khi trích xuất hình ảnh?
Lọc tài nguyên giúp bạn:
- Giảm tiêu thụ bộ nhớ bằng cách bỏ qua các tệp lớn hoặc không liên quan.  
- Cải thiện bảo mật bằng cách ngăn việc tải nội dung có thể không an toàn.  
- Tăng tốc độ xử lý, đặc biệt với các tài liệu khổng lồ chứa nhiều đối tượng nhúng.

## Yêu cầu trước

- **Java Development Kit (JDK)** – phiên bản 8 hoặc cao hơn.  
- **Maven** – để quản lý phụ thuộc.  
- Kiến thức cơ bản về I/O và xử lý ngoại lệ trong Java.

## Cài đặt GroupDocs.Parser cho Java

Thêm kho lưu trữ GroupDocs và phụ thuộc parser vào `pom.xml` của bạn:

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

Hoặc tải phiên bản mới nhất từ [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Mua giấy phép
- **Bản dùng thử** – khám phá các tính năng cốt lõi mà không tốn phí.  
- **Giấy phép tạm thời** – mở khóa đầy đủ chức năng trong thời gian đánh giá.  
- **Giấy phép mua** – bắt buộc cho triển khai thương mại.

## Cách lọc tài nguyên khi trích xuất hình ảnh

### Bước 1: Tạo một handler tùy chỉnh
Định nghĩa một lớp kế thừa `ExternalResourceHandler`. Trong phương thức `onLoading` bạn quyết định tài nguyên nào sẽ được giữ lại.

```java
import com.groupdocs.parser.options.ExternalResourceHandler;
import com.groupdocs.parser.data.ExternalResourceLoadingArgs;

class Handler extends ExternalResourceHandler {
    @Override
    public void onLoading(ExternalResourceLoadingArgs args) {
        if (!args.getUri().endsWith("installation.png")) {
            args.setSkipped(true);
        }
        super.onLoading(args);
    }
}
```

### Bước 2: Cấu hình `ParserSettings` với handler
Truyền thể hiện `Handler` của bạn vào `ParserSettings` và sử dụng nó khi mở tài liệu.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.IOException;
import com.groupdocs.parser.options.ParserSettings;

public class LoadExternalResources {
    public static void run() throws IOException {
        ParserSettings settings = new ParserSettings(new Handler());
        
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
            Iterable<PageImageArea> images = parser.getImages();
            
            for (PageImageArea image : images) {
                System.out.println(image.getFileType());
            }
        }
    }
}
```

### Bước 3: Tinh chỉnh logic lọc
Nếu bạn cần các quy tắc phức tạp hơn — chẳng hạn lọc theo kích thước ảnh, định dạng, hoặc mẫu URI — hãy mở rộng phương thức `onLoading` cho phù hợp:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Ứng dụng thực tiễn

1. **Hệ thống quản lý tài liệu** – Lấy chỉ những hình ảnh cần thiết từ hợp đồng đã quét để tạo thumbnail.  
2. **Dịch vụ trích xuất dữ liệu** – Bỏ qua các đồ họa trang trí và tập trung vào biểu đồ chứa dữ liệu quan trọng.  
3. **Công cụ thu thập web** – Lọc bỏ pixel theo dõi trong khi lấy các phương tiện có ý nghĩa từ tài liệu dựa trên HTML.

## Các cân nhắc về hiệu năng
- **Lọc sớm**: Áp dụng handler tùy chỉnh trước khi duyệt qua tài nguyên để tránh tải dữ liệu không mong muốn vào bộ nhớ.  
- **Giải phóng kịp thời**: Sử dụng try‑with‑resources (`try (Parser parser = …)`) để giải phóng tài nguyên gốc.  
- **Xử lý bất đồng bộ**: Đối với các lô lớn, xử lý tài liệu bằng parallel streams trong khi mỗi thể hiện `Parser` chỉ được dùng trong một luồng.

## Các vấn đề thường gặp & Giải pháp
| Vấn đề | Nguyên nhân | Giải pháp |
|-------|-------------|----------|
| Không có hình ảnh nào được trả về | Handler vô tình bỏ qua tất cả tài nguyên | Kiểm tra lại điều kiện `if` và đảm bảo `args.setSkipped(true)` chỉ được gọi cho các URI không mong muốn. |
| `IOException` khi xử lý tệp lớn | Bộ nhớ heap không đủ | Tăng heap JVM (`-Xmx2g`) hoặc xử lý các trang theo từng phần nhỏ hơn. |
| Giấy phép không được công nhận | Sử dụng DLL dùng thử trong mã sản xuất | Áp dụng đúng đường dẫn file giấy phép qua `License.setLicense("path/to/license")`. |

## Câu hỏi thường gặp

**H: Mục đích chính của việc sử dụng `ExternalResourceHandler` tùy chỉnh là gì?**  
Đ: Nó cho phép bạn kiểm soát tài nguyên bên ngoài nào sẽ được tải, nâng cao bảo mật và hiệu năng bằng cách lọc bỏ các tệp không cần thiết.

**H: Tôi có thể dùng GroupDocs.Parser cho Java mà không có giấy phép không?**  
Đ: Có, bản dùng thử miễn phí có sẵn, nhưng một số tính năng nâng cao có thể bị giới hạn cho đến khi bạn có giấy phép tạm thời hoặc mua.

**H: Làm sao xử lý ngoại lệ khi phân tích bằng GroupDocs.Parser?**  
Đ: Bao bọc các lời gọi phân tích trong khối try‑catch cho `IOException` và các ngoại lệ cụ thể khác để xử lý lỗi một cách mềm mại.

**H: Những cạm bẫy thường gặp khi lọc tài nguyên là gì?**  
Đ: Kiểm tra URI không chính xác có thể bỏ qua các tệp cần thiết; hãy dùng logging hoặc breakpoint để xác minh điều kiện của bạn.

**H: Có thể phân tích tài liệu không phải HTML bằng GroupDocs.Parser cho Java không?**  
Đ: Chắc chắn — GroupDocs.Parser hỗ trợ PDF, Word, Excel, PowerPoint và nhiều định dạng khác.

## Bước tiếp theo
Tìm hiểu sâu hơn về thư viện bằng cách khám phá [API Reference](https://reference.groupdocs.com/parser/java) hoặc thử nghiệm các thiết lập bổ sung như `ParserSettings.setDetectTables(true)` để trích xuất bảng.

---

**Cập nhật lần cuối:** 2025-12-29  
**Kiểm thử với:** GroupDocs.Parser 25.5 cho Java  
**Tác giả:** GroupDocs  

**Tài nguyên**  
- **Tài liệu:** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **Tham khảo API:** [API Details](https://reference.groupdocs.com/parser/java)  
- **Tải xuống:** [Latest Versions](https://releases.groupdocs.com/parser/java/)