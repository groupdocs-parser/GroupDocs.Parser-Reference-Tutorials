---
title: Extraia imagens de um documento Excel
linktitle: Extraia imagens de um documento Excel
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair imagens de documentos Excel usando GroupDocs.Parser for .NET. Guia passo a passo com exemplos de código.
type: docs
weight: 10
url: /pt/net/excel-document-processing/extract-images-from-excel-document/
---
## Introdução
Neste tutorial, você aprenderá como extrair imagens de um documento Excel usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma biblioteca poderosa que permite analisar e extrair texto, metadados e imagens de vários formatos de documentos, incluindo arquivos Excel.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos configurados:
1. Ambiente de desenvolvimento: instale o Visual Studio ou qualquer ambiente de desenvolvimento .NET preferido.
2.  Biblioteca GroupDocs.Parser: baixe e faça referência à biblioteca GroupDocs.Parser. Você pode obter a biblioteca em[aqui](https://releases.groupdocs.com/parser/net/).
3. Arquivo Excel de amostra: Prepare um arquivo Excel de amostra do qual deseja extrair imagens.
## Importar namespaces
Inclua os namespaces necessários em seu projeto:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Siga estas etapas para extrair imagens de um documento Excel:
## Etapa 1: instanciar a classe do analisador
 Primeiro, crie uma instância do`Parser` class fornecendo o caminho para seu arquivo Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Seu código aqui...
}
```
## Etapa 2: recuperar imagens do documento Excel
 Use o`GetImages()` método para extrair imagens do arquivo Excel.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Etapa 3: definir opções de extração de imagem
Especifique o formato da imagem e outras opções para salvar as imagens extraídas. Por exemplo, para salvar imagens no formato PNG:
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Etapa 4: iterar e salvar imagens
Itere sobre as imagens extraídas e salve cada imagem em um arquivo.
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
Neste tutorial, você aprendeu como usar GroupDocs.Parser for .NET para extrair imagens de um documento Excel. Seguindo essas etapas, você pode incorporar recursos de extração de imagens em seus aplicativos .NET com eficiência.

## Perguntas frequentes
### P: O GroupDocs.Parser pode extrair imagens de outros formatos de documento além do Excel?
R: Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo Word, PowerPoint, PDF e muito mais.
### P: Como posso obter suporte ou assistência com a integração do GroupDocs.Parser?
 R: Para suporte e assistência, visite o[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### P: O uso do GroupDocs.Parser é gratuito?
 R: GroupDocs.Parser oferece uma avaliação gratuita, mas para uso contínuo, pode ser necessário adquirir uma licença. Verifica a[preços e licenciamento](https://purchase.groupdocs.com/buy)detalhes.
### P: Posso experimentar o GroupDocs.Parser antes de comprar uma licença?
 R: Sim, você pode obter um[teste grátis](https://releases.groupdocs.com/) para avaliar GroupDocs.Parser.
### P: Onde posso encontrar documentação detalhada para GroupDocs.Parser?
 R: Consulte o abrangente[documentação](https://reference.groupdocs.com/parser/net/) para obter informações detalhadas sobre como usar GroupDocs.Parser.