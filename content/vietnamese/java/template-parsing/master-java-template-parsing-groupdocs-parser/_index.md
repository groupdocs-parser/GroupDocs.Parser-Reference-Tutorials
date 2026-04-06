---
date: '2026-02-11'
description: Tìm hiểu cách trích xuất dữ liệu hoá đơn bằng GroupDocs.Parser cho Java.
  Hướng dẫn này chỉ cách tự động hoá việc trích xuất tài liệu, tạo các trường liên
  kết và xử lý tài liệu hàng loạt.
keywords:
- Java template parsing
- GroupDocs.Parser
- regular expressions in Java
title: Trích xuất dữ liệu hoá đơn bằng Java Parsing – GroupDocs.Parser
type: docs
url: /vi/java/template-parsing/master-java-template-parsing-groupdocs-parser/
weight: 1
---

# Trích xuất dữ liệu hoá đơn bằng Java Parsing – GroupDocs.Parser

Trong môi trường kinh doanh nhanh‑chóng ngày nay, **trích xuất dữ liệu hoá đơn** một cách nhanh chóng và chính xác là bước quan trọng để tự động hoá quy trình tài chính. Dù bạn đang xử lý một hoá đơn duy nhất hay hàng nghìn hoá đơn trong một lô, GroupDocs.Parser cho Java cho phép bạn định nghĩa các mẫu linh hoạt, sử dụng biểu thức chính quy, và **tạo các trường liên kết** thích ứng với bất kỳ bố cục tài liệu nào. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn cách cài đặt thư viện, xây dựng một mẫu **trích xuất dữ liệu hoá đơn**, và phân tích tài liệu ở quy mô lớn.

## Câu trả lời nhanh
- **“Trích xuất dữ liệu hoá đơn” có nghĩa là gì?** Nó đề cập đến việc tự động lấy các trường như số hoá đơn, ngày, thuế và tổng cộng từ các tệp PDF, DOCX hoặc hình ảnh.  
- **Tôi nên sử dụng thư viện nào?** GroupDocs.Parser cho Java cung cấp khả năng trích xuất dựa trên mẫu mạnh mẽ với hỗ trợ regex.  
- **Tôi có thể xử lý nhiều tệp cùng lúc không?** Có – kết hợp parser với các kỹ thuật xử lý tài liệu hàng loạt.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoặc giấy phép tạm thời đủ cho việc đánh giá; giấy phép mua sẽ cần cho môi trường sản xuất.  
- **Có phù hợp với Java 8+ không?** Chắc chắn – thư viện hỗ trợ JDK 8 và các phiên bản mới hơn.

## “Trích xuất dữ liệu hoá đơn” là gì?
Việc trích xuất dữ liệu hoá đơn có nghĩa là tự động xác định và lấy các thông tin quan trọng—như số hoá đơn, ngày, số tiền thuế và tổng cộng—trực tiếp từ các tài liệu kỹ thuật số, loại bỏ việc nhập dữ liệu thủ công.

## Tại sao nên sử dụng GroupDocs.Parser cho Java?
- **Độ chính xác cao** với regex và vị trí trường liên kết.  
- **Hỗ trợ nhiều định dạng** (PDF, DOCX, hình ảnh).  
- **Khả năng mở rộng** – lý tưởng cho cả trường hợp tài liệu đơn và xử lý tài liệu hàng loạt.  
- **Dễ dàng tích hợp** với các ứng dụng Java hiện có.

## Yêu cầu trước
- JDK 8 hoặc cao hơn.  
- Một IDE (IntelliJ IDEA, Eclipse, v.v.).  
- Truy cập vào thư viện GroupDocs.Parser cho Java (tải xuống hoặc Maven).

### Thư viện, Phiên bản và Phụ thuộc cần thiết
Thêm kho lưu trữ và phụ thuộc vào `pom.xml` của bạn:

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

Bạn cũng có thể **tải xuống JAR mới nhất** từ [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Kiến thức tiên quyết
Kiến thức lập trình Java cơ bản và quen thuộc với I/O tệp sẽ giúp các bước thực hiện suôn sẻ hơn.

## Cài đặt GroupDocs.Parser cho Java
1. **Thêm phụ thuộc Maven** (hoặc JAR) vào dự án của bạn.  
2. **Nhận giấy phép** – bạn có thể bắt đầu với bản dùng thử miễn phí hoặc giấy phép tạm thời từ [đây](https://purchase.groupdocs.com/temporary-license/).  
3. **Khởi tạo parser** – đoạn mã dưới đây hiển thị các import cần thiết và một khởi tạo đơn giản.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.*;
import com.groupdocs.parser.templates.*;
```

## Cách tạo trường liên kết trong mẫu
Trường liên kết cho phép bạn nắm bắt dữ liệu xuất hiện ở vị trí cố định so với một trường đã biết khác (ví dụ, giá trị thuế xuất hiện sau từ “Tax”).

### Định nghĩa trường biểu thức chính quy
Đầu tiên, chúng ta xác định nhãn **Tax** bằng một mẫu regex.

```java
// Create a template field with a regex position
TemplateField regexField = new TemplateField(
        new TemplateRegexPosition("Tax"), 
        "Tax");
```

### Cấu hình trường liên kết
Tiếp theo, chúng ta định nghĩa trường chứa giá trị thuế thực tế, được đặt vị trí tương đối so với nhãn **Tax**.

```java
// Create a linked field based on the position of 'Tax'
TemplateField linkedField = new TemplateField(
        new TemplateLinkedPosition(
                "Tax",
                new Size(100, 20),
                new TemplateLinkedPositionEdges(false, false, true, false)),
        "TaxValue");
```

### Tập hợp mẫu
Kết hợp trường regex và trường liên kết thành một đối tượng mẫu duy nhất.

```java
// Combine both fields into a comprehensive template
Template templateWithRegexAndLink = new Template(Arrays.asList(
        new TemplateItem[]{regexField, linkedField}));
```

## Cách trích xuất dữ liệu hoá đơn bằng mẫu đã định nghĩa
Bây giờ mẫu đã sẵn sàng, chúng ta có thể phân tích một hoá đơn và lấy các giá trị mong muốn.

### Phân tích tài liệu
Mở file PDF (hoặc bất kỳ định dạng hỗ trợ nào) và áp dụng mẫu.

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY/InvoiceSample.pdf")) {
    // Extract data according to the defined template
    DocumentData data = parser.parseByTemplate(templateWithRegexAndLink);
```

### Lặp qua dữ liệu đã trích xuất
Lặp qua các kết quả và in ra tên và giá trị của mỗi trường.

```java
    // Loop through all extracted data items
    for (int i = 0; i < data.getCount(); i++) {
        Object pageArea = data.get(i).getPageArea();
        if (pageArea instanceof PageTextArea) {
            PageTextArea area = (PageTextArea) pageArea;
            System.out.println(data.get(i).getName() + ": " + area.getText());
        } else {
            System.out.println(data.get(i).getName() + ": Not a template field");
        }
    }
}
```

#### Mẹo khắc phục sự cố
- Kiểm tra đường dẫn tệp và đảm bảo tài liệu có thể truy cập.  
- Kiểm tra biểu thức chính quy của bạn bằng công cụ như regex101.com trước khi nhúng.  
- Điều chỉnh các thiết lập `Size` và edge trong `TemplateLinkedPosition` nếu trường liên kết không được bắt đúng.

## Ứng dụng thực tiễn
### Các trường hợp sử dụng thực tế
- **Xử lý hoá đơn** – tự động lấy số hoá đơn, ngày, thuế và tổng cộng cho hệ thống kế toán.  
- **Quản lý hợp đồng** – trích xuất các bên, ngày hiệu lực và các điều khoản quan trọng.  
- **Trích xuất dữ liệu khách hàng** – lấy chi tiết đơn hàng từ các mẫu đã điền.

### Khả năng tích hợp
Kết hợp dữ liệu đã trích xuất với các nền tảng ERP hoặc CRM để tạo quy trình làm việc tự động đầu‑tới‑cuối.

## Mẹo xử lý tài liệu hàng loạt
Khi làm việc với **xử lý tài liệu hàng loạt**, hãy cân nhắc:
- Tái sử dụng một thể hiện `Parser` duy nhất cho nhiều tệp để giảm tải.  
- Chạy các tác vụ phân tích trong **parallel streams** hoặc **executor services**.  
- Lưu kết quả đã trích xuất vào cơ sở dữ liệu hoặc CSV để báo cáo downstream.

## Các yếu tố hiệu năng
- **Đơn giản hoá mẫu** – ít trường hơn và mẫu regex đơn giản hơn giúp tăng tốc phân tích.  
- **Quản lý bộ nhớ** – đóng các đối tượng `Parser` kịp thời (như trong ví dụ try‑with‑resources).  
- **Xử lý theo lô** – nhóm tài liệu để cân bằng việc sử dụng CPU và I/O.

## Câu hỏi thường gặp

**Q: GroupDocs.Parser cho Java là gì?**  
A: Đó là một thư viện Java giúp trích xuất dữ liệu có cấu trúc từ PDF, tài liệu Word, hình ảnh và hơn thế nữa bằng các mẫu có thể tùy chỉnh.

**Q: Làm thế nào để thiết lập dự án Maven với GroupDocs.Parser?**  
A: Thêm kho lưu trữ và `<dependency>` được hiển thị trong khối Maven ở trên vào `pom.xml` của bạn.

**Q: Tôi có thể sử dụng GroupDocs.Parser mà không mua giấy phép không?**  
A: Có, bạn có thể bắt đầu với bản dùng thử miễn phí hoặc nhận giấy phép tạm thời để đánh giá.

**Q: Trường liên kết trong mẫu là gì?**  
A: Trường liên kết là các phần tử mẫu có vị trí được định nghĩa tương đối so với một trường khác, cho phép trích xuất chính xác dựa trên bố cục.

**Q: Làm thế nào để mở rộng giải pháp cho hàng nghìn hoá đơn?**  
A: Thực hiện xử lý tài liệu hàng loạt, tái sử dụng các thể hiện parser và cân nhắc đa luồng để xử lý khối lượng lớn một cách hiệu quả.

## Kết luận
Bằng cách làm theo hướng dẫn này, bạn đã biết cách **trích xuất dữ liệu hoá đơn** bằng Java parsing, tận dụng biểu thức chính quy, và **tạo các trường liên kết** thích ứng với bất kỳ bố cục hoá đơn nào. Hãy thử nghiệm với các mẫu khác nhau, tích hợp kết quả vào hệ thống tài chính của bạn, và khám phá các tính năng nâng cao như bộ chuyển đổi dữ liệu tùy chỉnh và hỗ trợ OCR.

---

**Cập nhật lần cuối:** 2026-02-11  
**Kiểm thử với:** GroupDocs.Parser 25.5  
**Tác giả:** GroupDocs