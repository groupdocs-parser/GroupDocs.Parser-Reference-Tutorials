---
title: 키워드로 텍스트 검색
linktitle: 키워드로 텍스트 검색
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 키워드로 텍스트를 검색하는 방법을 알아보세요. 관련 콘텐츠를 쉽고 효율적으로 추출하세요.
weight: 21
url: /ko/net/text-extraction/search-text-by-keyword/
type: docs
---
# 키워드로 텍스트 검색

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Parser를 사용하여 문서 내에서 키워드로 텍스트를 검색하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 PDF, Microsoft Office 문서 등과 같은 다양한 파일 형식에서 텍스트, 메타데이터 및 기타 정보를 추출할 수 있는 강력한 라이브러리입니다. 대량의 텍스트 데이터를 처리하는 애플리케이션에서는 이러한 문서 내에서 특정 키워드를 검색하는 것이 필수적일 수 있습니다.
## 전제 조건
시작하기 전에 다음이 설정되어 있는지 확인하세요.
1. 개발 환경: Visual Studio 또는 선호하는 .NET IDE.
2.  .NET용 GroupDocs.Parser: 다음에서 라이브러리를 다운로드하세요.[여기](https://releases.groupdocs.com/parser/net/).
3. 샘플 파일에 액세스: 키워드 검색 기능을 테스트하기 위해 샘플 파일(예: PDF, DOCX)을 준비합니다.

## 네임스페이스 가져오기
먼저 프로젝트에 필요한 네임스페이스를 포함해야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## 1단계: 파서 클래스 인스턴스화
 인스턴스를 생성하여 시작합니다.`Parser` 클래스를 선택하고 샘플 파일의 경로를 제공하세요.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 키워드 검색
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // 검색 결과 반복
    foreach (SearchResult result in searchResults)
    {
        //색인과 찾은 텍스트를 인쇄합니다.
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## 2단계: 키워드 검색
 내`using` 차단하고 전화해`Search` 에 대한 방법`parser` 원하는 키워드를 인수로 전달합니다.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 바꾸다`"test"` 문서 내에서 검색하고 싶은 키워드를 입력하세요.
## 3단계: 검색 결과 반복
 다음으로, 다음에서 얻은 검색 결과를 반복합니다.`Search` 을 사용하는 방법`foreach` 고리.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 각각`SearchResult` 물체`result` , 해당 항목에 액세스할 수 있습니다.`Position` (색인) 및`Text` (발견된 텍스트).

## 결론
 이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 내에서 키워드로 텍스트를 쉽게 검색하는 방법을 살펴보았습니다. 활용`Search` 의 방법`Parser` 클래스를 사용하면 특정 검색어를 기반으로 관련 텍스트 조각을 효율적으로 검색할 수 있습니다.

## FAQ
### GroupDocs.Parser는 다양한 문서 형식과 호환됩니까?
예, GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX 등을 포함한 광범위한 파일 형식을 지원합니다.
### GroupDocs.Parser를 사용하여 고급 텍스트 추출 작업을 수행할 수 있습니까?
전적으로! 텍스트 검색 외에도 GroupDocs.Parser는 메타데이터 추출, 구조화된 텍스트 추출 등을 지원합니다.
### GroupDocs.Parser에 대한 자세한 문서는 어디서 찾을 수 있나요?
전체 문서 살펴보기[여기](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser 관련 쿼리에 대한 지원을 받으려면 어떻게 해야 합니까?
 지원 및 토론을 위해 GroupDocs 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/parser/17).
### 구매하기 전에 GroupDocs.Parser를 평가할 수 있는 평가판이 있습니까?
 예, 무료 평가판에 액세스할 수 있습니다[여기](https://releases.groupdocs.com/).