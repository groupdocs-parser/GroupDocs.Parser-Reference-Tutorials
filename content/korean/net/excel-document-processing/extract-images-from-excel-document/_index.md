---
title: Excel 문서에서 이미지 추출
linktitle: Excel 문서에서 이미지 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 Excel 문서에서 이미지를 추출하는 방법을 알아보세요. 코드 예제가 포함된 단계별 가이드입니다.
type: docs
weight: 10
url: /ko/net/excel-document-processing/extract-images-from-excel-document/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 Excel 문서에서 이미지를 추출하는 방법을 알아봅니다. GroupDocs.Parser는 Excel 파일을 포함한 다양한 문서 형식에서 텍스트, 메타데이터 및 이미지를 구문 분석하고 추출할 수 있는 강력한 라이브러리입니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 설정되어 있는지 확인하세요.
1. 개발 환경: Visual Studio 또는 선호하는 .NET 개발 환경을 설치합니다.
2.  GroupDocs.Parser 라이브러리: GroupDocs.Parser 라이브러리를 다운로드하고 참조합니다. 도서관은 다음에서 구할 수 있습니다.[여기](https://releases.groupdocs.com/parser/net/).
3. 샘플 엑셀 파일: 이미지를 추출할 샘플 엑셀 파일을 준비합니다.
## 네임스페이스 가져오기
프로젝트에 필요한 네임스페이스를 포함합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Excel 문서에서 이미지를 추출하려면 다음 단계를 따르세요.
## 1단계: 파서 클래스 인스턴스화
 먼저,`Parser` Excel 파일의 경로를 제공하여 클래스를 지정합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // 여기에 귀하의 코드가 있습니다 ...
}
```
## 2단계: Excel 문서에서 이미지 검색
 사용`GetImages()` Excel 파일에서 이미지를 추출하는 방법.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3단계: 이미지 추출 옵션 정의
추출된 이미지를 저장하기 위한 이미지 형식 및 기타 옵션을 지정합니다. 예를 들어 이미지를 PNG 형식으로 저장하려면 다음을 수행하세요.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 4단계: 이미지 반복 및 저장
추출된 이미지를 반복하고 각 이미지를 파일에 저장합니다.
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
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 Excel 문서에서 이미지를 추출하는 방법을 배웠습니다. 다음 단계를 수행하면 이미지 추출 기능을 .NET 애플리케이션에 효율적으로 통합할 수 있습니다.

## FAQ
### Q: GroupDocs.Parser는 Excel 이외의 다른 문서 형식에서 이미지를 추출할 수 있습니까?
A: 예, GroupDocs.Parser는 Word, PowerPoint, PDF 등을 포함한 광범위한 문서 형식을 지원합니다.
### Q: GroupDocs.Parser 통합에 대한 지원을 받으려면 어떻게 해야 합니까?
 A: 지원 및 도움이 필요하면 다음 사이트를 방문하세요.[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17).
### Q: GroupDocs.Parser는 무료로 사용할 수 있나요?
 답변: GroupDocs.Parser는 무료 평가판을 제공하지만 계속 사용하려면 라이센스를 구입해야 할 수도 있습니다. 을 체크 해봐[가격 및 라이선스](https://purchase.groupdocs.com/buy)세부.
### Q: 라이센스를 구매하기 전에 GroupDocs.Parser를 사용해 볼 수 있습니까?
 A: 네, 가능합니다.[무료 시험판](https://releases.groupdocs.com/) GroupDocs.Parser를 평가합니다.
### Q: GroupDocs.Parser에 대한 자세한 설명서는 어디에서 찾을 수 있습니까?
 A: 포괄적인 내용을 참조하세요.[선적 서류 비치](https://reference.groupdocs.com/parser/net/) GroupDocs.Parser 사용에 대한 자세한 내용은