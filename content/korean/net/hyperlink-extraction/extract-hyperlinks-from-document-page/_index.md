---
title: 문서 페이지에서 하이퍼링크 추출
linktitle: 문서 페이지에서 하이퍼링크 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 하이퍼링크를 추출하는 방법을 알아보세요. C#에서 하이퍼링크 추출을 위한 단계별 가이드입니다.
weight: 11
url: /ko/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---

# 문서 페이지에서 하이퍼링크 추출

## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서에서 하이퍼링크를 단계별로 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 다양한 문서 형식을 구문 분석하고 텍스트, 메타데이터 및 기타 요소를 추출할 수 있는 강력한 라이브러리입니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- Visual Studio: 개발 컴퓨터에 Visual Studio를 설치합니다.
-  GroupDocs.Parser 라이브러리: GroupDocs.Parser 라이브러리를 다운로드하고 참조합니다. 당신은 그것을 얻을 수 있습니다[여기](https://releases.groupdocs.com/parser/net/).
- 샘플 문서: 테스트용 하이퍼링크가 포함된 샘플 문서(예: DOCX, PDF)를 준비합니다.

## 네임스페이스 가져오기
먼저 GroupDocs.Parser 기능을 사용하는 데 필요한 네임스페이스를 포함합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 인스턴스 생성
 인스턴스화`Parser` 클래스를 샘플 문서의 경로로 바꿉니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // 코드는 여기에 있습니다...
}
```
## 2단계: 하이퍼링크 추출 지원 확인
계속하기 전에 문서가 하이퍼링크 추출을 지원하는지 확인하세요.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## 3단계: 문서 정보 검색
문서에 대한 기본 정보를 확인하고 페이지가 포함되어 있는지 확인하세요.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 4단계: 문서 페이지 반복
문서의 각 페이지를 반복합니다.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // 현재 페이지에서 하이퍼링크 추출
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // 추출된 하이퍼링크 반복
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // 가독성을 위해 빈 줄
    }
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서에서 하이퍼링크를 추출하는 기본 사항을 다루었습니다. 파서를 초기화하고, 하이퍼링크 지원을 확인하고, 문서 정보를 검색하고, 문서 페이지를 반복하여 하이퍼링크를 효율적으로 추출하는 방법을 배웠습니다.

## FAQ
### 다양한 문서 형식에서 하이퍼링크를 추출할 수 있나요?
예, GroupDocs.Parser는 하이퍼링크 추출을 위해 DOCX, PDF, PPTX 등과 같은 다양한 형식을 지원합니다.
### GroupDocs.Parser는 기존 .NET 응용 프로그램에 쉽게 통합됩니까?
물론, GroupDocs.Parser는 간단하게 설계되었으며 .NET 프로젝트에 쉽게 통합될 수 있습니다.
### GroupDocs.Parser를 사용하여 하이퍼링크와 함께 다른 메타데이터를 추출할 수 있습니까?
예, 하이퍼링크 외에도 이 라이브러리를 사용하여 문서에서 텍스트, 이미지 및 메타데이터를 추출할 수 있습니다.
### GroupDocs.Parser는 암호화되거나 암호로 보호된 문서를 처리합니까?
GroupDocs.Parser는 비밀번호가 제공되면 비밀번호로 보호된 문서를 구문 분석할 수 있습니다.
### 구매하기 전에 테스트할 수 있는 평가판이 있나요?
 예, 무료 평가판을 다운로드할 수 있습니다[여기](https://releases.groupdocs.com/).