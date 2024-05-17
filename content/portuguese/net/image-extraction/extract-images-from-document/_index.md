---
title: Extrair imagens do documento
linktitle: Extrair imagens do documento
second_title: API GroupDocs.Parser .NET
description: Extraia imagens de documentos sem esforço usando GroupDocs.Parser for .NET. Seus recursos de processamento de documentos e agilizam as tarefas de extração de imagens com eficiência.
type: docs
weight: 11
url: /pt/net/image-extraction/extract-images-from-document/
---
## Introdução
Neste tutorial, exploraremos como extrair imagens de documentos usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores extrair texto, metadados, imagens e muito mais de vários formatos de documentos.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos configurados:
- Visual Studio: instale o Visual Studio em sua máquina.
-  GroupDocs.Parser para .NET: Baixe e instale GroupDocs.Parser do[página de download](https://releases.groupdocs.com/parser/net/).
- Documento de amostra: Prepare um documento de amostra (PDF, DOCX, etc.) do qual deseja extrair imagens.

## Importar namespaces
Comece importando os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Etapa 1: crie uma instância da classe analisador
 Primeiro, crie uma instância do`Parser` class fornecendo o caminho para seu documento de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Seu código vai aqui
}
```
 Substituir`"YourSampleFile.pdf"` com o caminho para o arquivo do seu documento.
## Etapa 2: extrair imagens do documento
 A seguir, extraia imagens do documento usando o`GetImages()` método.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 O`GetImages()` método retorna uma coleção de`PageImageArea` objetos que representam imagens encontradas no documento.
## Etapa 3: verifique o suporte para extração de imagens
Antes de iterar nas imagens, verifique se a extração de imagens é compatível com o documento.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Esta etapa garante que o documento contenha imagens extraíveis.
## Etapa 4: iterar sobre imagens extraídas
Agora, itere sobre as imagens extraídas para acessar informações detalhadas sobre cada imagem, como índice da página, coordenadas do retângulo e tipo de imagem.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Este loop imprime informações sobre cada imagem extraída, incluindo sua localização e tipo.

## Conclusão
Neste tutorial, aprendemos como usar GroupDocs.Parser for .NET para extrair imagens de documentos programaticamente. Seguindo essas etapas, você pode integrar perfeitamente a funcionalidade de extração de imagens de documentos em seus aplicativos .NET.

## Perguntas frequentes
### GroupDocs.Parser pode extrair imagens de todos os formatos de documentos?
GroupDocs.Parser oferece suporte à extração de imagens de vários formatos, incluindo PDF, DOCX, XLSX e muito mais.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode acessar uma avaliação gratuita do GroupDocs.Parser no site[local na rede Internet](https://releases.groupdocs.com/).
### Onde posso encontrar documentação para GroupDocs.Parser?
 Documentação detalhada para GroupDocs.Parser pode ser encontrada[aqui](https://reference.groupdocs.com/parser/net/).
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode obter uma licença temporária do[página de licença temporária](https://purchase.groupdocs.com/temporary-license/).
### Onde posso obter suporte para GroupDocs.Parser?
 Para suporte e assistência técnica, visite o[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).