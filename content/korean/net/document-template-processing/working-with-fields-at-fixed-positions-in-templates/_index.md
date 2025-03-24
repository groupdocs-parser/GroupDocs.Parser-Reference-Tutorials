---
title: 템플릿의 고정 위치에 있는 필드 작업
linktitle: 템플릿의 고정 위치에 있는 필드 작업
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 데이터를 추출하는 방법을 알아보세요. 코드 예제가 포함된 종합 튜토리얼입니다.
weight: 11
url: /ko/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---

# 템플릿의 고정 위치에 있는 필드 작업

## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 템플릿 내의 고정 위치에 있는 필드로 작업하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 PDF, Word, Excel 등과 같은 다양한 문서 형식에서 데이터를 추출할 수 있는 강력한 문서 구문 분석 라이브러리입니다. 특히, 고정된 위치를 기반으로 타겟 정보를 추출하기 위해 템플릿 필드를 정의하고 활용하는 데 중점을 둘 것입니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- C# 및 .NET 개발에 대한 기본 이해.
- 시스템에 Visual Studio가 설치되어 있습니다.
- .NET 라이브러리용 GroupDocs.Parser가 설치되었습니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/parser/net/).
- 테스트용 샘플 문서 파일입니다.

## 네임스페이스 가져오기
C# 프로젝트에 필요한 네임스페이스를 포함하는 것부터 시작하세요.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 1단계: 템플릿 필드 정의
먼저 템플릿 내에서 위치가 고정된 필드를 정의합니다. 이 필드는 데이터가 추출될 영역을 나타냅니다.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
여기:
- `Rectangle` 필드의 위치와 크기를 지정합니다.
- `Point(35, 135)` 왼쪽 위 모서리 좌표를 나타냅니다.
- `Size(100, 10)` 필드의 너비와 높이를 정의합니다.
- `"FromCompany"` 이 필드에 할당된 이름입니다.
## 2단계: 템플릿 만들기
정의된 필드를 사용하여 템플릿을 구성합니다.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 그만큼`Template` 객체는 정의된 필드를 보유합니다.
## 3단계: 템플릿을 사용하여 문서 구문 분석
 인스턴스화`Parser` 클래스를 대상 문서 경로로 지정한 다음 생성된 템플릿을 사용하여 문서를 구문 분석합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // 추출된 데이터를 통해 반복
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
여기:
- `Parser` 샘플 문서 파일 경로로 초기화됩니다.
- `ParseByTemplate` 메소드는 제공된 템플릿을 기반으로 데이터를 추출하는 데 사용됩니다.
-  추출된 데이터는 다음을 사용하여 액세스됩니다.`DocumentData`여기서 각 항목은 정의된 필드에 해당합니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 템플릿의 고정 위치에 있는 필드로 작업하는 프로세스를 다루었습니다. 특정 필드 위치로 템플릿을 정의함으로써 개발자는 다양한 문서 형식에서 대상 데이터를 정확하게 추출할 수 있습니다.

## FAQ
### GroupDocs.Parser는 모든 문서 형식과 호환됩니까?
 GroupDocs.Parser는 PDF, Microsoft Word, Excel, PowerPoint 등을 포함한 광범위한 파일 형식을 지원합니다. 다음을 참조하세요.[선적 서류 비치](https://tutorials.groupdocs.com/parser/net/) 자세한 목록을 보려면.
### GroupDocs.Parser의 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 다음에서 테스트 목적으로 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser에 대한 지원은 어디서 찾을 수 있나요?
 기술 지원 및 토론을 원하시면 다음을 방문하십시오.[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17).
### 구매하기 전에 GroupDocs.Parser를 사용해 볼 수 있나요?
 예, 무료 평가판을 통해 라이브러리를 탐색할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Parser 라이센스를 어떻게 구매하나요?
 라이센스를 구입하려면 다음을 방문하십시오.[구매 페이지](https://purchase.groupdocs.com/buy).