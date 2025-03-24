---
title: Pesquisar texto com destaques
linktitle: Pesquisar texto com destaques
second_title: API GroupDocs.Parser .NET
description: Aprenda como pesquisar e destacar texto em documentos usando GroupDocs.Parser for .NET. Extraia insights valiosos com eficiência.
weight: 24
url: /pt/net/text-extraction/search-text-with-highlights/
---

# Pesquisar texto com destaques

## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para pesquisar texto em um documento e destacar os resultados da pesquisa. GroupDocs.Parser é uma biblioteca poderosa que permite trabalhar com vários formatos de documentos e extrair texto, metadados e muito mais.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
1.  GroupDocs.Parser for .NET: Baixe e instale a biblioteca de[aqui](https://releases.groupdocs.com/parser/net/).
2. IDE: Use o Visual Studio ou qualquer IDE preferido para desenvolvimento .NET.
3. Arquivo de amostra: Prepare um documento de amostra (por exemplo, PDF, DOCX) para pesquisa de texto.

## Importar namespaces
Primeiro, comece importando os namespaces necessários em seu projeto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: criar uma instância do analisador
 Comece instanciando o`Parser` class pelo caminho para seu arquivo de amostra:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Seu código aqui
}
```
## Etapa 2: definir opções de destaque
 Especifique o`HighlightOptions` para configurar como os resultados da pesquisa devem ser destacados. Por exemplo, definindo uma janela de contexto de 15 caracteres:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Etapa 3: pesquisar texto
Agora, faça uma pesquisa de texto no documento. Forneça a palavra-chave que deseja pesquisar (por exemplo, “lorem”):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Etapa 4: processar resultados da pesquisa
Itere pelos resultados da pesquisa e exiba o texto encontrado junto com os destaques:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Conclusão
Neste tutorial, você aprendeu como usar GroupDocs.Parser for .NET para pesquisar texto em documentos e destacar os resultados da pesquisa. Essa funcionalidade pode ser imensamente útil para extração e análise de texto em seus aplicativos .NET.

## Perguntas frequentes
### O GroupDocs.Parser é adequado para processar vários formatos de documentos?
Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, DOCX, XLSX, PPTX e muito mais.
### Posso usar GroupDocs.Parser para extrair metadados de documentos?
Absolutamente! GroupDocs.Parser permite extrair metadados, texto e dados estruturados de documentos.
### Onde posso encontrar suporte ou fazer perguntas sobre GroupDocs.Parser?
 Você pode visitar o[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) para quaisquer dúvidas relacionadas ao suporte.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode acessar um[teste grátis](https://releases.groupdocs.com/) do GroupDocs.Parser para avaliar seus recursos.
### Como posso adquirir uma licença para GroupDocs.Parser?
 Você pode comprar uma licença de[aqui](https://purchase.groupdocs.com/buy) e também obter licenças temporárias[aqui](https://purchase.groupdocs.com/temporary-license/).