---
title: 원시 모드의 페이지에서 텍스트 추출
linktitle: 원시 모드의 페이지에서 텍스트 추출
second_title: GroupDocs.Parser .NET API
description: 이 포괄적인 튜토리얼에서 .NET용 Groupdocs.Parser를 사용하여 문서 페이지에서 효율적인 텍스트 추출에 대해 알아보세요.
weight: 17
url: /ko/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## 소개
이 자습서에서는 .NET용 Groupdocs.Parser를 사용하여 원시 모드로 문서 페이지에서 텍스트를 추출하는 방법을 배웁니다. 이 라이브러리는 다양한 파일 형식의 콘텐츠를 구문 분석하고 추출하는 효율적인 도구를 제공하므로 개발자는 문서 텍스트 추출을 .NET 애플리케이션에 통합할 수 있습니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
- C# 및 .NET 프로그래밍에 대한 기본 지식
- 컴퓨터에 설치된 Visual Studio
- .NET 라이브러리용 Groupdocs.Parser에 액세스
- 테스트용 샘플 문서 파일

## 네임스페이스 가져오기
C# 프로젝트에 필요한 네임스페이스를 포함하는 것부터 시작하세요.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 초기화
 먼저,`Parser` 샘플 문서 파일의 경로를 제공하여 클래스를 생성합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 여기에 귀하의 코드가 있습니다
}
```
## 2단계: 문서 정보 검색
 다음을 사용하여 문서에 대한 정보를 검색합니다.`GetDocumentInfo()` 방법.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## 3단계: 페이지 반복 및 텍스트 추출
문서의 각 페이지를 반복하고 텍스트 콘텐츠를 추출합니다.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // 페이지에서 텍스트 추출
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 결론
이제 .NET용 Groupdocs.Parser를 사용하여 원시 모드로 문서 페이지에서 텍스트를 추출하는 방법을 배웠습니다. 이는 다양한 파일 형식의 텍스트 콘텐츠를 분석하거나 처리해야 하는 애플리케이션에 강력한 기능이 될 수 있습니다.

## FAQ
### .NET용 Groupdocs.Parser는 모든 파일 형식과 호환됩니까?
Groupdocs.Parser는 PDF, DOCX, XLSX, PPTX, EPUB 등을 포함한 광범위한 파일 형식을 지원합니다.
### 이 라이브러리를 사용하여 텍스트와 함께 메타데이터를 추출할 수 있나요?
예, Groupdocs.Parser를 사용하면 문서에서 텍스트와 메타데이터를 모두 추출할 수 있습니다.
### 테스트에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### Groupdocs.Parser에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
 기술 지원을 받으려면 다음을 방문하세요.[Groupdocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17).
### .NET용 Groupdocs.Parser 라이센스는 어디서 구매할 수 있나요?
 라이센스를 구매하실 수 있습니다[여기](https://purchase.groupdocs.com/buy).