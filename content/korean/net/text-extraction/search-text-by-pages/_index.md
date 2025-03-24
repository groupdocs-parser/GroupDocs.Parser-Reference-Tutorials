---
title: 페이지별로 텍스트 검색
linktitle: 페이지별로 텍스트 검색
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 페이지별로 텍스트를 검색하는 방법을 알아보세요. .NET 애플리케이션의 문서에서 특정 콘텐츠를 효율적으로 추출합니다.
weight: 22
url: /ko/net/text-extraction/search-text-by-pages/
---
## 소개
.NET 개발 세계에서는 문서에서 텍스트를 효율적으로 구문 분석하고 추출하는 것이 중요한 작업입니다. .NET용 GroupDocs.Parser는 다양한 문서 형식으로 작업할 수 있는 강력한 기능을 제공하므로 개발자는 특정 콘텐츠를 원활하게 검색하고 추출할 수 있습니다. 이 자습서에서는 GroupDocs.Parser를 활용하여 .NET 응용 프로그램에서 페이지별로 텍스트를 검색하는 과정을 안내합니다.
## 전제 조건
이 튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
- C# 및 .NET 프레임워크에 대한 기본 이해
- 시스템에 설치된 Visual Studio
-  .NET 라이브러리용 GroupDocs.Parser가 설치되었습니다(다운로드:[여기](https://releases.groupdocs.com/parser/net/))
- 검색 기능 테스트를 위한 샘플 파일
## 네임스페이스 가져오기
먼저, GroupDocs.Parser 기능에 액세스하려면 프로젝트에 필요한 네임스페이스를 포함하세요.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 클래스 인스턴스 생성
 인스턴스화부터 시작하세요.`Parser` 샘플 파일 경로가 포함된 클래스:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // 귀하의 코드는 여기에 있습니다
}
```
## 2단계: 페이지 번호로 텍스트 검색
 활용`Search` 페이지 번호와 함께 문서 내에서 특정 키워드를 찾는 방법:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## 3단계: 검색 지원 확인
문서 유형에 대해 검색 작업이 지원되는지 확인하십시오.
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## 4단계: 검색 결과 반복
검색 결과를 반복하여 색인된 위치, 페이지 번호 및 발견된 텍스트를 검색합니다.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 페이지별로 텍스트 검색을 구현하는 방법을 살펴보았습니다. 다음 단계를 수행하면 문서 구문 분석 및 검색 기능을 .NET 애플리케이션에 효율적으로 통합할 수 있습니다.

## FAQ
### GroupDocs.Parser는 다양한 문서 형식과 호환됩니까?
예, GroupDocs.Parser는 DOCX, PDF, XLSX, PPTX 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Parser를 사용하여 문서에서 이미지와 메타데이터를 추출할 수 있습니까?
물론, GroupDocs.Parser를 사용하면 문서에서 이미지, 메타데이터 및 텍스트를 추출할 수 있습니다.
### GroupDocs.Parser에 대한 자세한 문서는 어디서 찾을 수 있나요?
 문서에 액세스할 수 있습니다.[여기](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser의 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 임시 라이센스를 요청할 수 있습니다[여기](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser에 대한 지원은 어디서 받을 수 있나요?
 지원 및 토론을 원하시면 GroupDocs.Parser 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/parser/17).