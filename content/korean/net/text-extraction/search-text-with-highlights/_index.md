---
title: 하이라이트로 텍스트 검색
linktitle: 하이라이트로 텍스트 검색
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 텍스트를 검색하고 강조 표시하는 방법을 알아보세요. 귀중한 통찰력을 효율적으로 추출하세요.
weight: 24
url: /ko/net/text-extraction/search-text-with-highlights/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 내에서 텍스트를 검색하고 검색 결과를 강조 표시하는 방법을 살펴보겠습니다. GroupDocs.Parser는 다양한 문서 형식으로 작업하고 텍스트, 메타데이터 등을 추출할 수 있는 강력한 라이브러리입니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Parser: 다음에서 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/parser/net/).
2. IDE: .NET 개발을 위해 Visual Studio 또는 선호하는 IDE를 사용하세요.
3. 샘플 파일: 텍스트 검색을 위한 샘플 문서(예: PDF, DOCX)를 준비합니다.

## 네임스페이스 가져오기
먼저 .NET 프로젝트에서 필요한 네임스페이스를 가져오는 것부터 시작합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 인스턴스 생성
 인스턴스화부터 시작하세요.`Parser` 샘플 파일 경로가 포함된 클래스:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 여기에 귀하의 코드가 있습니다
}
```
## 2단계: 하이라이트 옵션 정의
 지정`HighlightOptions` 검색 결과를 강조 표시하는 방법을 구성합니다. 예를 들어 컨텍스트 창을 15자로 설정하면 다음과 같습니다.
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## 3단계: 텍스트 검색
이제 문서 내에서 텍스트 검색을 수행합니다. 검색하려는 키워드를 입력하세요(예: "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## 4단계: 검색 결과 처리
검색 결과를 반복하고 하이라이트와 함께 찾은 텍스트를 표시합니다.
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 내의 텍스트를 검색하고 검색 결과를 강조 표시하는 방법을 배웠습니다. 이 기능은 .NET 애플리케이션에서 텍스트 추출 및 분석에 매우 유용할 수 있습니다.

## FAQ
### GroupDocs.Parser는 다양한 문서 형식을 처리하는 데 적합합니까?
예, GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Parser를 사용하여 문서에서 메타데이터를 추출할 수 있습니까?
전적으로! GroupDocs.Parser를 사용하면 문서에서 메타데이터, 텍스트 및 구조화된 데이터를 추출할 수 있습니다.
### GroupDocs.Parser에 대한 지원이나 질문은 어디서 찾을 수 있나요?
 당신은 방문 할 수 있습니다[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17) 지원 관련 문의사항이 있는 경우
### GroupDocs.Parser에 대한 무료 평가판이 있습니까?
 예, 액세스할 수 있습니다[무료 시험판](https://releases.groupdocs.com/) GroupDocs.Parser의 기능을 평가합니다.
### GroupDocs.Parser 라이센스를 어떻게 구매할 수 있나요?
 다음에서 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy) 임시면허도 취득하고[여기](https://purchase.groupdocs.com/temporary-license/).