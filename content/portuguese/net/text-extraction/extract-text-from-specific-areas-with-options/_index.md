---
title: Extraia texto de áreas específicas com opções
linktitle: Extraia texto de áreas específicas com opções
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto de áreas específicas em documentos usando GroupDocs.Parser for .NET. Explore opções avançadas de extração de texto com este tutorial.
weight: 14
url: /pt/net/text-extraction/extract-text-from-specific-areas-with-options/
---
## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para extrair texto de áreas específicas de um documento usando opções personalizáveis. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores analisar e extrair texto de vários formatos de documentos sem esforço.
## Pré-requisitos
Antes de mergulharmos na codificação, certifique-se de ter o seguinte:
1. Ambiente de desenvolvimento: Instale o Visual Studio ou qualquer outro IDE de desenvolvimento .NET.
2.  Biblioteca GroupDocs.Parser: Baixe e instale GroupDocs.Parser for .NET em[aqui](https://releases.groupdocs.com/parser/net/).
3. Arquivo de amostra: prepare um documento de amostra (por exemplo, PDF, DOCX, etc.) para extrair o texto.

## Importar namespaces
Primeiro, você precisará importar os namespaces necessários para acessar as classes e métodos GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: crie uma instância da classe analisador
 Inicialize uma instância do`Parser` class fornecendo o caminho para seu arquivo de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // O código para extração de área de texto irá aqui
}
```
## Etapa 2: definir opções de extração de área de texto
 Criar`PageTextAreaOptions` para especificar os critérios para extração de texto.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
Neste exemplo:
- `"\\s[a-z]{2}\\s"` é um padrão de expressão regular para corresponder a áreas de texto contendo apenas letras minúsculas.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` define o retângulo (posição e tamanho) na página da qual o texto será extraído.
## Etapa 3: extrair áreas de texto
Use as opções definidas para extrair áreas de texto que atendam aos critérios especificados.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Etapa 4: verificar e iterar nas áreas de texto extraídas
Verifique se a extração de área de texto é suportada e, em seguida, itere sobre as áreas extraídas.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Conclusão
Neste tutorial, abordamos como extrair texto de áreas específicas de um documento usando GroupDocs.Parser for .NET. Esta biblioteca oferece amplos recursos para analisar vários formatos de documentos, tornando-a uma ferramenta valiosa para tarefas de extração de texto.

## Perguntas frequentes
### O GroupDocs.Parser pode extrair texto de documentos digitalizados?
Sim, GroupDocs.Parser oferece suporte à extração de texto baseada em OCR para documentos digitalizados.
### O GroupDocs.Parser é compatível com vários formatos de documentos?
Sim, ele pode analisar e extrair texto de PDF, DOCX, XLSX, PPTX e outros formatos populares.
### O GroupDocs.Parser fornece suporte para .NET Core?
Sim, GroupDocs.Parser é compatível com .NET Core e também com .NET Framework.
### Posso extrair metadados junto com texto usando GroupDocs.Parser?
Sim, você pode extrair conteúdo textual e metadados de documentos.
### Existe uma versão de teste disponível para GroupDocs.Parser?
 Sim, você pode obter um teste gratuito em[aqui](https://releases.groupdocs.com/).