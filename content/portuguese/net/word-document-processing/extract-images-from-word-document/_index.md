---
title: Extraia imagens de um documento do Word
linktitle: Extraia imagens de um documento do Word
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair imagens de um documento do Word usando GroupDocs.Parser for .NET. Este tutorial fornece orientação passo a passo para integrar imagens ao seu .NET.
weight: 11
url: /pt/net/word-document-processing/extract-images-from-word-document/
type: docs
---
# Extraia imagens de um documento do Word

## Introdução
Neste tutorial, você aprenderá como extrair imagens de um documento do Word usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma biblioteca .NET poderosa que permite analisar e extrair texto, metadados, imagens e muito mais de vários formatos de documentos, incluindo Word (DOCX).
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos configurados:
- Visual Studio instalado em sua máquina.
- Conhecimento básico de programação C#.
- Biblioteca GroupDocs.Parser para .NET instalada. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/parser/net/).
## Importar namespaces
Primeiro, você precisa importar os namespaces necessários em seu projeto C# para usar as funcionalidades GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Agora, vamos dividir o processo de extração de imagens de um documento Word em etapas simples:
## Etapa 1: crie uma instância da classe analisador
 Você começará criando uma instância do`Parser`class, fornecendo o caminho para o seu documento do Word como entrada.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // O código para extração de imagem vai aqui
}
```
## Etapa 2: extrair imagens do documento do Word
 A seguir, use o`GetImages()` método do`Parser` objeto para extrair imagens do documento.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Etapa 3: definir opções para salvar imagens
Especifique as opções para salvar as imagens extraídas. Por exemplo, você pode escolher o formato da imagem (por exemplo, PNG) e definir outras configurações.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Etapa 4: iterar sobre as imagens extraídas e salvar
Itere cada imagem extraída e salve-a em um arquivo usando as opções especificadas.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Salve a imagem em um arquivo PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Conclusão
Neste tutorial, você aprendeu como extrair imagens de um documento do Word usando GroupDocs.Parser for .NET. Seguindo essas etapas, você pode integrar facilmente recursos de análise de documentos e extração de imagens em seus aplicativos .NET.

## Perguntas frequentes
### O GroupDocs.Parser pode extrair imagens de outros formatos de documentos além do Word?
Sim, GroupDocs.Parser oferece suporte a vários formatos de documentos, incluindo PDF, PowerPoint, Excel e muito mais.
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode obter uma licença temporária para fins de teste em[aqui](https://purchase.groupdocs.com/temporary-license/).
### Onde posso encontrar mais documentação sobre GroupDocs.Parser for .NET?
 Você pode consultar a documentação completa[aqui](https://tutorials.groupdocs.com/parser/net/).
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode explorar os recursos do GroupDocs.Parser com uma avaliação gratuita disponível[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte ou fazer perguntas relacionadas ao GroupDocs.Parser?
 Você pode postar suas dúvidas no[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).