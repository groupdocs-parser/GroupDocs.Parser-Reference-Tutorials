---
date: '2026-06-22'
description: Nắm vững việc phân tích tài liệu java bằng cách trích xuất hình ảnh và
  giảm mức sử dụng bộ nhớ với GroupDocs.Parser. Tìm hiểu custom handlers, resource
  filtering, và performance tips.
keywords:
- java document parsing
- reduce memory usage
- load external resources
- skip unwanted images
- extract pictures docx
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Master java document parsing by extracting images and reducing memory
    usage with GroupDocs.Parser. Learn custom handlers, resource filtering, and performance
    tips.
  headline: 'Java Document Parsing: Extract Images from Documents with GroupDocs.Parser'
  type: TechArticle
- description: Master java document parsing by extracting images and reducing memory
    usage with GroupDocs.Parser. Learn custom handlers, resource filtering, and performance
    tips.
  name: 'Java Document Parsing: Extract Images from Documents with GroupDocs.Parser'
  steps:
  - name: Create a custom handler
    text: '`ExternalResourceHandler` is an interface that lets you decide whether
      a specific external resource—such as an image—should be loaded. Implement the
      `onLoading` method and return `true` for resources you want to keep, `false`
      to skip them. The `onLoading` method receives the resource metadata and sh'
  - name: Configure `ParserSettings` with the handler
    text: '`ParserSettings` is a configuration class that holds options like custom
      handlers, detection settings, and performance tweaks for the parser. Pass your
      handler instance to `ParserSettings` before opening a document.'
  - name: Fine‑tune the filtering logic
    text: If you need more sophisticated rules—such as filtering by image size, format,
      or URI pattern—extend the `onLoading` method accordingly. For example, you can
      skip any image larger than 2 MB or ignore all PNG files.
  type: HowTo
- questions:
  - answer: It lets you control which external resources are loaded, enhancing security
      and performance by filtering out unnecessary files.
    question: What is the primary purpose of using a custom `ExternalResourceHandler`?
  - answer: Yes, a free trial is available, but advanced features and large‑scale
      deployments require a valid license.
    question: Can I use GroupDocs.Parser for Java without a license?
  - answer: Wrap parsing calls in try‑catch blocks for `IOException` and other specific
      exceptions to gracefully handle errors.
    question: How do I handle exceptions during parsing with GroupDocs.Parser?
  - answer: Incorrect URI checks can skip needed files; use logging or breakpoints
      to verify your conditions.
    question: What are common pitfalls when filtering resources?
  - answer: Absolutely—GroupDocs.Parser supports PDFs, Word, Excel, PowerPoint, and
      many other formats.
    question: Is it possible to parse non‑HTML documents using GroupDocs.Parser for
      Java?
  type: FAQPage
title: 'Phân tích tài liệu Java: Trích xuất hình ảnh từ tài liệu bằng GroupDocs.Parser'
type: docs
url: /vi/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Phân tích tài liệu Java: Trích xuất hình ảnh từ tài liệu với GroupDocs.Parser

Trong hướng dẫn toàn diện này, bạn sẽ học các kỹ thuật **java document parsing** để trích xuất hình ảnh từ nhiều loại tệp khác nhau bằng GroupDocs.Parser cho Java. Chúng tôi sẽ hướng dẫn cài đặt thư viện, tạo một `ExternalResourceHandler` tùy chỉnh, và áp dụng bộ lọc thông minh để bạn chỉ tải các tài nguyên thực sự cần thiết—giúp **giảm việc sử dụng bộ nhớ** và tăng tốc xử lý.

## Câu trả lời nhanh
- **GroupDocs.Parser làm gì?** Nó phân tích hơn 50 định dạng tệp, cung cấp văn bản, hình ảnh và các tài nguyên nhúng khác để sử dụng trong lập trình.  
- **Tôi có thể bỏ qua các hình ảnh không mong muốn không?** Có—triển khai một `ExternalResourceHandler` tùy chỉnh để lọc tài nguyên ngay lập tức.  
- **Phiên bản Maven nào được yêu cầu?** Sử dụng GroupDocs.Parser Java 25.5 hoặc mới hơn.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc đánh giá; giấy phép vĩnh viễn là bắt buộc cho môi trường sản xuất.  
- **Cách tiếp cận này có an toàn với đa luồng không?** Tạo một thể hiện `Parser` riêng cho mỗi luồng; các đối tượng không được chia sẻ.

## “Trích xuất hình ảnh từ tài liệu” là gì?
Trích xuất hình ảnh từ tài liệu có nghĩa là lấy các tệp hình ảnh nhúng một cách lập trình để bạn có thể lưu trữ, hiển thị hoặc xử lý chúng bên ngoài tệp gốc. Hoạt động này rất quan trọng khi bạn cần ảnh thu nhỏ, trực quan hoá dữ liệu, hoặc tái sử dụng tài nguyên truyền thông mà không cần giữ toàn bộ tài liệu nguồn.

## Tại sao phải lọc tài nguyên khi trích xuất hình ảnh?
Lọc tài nguyên khi trích xuất hình ảnh cho phép bạn **giảm việc sử dụng bộ nhớ lên tới 70 %** khi xử lý các tệp lớn, vì các tệp nhị phân không mong muốn sẽ không bao giờ vào heap của JVM. Nó cũng cải thiện bảo mật bằng cách ngăn chặn nội dung tiềm ẩn không an toàn được tải, và tăng tốc quy trình—các hợp đồng lớn với hàng trăm đồ họa trang trí có thể được phân tích trong một phần thời gian so với trước.

## Yêu cầu trước

- **Bộ công cụ phát triển Java (JDK)** – phiên bản 8 hoặc cao hơn.  
- **Maven** – để quản lý phụ thuộc.  
- Kiến thức cơ bản về Java I/O và xử lý ngoại lệ.

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

Hoặc, tải phiên bản mới nhất từ [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Nhận giấy phép
- **Bản dùng thử miễn phí** – khám phá các tính năng cốt lõi mà không tốn phí.  
- **Giấy phép tạm thời** – mở khóa toàn bộ chức năng trong quá trình đánh giá.  
- **Giấy phép mua** – bắt buộc cho triển khai thương mại.

## Cách lọc tài nguyên khi trích xuất hình ảnh
Để lọc tài nguyên, triển khai một `ExternalResourceHandler` quyết định tệp nhúng nào sẽ được tải. Đăng ký trình xử lý này trong `ParserSettings` trước khi mở tài liệu, sau đó gọi parser. Trình xử lý nhận siêu dữ liệu của mỗi tài nguyên, cho phép bạn chấp nhận hoặc từ chối dựa trên tiêu chí như loại, kích thước hoặc tên, đảm bảo chỉ các hình ảnh cần thiết được xử lý.

### Bước 1: Tạo trình xử lý tùy chỉnh
`ExternalResourceHandler` là một giao diện cho phép bạn quyết định liệu một tài nguyên bên ngoài cụ thể—như một hình ảnh—có nên được tải hay không. Triển khai phương thức `onLoading` và trả về `true` cho các tài nguyên bạn muốn giữ, `false` để bỏ qua chúng. Phương thức `onLoading` nhận siêu dữ liệu tài nguyên và nên trả về `true` để tải hoặc `false` để bỏ qua tài nguyên.

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

### Bước 2: Cấu hình `ParserSettings` với trình xử lý
`ParserSettings` là lớp cấu hình chứa các tùy chọn như trình xử lý tùy chỉnh, cài đặt phát hiện và tối ưu hiệu năng cho parser. Truyền thể hiện trình xử lý của bạn vào `ParserSettings` trước khi mở tài liệu.

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
Nếu bạn cần các quy tắc phức tạp hơn—như lọc theo kích thước hình ảnh, định dạng, hoặc mẫu URI—mở rộng phương thức `onLoading` cho phù hợp. Ví dụ, bạn có thể bỏ qua bất kỳ hình ảnh nào lớn hơn 2 MB hoặc bỏ qua tất cả các tệp PNG.

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Ứng dụng thực tiễn

1. **Hệ thống quản lý tài liệu** – Lấy chỉ các hình ảnh cần thiết từ hợp đồng đã quét để tạo ảnh thu nhỏ.  
2. **Dịch vụ trích xuất dữ liệu** – Bỏ qua đồ họa trang trí và tập trung vào biểu đồ chứa dữ liệu quan trọng.  
3. **Công cụ thu thập web** – Lọc bỏ các pixel theo dõi khi lấy các phương tiện có ý nghĩa từ tài liệu dựa trên HTML.

## Các cân nhắc về hiệu năng
Parser là lớp cốt lõi mở tài liệu và cung cấp truy cập vào nội dung của nó.  
- **Lọc sớm**: Áp dụng trình xử lý tùy chỉnh của bạn trước khi duyệt qua các tài nguyên để tránh tải dữ liệu không mong muốn vào bộ nhớ.  
- **Giải phóng kịp thời**: Sử dụng try‑with‑resources (`try (Parser parser = …)`) để giải phóng tài nguyên gốc.  
- **Xử lý bất đồng bộ**: Đối với các lô lớn, xử lý tài liệu bằng các luồng song song trong khi mỗi thể hiện `Parser` được giới hạn trong một luồng duy nhất.

## Các vấn đề thường gặp & Giải pháp

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| Không có hình ảnh nào được trả về | Trình xử lý bỏ qua tất cả tài nguyên một cách vô tình | Kiểm tra điều kiện `if` và đảm bảo `args.setSkipped(true)` chỉ được gọi cho các URI không mong muốn. |
| `IOException` trên các tệp lớn | Bộ nhớ heap không đủ | Tăng bộ nhớ heap JVM (`-Xmx2g`) hoặc xử lý các trang theo các phần nhỏ hơn. |
| Giấy phép không được công nhận | Sử dụng DLL dùng thử trong mã sản xuất | Áp dụng đúng đường dẫn tệp giấy phép qua `License.setLicense("path/to/license")`. |

## Câu hỏi thường gặp

**Q: Mục đích chính của việc sử dụng `ExternalResourceHandler` tùy chỉnh là gì?**  
A: Nó cho phép bạn kiểm soát tài nguyên bên ngoài nào sẽ được tải, nâng cao bảo mật và hiệu năng bằng cách lọc bỏ các tệp không cần thiết.

**Q: Tôi có thể sử dụng GroupDocs.Parser cho Java mà không có giấy phép không?**  
A: Có, bản dùng thử miễn phí có sẵn, nhưng các tính năng nâng cao và triển khai quy mô lớn yêu cầu giấy phép hợp lệ.

**Q: Làm thế nào để xử lý ngoại lệ khi phân tích bằng GroupDocs.Parser?**  
A: Bao quanh các lời gọi phân tích trong khối try‑catch cho `IOException` và các ngoại lệ cụ thể khác để xử lý lỗi một cách nhẹ nhàng.

**Q: Những sai lầm phổ biến khi lọc tài nguyên là gì?**  
A: Kiểm tra URI không đúng có thể bỏ qua các tệp cần thiết; sử dụng ghi log hoặc breakpoint để xác minh các điều kiện của bạn.

**Q: Có thể phân tích các tài liệu không phải HTML bằng GroupDocs.Parser cho Java không?**  
A: Chắc chắn—GroupDocs.Parser hỗ trợ PDF, Word, Excel, PowerPoint và nhiều định dạng khác.

## Các bước tiếp theo
Khám phá toàn bộ [API Reference](https://reference.groupdocs.com/parser/java) để biết thêm các cài đặt như `ParserSettings.setDetectTables(true)` để trích xuất bảng, hoặc thử nghiệm với `ParserSettings.setExtractEmbeddedFonts(true)` để trích xuất phông chữ.

---

**Cập nhật lần cuối:** 2026-06-22  
**Kiểm tra với:** GroupDocs.Parser 25.5 for Java  
**Tác giả:** GroupDocs  

**Tài nguyên**  
- **Tài liệu:** [Tài liệu GroupDocs.Parser](https://docs.groupdocs.com/parser/java/)  
- **Tham chiếu API:** [Chi tiết API](https://reference.groupdocs.com/parser/java)  
- **Tải xuống:** [Các phiên bản mới nhất](https://releases.groupdocs.com/parser/java/)

## Các hướng dẫn liên quan

- [Hướng dẫn tải tài liệu cho GroupDocs.Parser Java](/parser/java/document-loading/)
- [trích xuất hình ảnh pdf với GroupDocs.Parser Java – Hướng dẫn](/parser/java/image-extraction/)
- [Cách trích xuất hình ảnh từ pdf bằng GroupDocs.Parser trong Java: Hướng dẫn từng bước](/parser/java/image-extraction/extract-images-pdf-groupdocs-parser-java/)