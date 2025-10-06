---
title: 문서 페이지에서 테이블 추출
linktitle: 문서 페이지에서 테이블 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 프로그래밍 방식으로 문서에서 테이블을 추출하는 방법을 알아보세요. 이 포괄적인 튜토리얼은 단계별 지침을 제공합니다.
weight: 11
url: /ko/net/table-extraction/extract-tables-from-document-page/
type: docs
---
# 문서 페이지에서 테이블 추출

## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 페이지에서 테이블을 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 PDF, DOCX, XLSX 등과 같은 다양한 문서 형식으로 작업할 수 있는 강력한 라이브러리입니다. 해당 기능을 활용하면 이러한 문서에서 테이블과 같은 구조화된 데이터를 효율적으로 추출할 수 있으며 이를 통해 정보를 프로그래밍 방식으로 조작하고 분석할 수 있습니다.
## 전제 조건
시작하기 전에 다음 사항을 확인하세요.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- C# 및 .NET 개발에 대한 기본 이해.
-  .NET 라이브러리용 GroupDocs.Parser. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/parser/net/).
- 추출용 테이블이 포함된 샘플 문서(PDF, DOCX 등)에 액세스합니다.

## 네임스페이스 가져오기
먼저 C# 프로젝트에서 필요한 네임스페이스를 가져오는 것부터 시작합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## 1단계: 파서 클래스 인스턴스 생성
 인스턴스화`Parser` 샘플 문서에 대한 경로를 제공하여 클래스를 제공합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //귀하의 코드는 여기에 계속됩니다 ...
}
```
## 2단계: 문서 테이블 추출 지원 확인
계속하기 전에 문서가 테이블 추출을 지원하는지 확인하세요.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## 3단계: 테이블 레이아웃 정의
문서에서 추출할 테이블의 레이아웃을 정의합니다. 문서 구조에 따라 열 너비와 행 높이를 지정합니다.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // 열 너비
    new double[] { 325, 340, 365, 395 });         // 행 높이
```
## 4단계: 테이블 추출 옵션 구성
지정된 레이아웃을 사용하여 테이블 추출을 위한 옵션을 만듭니다.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 5단계: 문서 정보 검색
페이지 수를 포함하여 문서에 대한 정보를 가져옵니다.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 6단계: 문서 페이지 반복
문서의 각 페이지를 반복하여 테이블을 추출합니다.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // 현재 페이지에서 테이블 추출
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // 추출된 테이블 반복
    foreach (PageTableArea table in tables)
    {
        // 테이블의 행을 반복합니다.
        for (int row = 0; row < table.RowCount; row++)
        {
            // 테이블의 열을 반복합니다.
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // 테이블 셀 가져오기
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // 테이블 셀의 텍스트를 인쇄합니다.
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 페이지에서 테이블을 추출하는 프로세스를 다루었습니다. 제공된 단계를 따르면 테이블 추출 기능을 .NET 애플리케이션에 원활하게 통합하여 문서 내의 구조화된 데이터를 효율적으로 처리하고 조작할 수 있습니다.

## FAQ
### GroupDocs.Parser는 모든 유형의 문서에서 테이블을 추출할 수 있습니까?
GroupDocs.Parser는 PDF, DOCX, XLSX 등과 같은 다양한 문서 형식을 지원하므로 호환 가능한 파일 형식에서 테이블을 추출할 수 있습니다.
### .NET용 GroupDocs.Parser는 대규모 문서 처리에 적합합니까?
예, GroupDocs.Parser는 대용량 문서를 효율적으로 처리하도록 설계되어 광범위한 데이터 세트를 처리하는 데 적합합니다.
### GroupDocs.Parser는 테이블 추출 중에 서식을 유지합니까?
예, GroupDocs.Parser는 테이블 추출 중에 셀 테두리, 텍스트 스타일, 정렬과 같은 서식 세부 정보를 유지합니다.
### 콘텐츠 기준에 따라 특정 테이블을 추출할 수 있나요?
GroupDocs.Parser는 레이아웃 템플릿이나 추출을 위한 콘텐츠 조건을 기반으로 특정 테이블을 대상으로 하는 유연한 옵션을 제공합니다.
### GroupDocs.Parser는 .NET Core와 호환되나요?
예, GroupDocs.Parser는 .NET Framework 및 .NET Core 환경 모두와 호환됩니다.