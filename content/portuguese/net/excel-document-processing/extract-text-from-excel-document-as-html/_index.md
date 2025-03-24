---
title: Extraia texto de documento Excel como HTML
linktitle: Extraia texto de documento Excel como HTML
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto de documentos Excel e convertê-lo em HTML usando GroupDocs.Parser for .NET.
weight: 13
url: /pt/net/excel-document-processing/extract-text-from-excel-document-as-html/
---

# Extraia texto de documento Excel como HTML

## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para extrair texto de um documento Excel e convertê-lo em formato HTML. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores trabalhar com vários formatos de documentos, extraindo texto e metadados de forma eficiente.
## Pré-requisitos
Antes de começarmos, certifique-se de ter a seguinte configuração:
- Visual Studio instalado em seu sistema.
- Compreensão básica de programação C#.
-  Biblioteca GroupDocs.Parser para .NET. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/parser/net/).
## Importar namespaces
Comece incluindo os namespaces necessários em seu projeto C# para acessar as funcionalidades GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: crie uma instância da classe analisador
 Primeiro, instancie o`Parser` class fornecendo o caminho para o seu documento Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Mais código irá aqui
}
```
 Substituir`"YourSampleFile.xlsx"` com o caminho para o seu arquivo Excel.
## Etapa 2: extrair texto como HTML
 Dentro do`using` bloco do`Parser` por exemplo, use o`GetFormattedText` método para extrair texto formatado no modo HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Mais código irá aqui
    }
}
```
## Etapa 3: ler e imprimir o texto HTML extraído
 A seguir, leia o texto HTML extraído do`TextReader` e imprima-o no console.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Uma vez executado, este código irá extrair o texto do documento Excel e exibi-lo em formato HTML no console.
## Conclusão
Neste tutorial, aprendemos como usar GroupDocs.Parser for .NET para extrair texto de um documento Excel e convertê-lo para o formato HTML. Esta biblioteca fornece uma maneira simples de trabalhar com vários formatos de documentos, permitindo que os desenvolvedores lidem com eficiência com tarefas de extração de texto em seus aplicativos.

## Perguntas frequentes
### O GroupDocs.Parser pode lidar com outros formatos de documentos além do Excel?
Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de arquivo, incluindo PDF, Word, PowerPoint e muito mais.
### O GroupDocs.Parser é compatível com o .NET Core?
Sim, GroupDocs.Parser é compatível com .NET Framework e .NET Core.
### GroupDocs.Parser preserva a formatação durante a extração de texto?
Sim, GroupDocs.Parser pode preservar formatação como fontes, estilos e layout durante a extração de texto.
### Posso extrair metadados de documentos usando GroupDocs.Parser?
Sim, GroupDocs.Parser permite extrair metadados como autor, data de criação e muito mais de tipos de documentos suportados.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode baixar uma avaliação gratuita em[aqui](https://releases.groupdocs.com/).