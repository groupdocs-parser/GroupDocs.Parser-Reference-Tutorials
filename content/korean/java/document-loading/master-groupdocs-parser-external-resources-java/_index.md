---
date: '2025-12-29'
description: GroupDocs.Parser for Java를 사용하여 문서에서 이미지를 추출하고 리소스를 필터링하는 방법을 배웁니다. 이
  가이드는 구성, 사용자 정의 핸들러 및 실용적인 예제를 다룹니다.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: GroupDocs.Parser Java로 문서에서 이미지 추출하기 – 가이드
type: docs
url: /ko/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# 문서에서 이미지 추출 및 GroupDocs.Parser Java를 사용한 리소스 필터링

문서에서 이미지를 추출하는 것은 문서 처리 파이프라인을 구축할 때 일반적인 요구 사항입니다. 이 튜토리얼에서는 GroupDocs.Parser for Java를 사용하여 **문서에서 이미지를 추출하는 방법**을 배우고, **리소스를 필터링하는 방법**도 배워 필요하지 않은 파일이 로드되지 않도록 합니다. 라이브러리 설정, 사용자 정의 `ExternalResourceHandler` 생성, 필터링 로직 적용을 통해 애플리케이션을 빠르고 안전하게 유지하는 방법을 단계별로 안내합니다.

## 빠른 답변
- **GroupDocs.Parser는 무엇을 하나요?** 다양한 문서 형식을 파싱하고 텍스트, 이미지 및 기타 삽입된 리소스에 접근할 수 있게 해줍니다.  
- **원하지 않는 이미지를 건너뛸 수 있나요?** 네—사용자 정의 `ExternalResourceHandler`를 구현하면 로드할 리소스를 직접 결정할 수 있습니다.  
- **필요한 Maven 버전은 무엇인가요?** GroupDocs.Parser Java 25.5 이상을 사용하세요.  
- **라이선스가 필요합니까?** 평가용 무료 체험이 가능하지만, 프로덕션에서는 영구 라이선스가 필요합니다.  
- **이 접근 방식은 스레드‑안전한가요?** 파싱 객체는 스레드 간에 공유되지 않으며, 스레드당 새로운 `Parser` 인스턴스를 생성해야 합니다.

## “문서에서 이미지 추출”이란 무엇인가요?
문서에 삽입된 사진, 차트 또는 기타 미디어가 포함된 경우, “문서에서 이미지 추출”은 해당 바이너리 파일을 프로그래밍 방식으로 가져와 원본 파일 외부에 저장, 표시 또는 추가 처리할 수 있도록 하는 것을 의미합니다.

## 이미지 추출 시 리소스를 필터링하는 이유는?
- 큰 파일이나 관련 없는 파일을 무시하여 메모리 사용량을 줄입니다.  
- 잠재적으로 위험한 콘텐츠 로드를 방지하여 보안을 향상시킵니다.  
- 많은 삽입 객체가 포함된 대용량 문서의 경우 처리 속도를 높입니다.

## 사전 요구 사항

- **Java Development Kit (JDK)** – 버전 8 이상.  
- **Maven** – 의존성 관리를 위해 필요합니다.  
- Java I/O 및 예외 처리에 대한 기본적인 이해.

## GroupDocs.Parser for Java 설정

`pom.xml`에 GroupDocs 저장소와 파서 의존성을 추가합니다:

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

또는 최신 버전을 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/)에서 다운로드하세요.

### 라이선스 획득
- **Free Trial** – 비용 없이 핵심 기능을 탐색합니다.  
- **Temporary License** – 평가 기간 동안 전체 기능을 활성화합니다.  
- **Purchased License** – 상용 배포에 필요합니다.

## 이미지 추출 시 리소스를 필터링하는 방법

### 단계 1: 사용자 정의 핸들러 만들기
`ExternalResourceHandler`를 상속하는 클래스를 정의합니다. `onLoading` 메서드 안에서 유지할 리소스를 결정합니다.

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

### 단계 2: 핸들러와 함께 `ParserSettings` 구성
`Handler` 인스턴스를 `ParserSettings`에 전달하고 문서를 열 때 사용합니다.

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

### 단계 3: 필터링 로직 미세 조정
이미지 크기, 형식 또는 URI 패턴 등 보다 정교한 규칙이 필요하면 `onLoading` 메서드를 해당 방식으로 확장합니다:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## 실용적인 적용 사례

1. **Document Management Systems** – 스캔된 계약서에서 필요한 이미지만 추출해 썸네일을 생성합니다.  
2. **Data Extraction Services** – 장식용 그래픽을 건너뛰고 유용한 데이터가 포함된 차트에 집중합니다.  
3. **Web Scraping Tools** – HTML 기반 문서에서 의미 있는 미디어를 가져오면서 추적 픽셀을 필터링합니다.

## 성능 고려 사항
- **Filter early**: 리소스를 반복하기 전에 사용자 정의 핸들러를 적용해 원치 않는 데이터를 메모리에 로드하지 않도록 합니다.  
- **Dispose promptly**: `try‑with‑resources` (`try (Parser parser = …)`)를 사용해 네이티브 리소스를 즉시 해제합니다.  
- **Async processing**: 대량 배치의 경우 병렬 스트림으로 문서를 처리하되 각 `Parser` 인스턴스는 단일 스레드에만 사용하도록 합니다.

## 일반적인 문제 및 해결책
| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| 이미지가 반환되지 않음 | 핸들러가 모든 리소스를 실수로 건너뛰는 경우 | `if` 조건을 확인하고 `args.setSkipped(true)`가 원하지 않는 URI에만 호출되는지 확인합니다. |
| 대용량 파일에서 `IOException` 발생 | 힙 메모리 부족 | JVM 힙(`-Xmx2g`)을 늘리거나 페이지를 더 작은 청크로 처리합니다. |
| 라이선스 인식 안 됨 | 프로덕션 코드에 시험용 DLL 사용 | `License.setLicense("path/to/license")`를 통해 올바른 라이선스 파일 경로를 적용합니다. |

## 자주 묻는 질문

**Q: 사용자 정의 `ExternalResourceHandler`를 사용하는 주요 목적은 무엇인가요?**  
A: 외부 리소스 로드를 제어할 수 있어 불필요한 파일을 필터링함으로써 보안과 성능을 향상시킵니다.

**Q: GroupDocs.Parser for Java를 라이선스 없이 사용할 수 있나요?**  
A: 네, 무료 체험이 가능하지만 일부 고급 기능은 임시 또는 구매 라이선스를 얻을 때까지 제한될 수 있습니다.

**Q: GroupDocs.Parser를 사용한 파싱 중 예외를 어떻게 처리하나요?**  
A: `IOException` 및 기타 특정 예외에 대해 `try‑catch` 블록으로 파싱 호출을 감싸 오류를 우아하게 처리합니다.

**Q: 리소스를 필터링할 때 흔히 발생하는 실수는 무엇인가요?**  
A: 잘못된 URI 검사로 필요한 파일을 건너뛰는 경우가 있습니다; 로깅이나 브레이크포인트를 사용해 조건을 검증하세요.

**Q: GroupDocs.Parser for Java로 HTML이 아닌 문서를 파싱할 수 있나요?**  
A: 물론입니다—GroupDocs.Parser는 PDF, Word, Excel, PowerPoint 등 다양한 형식을 지원합니다.

## 다음 단계
라이브러리를 더 깊이 탐색하려면 [API Reference](https://reference.groupdocs.com/parser/java) 를 살펴보거나 `ParserSettings.setDetectTables(true)`와 같은 추가 설정을 실험해 보세요.

---

**Last Updated:** 2025-12-29  
**Tested With:** GroupDocs.Parser 25.5 for Java  
**Author:** GroupDocs  

**Resources**  
- **Documentation:** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API Reference:** [API Details](https://reference.groupdocs.com/parser/java)  
- **Downloads:** [Latest Versions](https://releases.groupdocs.com/parser/java/)