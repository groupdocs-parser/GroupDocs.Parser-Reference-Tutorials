---
title: Extrair texto simples
linktitle: Extrair texto simples
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto simples de documentos usando GroupDocs.Parser for .NET. Etapas fáceis para integrar a extração de texto em seus aplicativos.
weight: 14
url: /pt/net/formatted-text-extraction/extract-plain-text/
---

# Extrair texto simples

## Introdução
Neste tutorial, exploraremos como extrair texto simples de vários formatos de documento usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores trabalhar com documentos de forma integrada, extraindo texto e metadados de forma eficiente. Este guia orientará você nas etapas necessárias para integrar e utilizar esta biblioteca em seus aplicativos .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos em vigor:
1. Visual Studio: instale o Visual Studio em sua máquina de desenvolvimento.
2.  Biblioteca GroupDocs.Parser: Baixe e instale GroupDocs.Parser for .NET do[página de download](https://releases.groupdocs.com/parser/net/).
3. Documentos de amostra: Prepare documentos de amostra (por exemplo, DOCX, PDF, TXT) para extração de texto.

## Importar namespaces
Primeiro, inclua os namespaces necessários em seu projeto C# para acessar as funcionalidades do GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Etapa 1: inicializar o analisador
 Crie uma instância do`Parser` class especificando o caminho para seu documento de amostra.
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    // O código para extração de texto vai aqui
}
```
## Etapa 2: extrair texto formatado
 Dentro do`using` bloco do`Parser` extraia o texto formatado usando o`GetFormattedText` método com`PlainText` modo.
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    // Código para ler e processar o texto extraído
}
```
## Etapa 3: leia o texto extraído
 Use o`TextReader` instância para ler e gerar o texto simples extraído.
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## Conclusão
Neste tutorial, cobrimos os fundamentos da extração de texto simples de documentos usando GroupDocs.Parser for .NET. Seguindo essas etapas, você pode integrar perfeitamente recursos de extração de texto em seus aplicativos .NET.

## Perguntas frequentes
### O GroupDocs.Parser é compatível com vários formatos de documentos?
Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo DOCX, PDF, TXT e muito mais.
### Posso extrair metadados junto com texto usando GroupDocs.Parser?
Com certeza, GroupDocs.Parser permite a extração de conteúdo de texto e metadados como autor, data de criação, etc.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode acessar a avaliação gratuita do GroupDocs.Parser[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar suporte técnico para GroupDocs.Parser?
 Para assistência técnica, visite GroupDocs.Parser[fórum](https://forum.groupdocs.com/c/parser/17).
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Para adquirir uma licença temporária, visite GroupDocs.Parser[página de licença temporária](https://purchase.groupdocs.com/temporary-license/).