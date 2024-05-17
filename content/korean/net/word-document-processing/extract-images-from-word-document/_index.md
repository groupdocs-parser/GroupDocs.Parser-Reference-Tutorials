---
title: Word 문서에서 이미지 추출
linktitle: Word 문서에서 이미지 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 Word 문서에서 이미지를 추출하는 방법을 알아보세요. 이 자습서에서는 이미지를 .NET에 통합하기 위한 단계별 지침을 제공합니다.
type: docs
weight: 11
url: /ko/net/word-document-processing/extract-images-from-word-document/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 Word 문서에서 이미지를 추출하는 방법을 배웁니다. GroupDocs.Parser는 Word(DOCX)를 포함한 다양한 문서 형식에서 텍스트, 메타데이터, 이미지 등을 구문 분석하고 추출할 수 있는 강력한 .NET 라이브러리입니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 설정되어 있는지 확인하세요.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- C# 프로그래밍에 대한 기본 지식.
- .NET 라이브러리용 GroupDocs.Parser가 설치되었습니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/parser/net/).
## 네임스페이스 가져오기
먼저 GroupDocs.Parser 기능을 사용하려면 C# 프로젝트에서 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
이제 Word 문서에서 이미지를 추출하는 과정을 간단한 단계로 나누어 보겠습니다.
## 1단계: 파서 클래스 인스턴스 생성
 먼저`Parser`클래스, Word 문서에 대한 경로를 입력으로 제공합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // 이미지 추출 코드는 여기에 있습니다.
}
```
## 2단계: Word 문서에서 이미지 추출
 다음으로`GetImages()` 의 방법`Parser` 문서에서 이미지를 추출하는 개체입니다.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3단계: 이미지 저장 옵션 정의
추출된 이미지를 저장하기 위한 옵션을 지정합니다. 예를 들어 이미지 형식(예: PNG)을 선택하고 기타 설정을 구성할 수 있습니다.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 4단계: 추출된 이미지를 반복하고 저장
추출된 각 이미지를 반복하고 지정된 옵션을 사용하여 파일에 저장합니다.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // 이미지를 PNG 파일로 저장
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 Word 문서에서 이미지를 추출하는 방법을 배웠습니다. 다음 단계를 수행하면 문서 구문 분석 및 이미지 추출 기능을 .NET 애플리케이션에 쉽게 통합할 수 있습니다.

## FAQ
### GroupDocs.Parser는 Word 이외의 다른 문서 형식에서 이미지를 추출할 수 있습니까?
예, GroupDocs.Parser는 PDF, PowerPoint, Excel 등을 포함한 다양한 문서 형식을 지원합니다.
### GroupDocs.Parser의 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 다음에서 테스트 목적으로 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
### .NET용 GroupDocs.Parser에 대한 추가 문서는 어디서 찾을 수 있나요?
 전체 문서를 참조할 수 있습니다.[여기](https://reference.groupdocs.com/parser/net/).
### GroupDocs.Parser에 대한 무료 평가판이 있습니까?
 예, 무료 평가판을 통해 GroupDocs.Parser의 기능을 탐색할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Parser와 관련된 지원을 받거나 질문을 하려면 어떻게 해야 합니까?
 문의사항은 에 게시하실 수 있습니다.[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17).