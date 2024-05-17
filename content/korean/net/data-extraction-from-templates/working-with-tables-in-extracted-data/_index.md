---
title: 추출된 데이터의 테이블 작업
linktitle: 추출된 데이터의 테이블 작업
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 테이블 데이터를 추출하는 방법을 알아보세요. 사전 정의된 템플릿을 사용하여 구조화된 콘텐츠를 효율적으로 구문 분석합니다.
type: docs
weight: 12
url: /ko/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서의 테이블에서 데이터를 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 PDF, DOCX, XLSX 등과 같은 다양한 파일 형식에서 텍스트, 메타데이터 및 구조화된 콘텐츠를 구문 분석하고 추출할 수 있는 강력한 도구입니다. 특히, 미리 정의된 템플릿을 사용하여 테이블 데이터를 효율적으로 추출하는 데 중점을 둘 것입니다.
## 전제 조건
시작하기 전에 다음 사항이 준비되어 있는지 확인하세요.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- C# 및 .NET 프레임워크에 대한 기본 이해.
- NuGet 패키지 관리자를 통해 설치된 GroupDocs.Parser 라이브러리.

## 네임스페이스 가져오기
GroupDocs.Parser 및 관련 기능을 사용하는 데 필요한 네임스페이스를 가져오는 것부터 시작하세요.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 1단계: 테이블 템플릿 만들기
테이블에서 데이터를 추출하려면 먼저 추출하려는 테이블의 구조를 나타내는 템플릿을 정의합니다. 문서 내에서 테이블의 위치와 크기를 지정합니다.
```csharp
// 테이블 매개변수 정의(위치 및 크기)
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// 매개변수가 포함된 테이블 템플릿 만들기
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## 2단계: 템플릿 정의
정의한 테이블 템플릿을 포함하는 템플릿을 만듭니다. 이 템플릿은 테이블 데이터를 추출할 때 무엇을 찾아야 하는지 파서에게 안내합니다.
```csharp
// 테이블을 사용하여 템플릿 만들기
Template template = new Template(new TemplateItem[] { table });
```
## 3단계: 문서 구문 분석 및 테이블 데이터 추출
정의한 템플릿을 사용하여 특정 문서를 구문 분석하려면 GroupDocs.Parser의 Parser 클래스를 활용하세요.
```csharp
// 샘플 파일의 경로를 지정하세요.
string filePath = "YourSampleFile.pdf";
// Parser 클래스의 인스턴스 생성
using (Parser parser = new Parser(filePath))
{
    // 템플릿을 기준으로 문서를 구문 분석합니다.
    DocumentData data = parser.ParseByTemplate(template);
    // 추출된 모든 데이터에 대해 반복
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // 추출된 필드가 테이블인지 확인
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // 테이블 행 반복
        for (int row = 0; row < area.RowCount; row++)
        {
            // 테이블 열 반복
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // 셀 값 가져오기
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // 셀 값(또는 null인 경우 빈 문자열)을 인쇄합니다.
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // 열 사이에 탭 공백 인쇄
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            // 각 행을 인쇄한 후 다음 줄로 이동
            Console.WriteLine();
        }
    }
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서에서 테이블 데이터를 추출하는 방법을 살펴보았습니다. 템플릿을 정의하고 구문 분석 방법을 활용함으로써 개발자는 다양한 파일 형식에서 테이블과 같은 구조화된 데이터를 효율적으로 추출할 수 있습니다.

## FAQ
### GroupDocs.Parser는 모든 문서 형식과 호환됩니까?
예, GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX 등을 포함한 광범위한 파일 형식을 지원합니다.
### 문서 내 특정 영역의 데이터를 추출할 수 있나요?
물론 추출을 위해 문서 내의 특정 영역(예: 테이블)을 대상으로 하는 템플릿을 정의할 수 있습니다.
### GroupDocs.Parser는 대용량 문서에 적합합니까?
예, GroupDocs.Parser는 대용량 문서를 효율적으로 처리하도록 최적화되어 개발자가 데이터를 원활하게 추출할 수 있도록 해줍니다.
### GroupDocs.Parser는 구조화된 데이터와 함께 텍스트 추출을 지원합니까?
예, 구조화된 데이터 추출(예: 테이블) 외에도 GroupDocs.Parser는 문서에서 일반 텍스트와 메타데이터를 추출할 수 있습니다.
### GroupDocs.Parser 통합에 대한 지원을 받으려면 어떻게 해야 합니까?
 지원 및 토론을 원하시면 GroupDocs 커뮤니티 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/parser/17).