---
title: Pesquisar texto em documento do Word por palavra-chave
linktitle: Pesquisar texto em documento do Word por palavra-chave
second_title: API GroupDocs.Parser .NET
description: Aprenda como pesquisar texto em documentos do Word usando GroupDocs.Parser for .NET. Extraia palavras-chave específicas com eficiência.
weight: 18
url: /pt/net/word-document-processing/search-text-in-word-document-by-keyword/
type: docs
---
# Pesquisar texto em documento do Word por palavra-chave

## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para pesquisar texto específico em um documento do Word usando C#. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores extrair texto e metadados de vários formatos de documentos, incluindo documentos do Word.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos:
1. Ambiente de Desenvolvimento: Instale o Visual Studio ou outro IDE compatível.
2.  Biblioteca GroupDocs.Parser: Baixe e instale a biblioteca GroupDocs.Parser for .NET do[local na rede Internet](https://releases.groupdocs.com/parser/net/).
3. Exemplo de documento do Word: prepare um exemplo de documento do Word para usar na pesquisa de texto.

## Importar namespaces
Comece importando os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Etapa 1: crie uma instância da classe analisador
 Primeiro, crie uma instância do`Parser` class passando o caminho para seu documento do Word de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // O código vai aqui
}
```
## Etapa 2: pesquise uma palavra-chave
 A seguir, use o`Search` método do`Parser` class para pesquisar uma palavra-chave específica no documento.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Substituir`"keyword"` com o texto que você deseja pesquisar no documento.
## Etapa 3: iterar nos resultados da pesquisa
 Itere sobre os resultados da pesquisa usando um`foreach` loop para acessar cada`SearchResult` objeto.
```csharp
foreach (SearchResult result in searchResults)
{
    //Código para lidar com cada resultado da pesquisa
}
```
## Etapa 4: acessar os detalhes do resultado da pesquisa
 Dentro do loop, você pode acessar a posição e o texto de cada resultado da pesquisa usando o`Position` e`Text` propriedades do`SearchResult` objeto.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Este trecho de código imprime o índice (`Position`) e o texto encontrado (`Text`) para cada resultado da pesquisa no console.

## Conclusão
Neste tutorial, você aprendeu como usar GroupDocs.Parser for .NET para pesquisar texto específico em um documento do Word. Esta biblioteca fornece uma maneira conveniente de extrair e manipular conteúdo de vários formatos de documentos de forma programática.

## Perguntas frequentes
### O GroupDocs.Parser pode lidar com outros formatos de documentos além do Word?
Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos, incluindo PDF, Excel, PowerPoint e muito mais.
### O GroupDocs.Parser é compatível com o .NET Core?
Sim, GroupDocs.Parser é compatível com .NET Framework e .NET Core.
### Como obtenho uma licença temporária para GroupDocs.Parser?
 Você pode solicitar uma licença temporária do[Página de compra do GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Onde posso encontrar suporte adicional ou fazer perguntas sobre GroupDocs.Parser?
 Visite a[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) para apoio e discussões da comunidade.
### Posso experimentar o GroupDocs.Parser gratuitamente antes de comprar?
 Sim, você pode baixar uma versão de teste gratuita no site[Página de lançamentos do GroupDocs](https://releases.groupdocs.com/).