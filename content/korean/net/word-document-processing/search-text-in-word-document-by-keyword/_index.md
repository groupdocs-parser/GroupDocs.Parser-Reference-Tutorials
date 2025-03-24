---
title: 키워드로 Word 문서의 텍스트 검색
linktitle: 키워드로 Word 문서의 텍스트 검색
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 Word 문서에서 텍스트를 검색하는 방법을 알아보세요. 특정 키워드를 효율적으로 추출합니다.
weight: 18
url: /ko/net/word-document-processing/search-text-in-word-document-by-keyword/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 C#을 사용하여 Word 문서 내에서 특정 텍스트를 검색하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 Word 문서를 포함한 다양한 문서 형식에서 텍스트와 메타데이터를 추출할 수 있는 강력한 라이브러리입니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
1. 개발 환경: Visual Studio 또는 다른 호환 IDE를 설치합니다.
2.  GroupDocs.Parser 라이브러리: 다음에서 .NET 라이브러리용 GroupDocs.Parser를 다운로드하고 설치합니다.[웹사이트](https://releases.groupdocs.com/parser/net/).
3. 샘플 Word 문서: 텍스트 검색에 사용할 샘플 Word 문서를 준비합니다.

## 네임스페이스 가져오기
C# 프로젝트에서 필요한 네임스페이스를 가져오는 것부터 시작하세요.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## 1단계: 파서 클래스 인스턴스 생성
 먼저,`Parser` 샘플 Word 문서의 경로를 전달하여 클래스를 생성합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // 코드는 여기에 표시됩니다.
}
```
## 2단계: 키워드 검색
 다음으로`Search` 의 방법`Parser` 문서 내에서 특정 키워드를 검색하는 클래스입니다.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 바꾸다`"keyword"` 문서 내에서 검색하려는 텍스트를 사용하세요.
## 3단계: 검색 결과 반복
 다음을 사용하여 검색 결과를 반복합니다.`foreach` 각각에 액세스하는 루프`SearchResult` 물체.
```csharp
foreach (SearchResult result in searchResults)
{
    //각 검색 결과를 처리하는 코드
}
```
## 4단계: 검색 결과 세부 정보에 액세스
 루프 내에서 다음을 사용하여 각 검색 결과의 위치와 텍스트에 액세스할 수 있습니다.`Position` 그리고`Text` 의 속성`SearchResult` 물체.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
이 코드 조각은 색인(`Position`) 및 발견된 텍스트(`Text`) 각 검색 결과를 콘솔에 보냅니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 Word 문서 내에서 특정 텍스트를 검색하는 방법을 배웠습니다. 이 라이브러리는 다양한 문서 형식의 콘텐츠를 프로그래밍 방식으로 추출하고 조작하는 편리한 방법을 제공합니다.

## FAQ
### GroupDocs.Parser는 Word 이외의 다른 문서 형식을 처리할 수 있습니까?
예, GroupDocs.Parser는 PDF, Excel, PowerPoint 등을 포함한 광범위한 형식을 지원합니다.
### GroupDocs.Parser는 .NET Core와 호환되나요?
예, GroupDocs.Parser는 .NET Framework 및 .NET Core 모두와 호환됩니다.
### GroupDocs.Parser에 대한 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 임시 라이센스를 요청할 수 있습니다.[GroupDocs 구매 페이지](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser에 대한 추가 지원이나 질문은 어디서 찾을 수 있나요?
 방문하다[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17) 커뮤니티 지원 및 토론을 위해.
### 구매하기 전에 GroupDocs.Parser를 무료로 사용해 볼 수 있나요?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[GroupDocs 릴리스 페이지](https://releases.groupdocs.com/).