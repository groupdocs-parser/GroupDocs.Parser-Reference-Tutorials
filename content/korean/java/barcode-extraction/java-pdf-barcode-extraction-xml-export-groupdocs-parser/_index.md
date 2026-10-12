---
date: '2026-10-12'
description: Java와 GroupDocs.Parser를 사용하여 PDF에서 QR을 추출하고 barcode 데이터를 XML로 내보내어 다운스트림
  처리에 활용하는 방법을 배웁니다.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Java와 GroupDocs.Parser를 사용하여 PDF에서 QR을 추출하고 barcode 데이터를 XML로 내보내어
  다운스트림 처리에 활용하는 방법을 배웁니다.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Java와 GroupDocs.Parser를 사용하여 PDF에서 QR을 추출하는 방법
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: Java와 GroupDocs.Parser를 사용하여 PDF에서 QR을 추출하는 방법
type: docs
url: /ko/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Java와 GroupDocs.Parser를 사용하여 PDF에서 QR 추출하는 방법

현대 비즈니스 워크플로에서 **PDF에서 QR 추출**은 수동 데이터 입력 병목 현상을 완전 자동화된 파이프라인으로 전환할 수 있습니다. 선적 명세서, 소매 영수증 또는 제품 카탈로그를 처리하든, QR 정보를 빠르고 신뢰성 있게 추출하는 것은 하위 시스템에 필수적입니다. 이 튜토리얼에서는 **Java용 GroupDocs.Parser**를 사용하여 PDF에서 QR 코드(및 기타 바코드)를 읽고, 결과를 ERP, 재고 또는 분석 플랫폼에서 사용할 수 있는 깔끔한 XML 파일로 내보내는 방법을 단계별로 안내합니다.

## 빠른 답변
- **GroupDocs.Parser for Java는 무엇을 하나요?** PDF 파일을 읽고 바코드, 표, 텍스트와 같은 구조화된 데이터를 추출합니다.  
- **QR 코드를 어떻게 추출하나요?** `BarcodeOptions`를 QR 유형으로 설정하고 `parser.getBarcodes()`를 호출합니다.  
- **Java에서 QR 코드를 읽을 수 있나요?** 예—옵션에서 바코드 유형을 `"QR"`로 설정합니다.  
- **라이선스가 필요합니까?** 테스트용으로는 체험판을 사용할 수 있지만, 프로덕션에서는 상용 라이선스가 필요합니다.  
- **필요한 Java 버전은?** Java 8 이상을 권장합니다.

## PDF 처리 맥락에서 “PDF에서 QR 추출”이란 무엇인가요?
PDF에서 QR를 추출한다는 것은 각 페이지를 스캔하여 QR‑인코딩된 그래픽을 찾고, 포함된 데이터를 디코딩하여 프로그램이 사용하기 쉬운 형식으로 반환하는 것을 의미합니다. GroupDocs.Parser는 저수준 이미지 분석을 추상화하여 픽셀 조작보다 비즈니스 로직에 집중할 수 있게 해줍니다.

## QR 추출에 GroupDocs.Parser를 사용하는 이유는?
GroupDocs.Parser는 **30개 이상의 입력 형식**을 지원하며, 전체 파일을 메모리에 로드하지 않고 **500 MB**까지의 PDF를 처리할 수 있어 저해상도 스캔에서도 높은 정확도의 결과를 제공합니다. 속도를 위해 `QualityMode.Low`를, 최대 정밀도를 위해 `QualityMode.High`를 선택할 수 있으며, 동일한 API가 PDF, 이미지 및 Office 문서에 모두 적용되어 여러 라이브러리를 사용할 필요가 없습니다.

## 전제 조건
- **Java용 GroupDocs.Parser** (버전 25.5 이상).  
- Maven 또는 수동 JAR 다운로드.  
- Java 8+ 개발 환경 (IntelliJ IDEA, Eclipse 또는 기타 편집기).  

## Java용 GroupDocs.Parser 설정
### Maven 사용
Add the GroupDocs repository and dependency to your `pom.xml`:

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

### 직접 다운로드
또는 최신 JAR를 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/)에서 다운로드하십시오.

#### 라이선스 획득 단계
- **무료 체험:** 전체 기능을 제공하는 30일 체험판.  
- **임시 라이선스:** 평가 기간 연장을 위한 임시 키를 요청합니다.  
- **구매:** 프로덕션 배포를 위한 상용 라이선스를 획득합니다.

### 기본 초기화 및 설정
분석하려는 PDF를 가리키는 `Parser` 인스턴스를 생성합니다:

`Parser`는 문서를 나타내며 텍스트, 표, 바코드와 같은 콘텐츠를 추출하는 메서드를 제공하는 GroupDocs.Parser의 핵심 클래스입니다.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## GroupDocs.Parser를 사용하여 Java PDF에서 QR 코드를 읽는 방법
GroupDocs.Parser를 사용하여 Java PDF에서 QR 코드를 읽으려면 파서 인스턴스를 생성하고, QR 유형을 대상으로 하는 바코드 옵션을 구성한 뒤, 바코드 추출 메서드를 호출하고 반환된 바코드 객체를 처리하면 됩니다. 이 과정은 간단하며 모든 PDF 페이지에서 작동하고, 디코딩된 값과 추가 처리를 위한 위치 메타데이터를 반환합니다.

### 단계 1: 바코드 지원 확인
Before attempting extraction, confirm that the document format supports barcode scanning:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*설명:* 이 검사는 지원되지 않는 파일 형식에서 발생할 수 있는 런타임 오류를 방지합니다.

### 단계 2: 바코드 옵션 구성 (Java에서 QR 코드 읽기)
`BarcodeOptions`는 감지할 바코드 심볼을 지정하고, 스캔 품질 모드를 설정하며, 감지 임계값과 같은 매개변수를 미세 조정하여 대상 QR 코드에 대한 최적 성능을 보장하는 구성 객체입니다.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*설명:* `QualityMode.Low`는 처리를 빠르게 하고, 추가 정확도가 필요하면 `High`로 전환합니다. `"QR"` 인자는 엔진에게 QR 유형 바코드만 찾도록 지시합니다.

### 단계 3: QR 데이터 추출
`parser.getBarcodes(options)`는 제공된 `BarcodeOptions`를 사용해 문서를 스캔하고, 디코딩된 QR 값, 페이지 번호, 페이지 내 바코드의 정확한 좌표를 포함하는 `PageBarcodeArea` 객체 컬렉션을 반환하여 정밀한 하위 처리를 가능하게 합니다.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*설명:* `parser.getBarcodes`는 각 객체가 디코딩된 QR 값과 페이지상의 위치를 포함하는 `PageBarcodeArea` 객체의 반복 가능한 컬렉션을 반환합니다.

## 추출된 데이터를 XML로 내보내기
### 단계 4: XML 내보내기 초기화
`XmlExporter`는 바코드 객체 컬렉션을 잘 구조화된 XML 문서로 변환하는 유틸리티 클래스이며, 각 바코드에 대해 페이지 인덱스, 위치 및 디코딩된 값을 속성으로 자동 생성하여 다른 시스템에 저장하거나 스트리밍할 수 있습니다.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*설명:* `XmlExporter`는 바코드 객체를 표준 XML로 직렬화하여 ERP 또는 재고 시스템과의 통합에 준비합니다.

### 단계 5: XML 파일 쓰기
Save the extracted QR information to disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*설명:* 결과 `data.xml` 파일에는 QR 코드당 하나의 `<Barcode>` 요소가 포함되며, 페이지 번호, 좌표 및 디코딩된 값을 속성으로 가집니다.

## 실제 적용 사례
1. **재고 관리:** 들어오는 선적 PDF의 QR 태그를 읽어 재고 데이터베이스를 자동으로 채웁니다.  
2. **공급망 가시성:** 물류 문서에 삽입된 QR 식별자를 추출하여 실시간으로 패키지를 추적합니다.  
3. **소매 영수증:** 디지털 영수증에 인쇄된 QR 코드를 통해 프로모션 또는 보증 정보를 가져옵니다.

## 성능 고려 사항
- **메모리 관리:** 매우 큰 PDF의 경우 전체 파일을 메모리에 로드하는 대신 스트리밍 방식으로 페이지를 처리합니다.  
- **QualityMode 선택:** 대량 처리 시 `Low`를 사용하고, 저해상도 스캔을 다룰 때는 `High`로 전환합니다.  
- **라이브러리 업데이트:** 최신 성능 향상 및 버그 수정을 활용하려면 GroupDocs.Parser를 최신 상태로 유지하십시오.

## 일반적인 문제 및 해결 방법
| 증상 | 가능한 원인 | 해결 방법 |
|---------|--------------|-----|
| 바코드가 반환되지 않음 | 잘못된 바코드 유형 지정 | `"QR"`를 적절한 유형(예: `"CODE_128"` )으로 변경합니다. |
| 대용량 PDF에서 메모리 부족 오류 | 전체 문서를 한 번에 로드함 | 페이지를 개별적으로 처리하거나 JVM 힙 크기(`-Xmx2g`)를 늘립니다. |
| XML 파일이 비어 있음 | `exportBarcodes`를 추출 전에 호출함 | 내보내기 전에 `parser.getBarcodes(options)`가 데이터를 반환하는지 확인합니다. |

## 자주 묻는 질문
**Q: 이미지 파일에서 바코드를 추출할 수 있나요?**  
A: 예, 라이브러리는 일반 이미지 형식(PNG, JPEG, TIFF)에서 바코드 추출을 지원합니다.

**Q: 어떤 바코드 형식을 인식하나요?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 등 다수. 전체 목록은 API 문서를 참고하십시오.

**Q: 비밀번호로 보호된 PDF를 어떻게 처리하나요?**  
A: 비밀번호를 `Parser` 생성자에 전달합니다: `new Parser(filePath, "password")`.

**Q: 체험판이 프로덕션 테스트에 충분한가요?**  
A: 체험판은 전체 기능을 제공하지만 추출된 데이터에 워터마크가 추가됩니다. 프로덕션에서는 상용 라이선스를 획득하십시오.

**Q: PDF에 QR 및 선형 바코드가 모두 포함된 경우는 어떻게 하나요?**  
A: 여러 `BarcodeOptions` 인스턴스를 만들거나 유형 배열을 전달하여 한 번에 모든 필요한 형식을 스캔합니다.

---

**마지막 업데이트:** 2026-10-12  
**테스트 환경:** GroupDocs.Parser 25.5  
**작성자:** GroupDocs  

## 리소스
- [GroupDocs.Parser Java 문서](https://docs.groupdocs.com/parser/java/)
- [API 레퍼런스](https://reference.groupdocs.com/parser/java)
- [GroupDocs.Parser 다운로드](https://releases.groupdocs.com/parser/java/)
- [GitHub 저장소](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [무료 지원 포럼](https://forum.groupdocs.com/c/parser)
- [임시 라이선스 신청](https://purchase.groupdocs.com/temporary-license/)

## 관련 튜토리얼
- [Java용 GroupDocs.Parser에서 PDF 바코드 추출](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Java용 GroupDocs.Parser로 URL에서 PDF 로드하는 방법](/parser/java/document-loading/)
- [Java에서 GroupDocs.Parser로 PDF 양식 데이터 추출](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)