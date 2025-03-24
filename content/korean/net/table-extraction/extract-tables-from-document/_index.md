---
title: 문서에서 테이블 추출
linktitle: 문서에서 테이블 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 Groupdocs.Parser를 사용하여 문서에서 테이블을 추출하는 방법을 알아보세요. 이 기능 통합에 대한 자세한 가이드를 따라가세요.
weight: 10
url: /ko/net/table-extraction/extract-tables-from-document/
---

# 문서에서 테이블 추출

## 소개
.NET용 Groupdocs.Parser는 문서 구문 분석을 용이하게 하는 포괄적인 라이브러리로, 이를 통해 문서에서 테이블, 텍스트, 메타데이터 등과 같은 중요한 정보를 추출할 수 있습니다. 이 튜토리얼에서는 특히 Groupdocs.Parser API를 사용하여 문서에서 테이블을 추출하는 데 중점을 둡니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- 시스템에 Visual Studio가 설치되어 있습니다.
- .NET Framework 또는 .NET Core가 설치되어 있습니다.
- C# 프로그래밍에 대한 기본 지식.

## 네임스페이스 가져오기
먼저 Groupdocs.Parser 클래스 및 메서드에 액세스하는 데 필요한 네임스페이스를 가져와야 합니다.
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
 새 인스턴스를 초기화합니다.`Parser` 샘플 문서의 경로를 제공하여 클래스를 생성합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // 귀하의 코드는 여기에 있습니다
}
```
## 2단계: 테이블 추출 지원 확인
 문서가 다음을 사용하여 테이블 추출을 지원하는지 확인하십시오.`Features` 의 재산`Parser` 수업.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## 3단계: 테이블 레이아웃 정의
다음을 사용하여 추출하려는 테이블의 레이아웃을 정의합니다.`TemplateTableLayout`. 문서 구조에 따라 열 너비와 행 높이를 지정합니다.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## 4단계: 테이블 추출 옵션 설정
 만들다`PageTableAreaOptions` 정의된 레이아웃을 사용하여 테이블 추출 방법을 지정합니다.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 5단계: 테이블 추출
 활용`GetTables` 의 방법`Parser` 지정된 옵션을 기반으로 문서에서 테이블을 추출하는 클래스입니다.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## 6단계: 테이블 데이터 반복 및 액세스
추출된 테이블과 해당 행 및 열을 반복하여 셀 데이터에 액세스합니다.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## 결론
이 자습서에서는 .NET용 Groupdocs.Parser를 사용하여 문서에서 테이블을 효율적으로 추출하는 방법을 다루었습니다. 이 라이브러리의 기능을 활용하면 테이블 추출을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.

## FAQ
### Groupdocs.Parser는 다양한 문서 형식을 처리할 수 있습니까?
예, Groupdocs.Parser는 DOCX, PDF, XLSX 등을 포함한 광범위한 문서 형식을 지원합니다.
### .NET용 Groupdocs.Parser에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### Groupdocs.Parser 관련 쿼리에 대한 지원을 받으려면 어떻게 해야 합니까?
 당신은 방문 할 수 있습니다[Groupdocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17) 도움을 위해.
### Groupdocs.Parser 라이센스는 어디서 구매할 수 있나요?
 다음에서 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy).
### 평가 목적으로 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 임시면허를 취득할 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).