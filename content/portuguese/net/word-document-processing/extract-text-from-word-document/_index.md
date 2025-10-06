---
title: Extraia texto de documento do Word
linktitle: Extraia texto de documento do Word
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto de documentos do Word usando GroupDocs.Parser for .NET. Guia passo a passo com exemplos de código.
weight: 15
url: /pt/net/word-document-processing/extract-text-from-word-document/
type: docs
---
# Extraia texto de documento do Word

## Introdução
Neste tutorial, exploraremos como extrair texto de documentos do Word usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma biblioteca .NET poderosa que permite aos desenvolvedores trabalhar com vários formatos de documentos, incluindo documentos Word, PDFs e muito mais. Ao final deste guia, você será capaz de extrair texto de arquivos do Word com eficiência usando código C# simples.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos em vigor:
- Visual Studio (ou qualquer ambiente de desenvolvimento C# preferido)
- Biblioteca GroupDocs.Parser para .NET instalada (Baixar[aqui](https://releases.groupdocs.com/parser/net/))
- Conhecimento básico de programação C#

## Importar namespaces
Primeiro, você precisa importar os namespaces necessários em seu projeto C# para acessar a funcionalidade GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Etapa 1: crie uma instância da classe analisador
 Comece criando uma instância do`Parser` class, fornecendo o caminho para o seu documento do Word.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Seu código para extração de texto irá aqui
}
```
 Substituir`"YourSampleFile.docx"` com o caminho para o seu documento real do Word.
## Etapa 2: extrair texto em um TextReader
 Dentro do`using` bloco do`Parser` por exemplo, use o`GetText()` método para extrair o conteúdo do texto em um`TextReader`.
```csharp
using (TextReader reader = parser.GetText())
{
    // Seu código de processamento de texto irá aqui
}
```
## Etapa 3: ler e exibir o texto extraído
 Agora, dentro do`TextReader` bloco, você pode ler e imprimir o texto extraído do documento Word.
```csharp
using (TextReader reader = parser.GetText())
{
    // Leia o texto extraído e imprima-o
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusão
Parabéns! Você aprendeu como extrair texto de documentos do Word usando GroupDocs.Parser for .NET. Esta biblioteca simples, mas poderosa, permite integrar recursos de extração de texto em seus aplicativos .NET de forma eficiente.

## Perguntas frequentes
### O GroupDocs.Parser é compatível com todas as versões do .NET?
Sim, GroupDocs.Parser for .NET é compatível com .NET Framework 4.6.1 e versões posteriores.
### Posso extrair texto de documentos Word criptografados ou protegidos por senha?
GroupDocs.Parser oferece suporte à extração de texto de documentos do Word protegidos por senha.
### O GroupDocs.Parser oferece suporte a outros formatos de documento além de documentos do Word?
Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Excel, PowerPoint e muito mais.
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode solicitar uma licença temporária para GroupDocs.Parser[aqui](https://purchase.groupdocs.com/temporary-license/).
### Onde posso encontrar suporte adicional ou fazer perguntas sobre GroupDocs.Parser?
 Você pode visitar o fórum GroupDocs.Parser[aqui](https://forum.groupdocs.com/c/parser/17)para apoio e discussões.