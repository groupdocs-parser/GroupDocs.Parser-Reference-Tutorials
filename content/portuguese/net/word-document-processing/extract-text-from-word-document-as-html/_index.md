---
title: Extraia texto de documento do Word como HTML
linktitle: Extraia texto de documento do Word como HTML
second_title: API GroupDocs.Parser .NET
description: Aprenda como usar GroupDocs.Parser for .NET para extrair texto de documentos do Word e salvá-lo como HTML. Tutorial passo a passo com exemplos de código.
weight: 16
url: /pt/net/word-document-processing/extract-text-from-word-document-as-html/
---
## Introdução
GroupDocs.Parser for .NET é uma poderosa biblioteca de análise de documentos que permite aos desenvolvedores extrair texto e metadados de vários formatos de arquivo perfeitamente. Neste tutorial, vamos nos concentrar em aproveitar GroupDocs.Parser para extrair texto de documentos do Word e salvá-lo como HTML. Este processo é essencial para tarefas como análise de conteúdo, indexação ou conversão de documentos em formatos compatíveis com a web. Ao final deste guia, você terá uma compreensão clara de como usar GroupDocs.Parser de forma eficiente em seus aplicativos .NET.
## Pré-requisitos
Antes de mergulhar neste tutorial, certifique-se de ter os seguintes pré-requisitos:
- Conhecimento básico de programação C#.
- Visual Studio instalado em sua máquina de desenvolvimento.
-  Biblioteca GroupDocs.Parser para .NET. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/parser/net/).
- Acesso a um documento Word de amostra para fins de teste.
## Importar namespaces
Para começar, você precisa importar os namespaces necessários para o seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Siga estas etapas detalhadas para extrair texto de um documento do Word e salvá-lo como HTML usando GroupDocs.Parser for .NET:
## Etapa 1: crie uma instância da classe analisador
 Primeiro, crie uma instância do`Parser` class fornecendo o caminho para seu documento do Word de amostra:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Continue na Etapa 2...
}
```
 Substituir`"YourSampleFile.docx"`com o caminho para o seu documento do Word.
## Etapa 2: extrair texto formatado como HTML
 A seguir, use o`GetFormattedText` método junto com`FormattedTextOptions`para extrair o texto em formato HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraia um texto formatado para o leitor
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Continue na Etapa 3...
    }
}
```
## Etapa 3: leia e produza o HTML extraído
 Por fim, leia o conteúdo HTML extraído do`TextReader` e imprima-o no console:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraia um texto formatado para o leitor
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Imprima o texto formatado como HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Conclusão
Neste tutorial, exploramos como usar GroupDocs.Parser for .NET para extrair texto de um documento do Word e salvá-lo como HTML. Esta biblioteca oferece uma maneira simples e eficiente de analisar o conteúdo do documento, tornando-a uma ferramenta inestimável para tarefas de processamento de documentos em aplicativos .NET.

## Perguntas frequentes
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode solicitar uma licença temporária de[aqui](https://purchase.groupdocs.com/temporary-license/).
### Onde posso encontrar mais documentação para GroupDocs.Parser?
 Documentação detalhada está disponível[aqui](https://tutorials.groupdocs.com/parser/net/).
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode acessar a versão de avaliação gratuita[aqui](https://releases.groupdocs.com/).
### Como obtenho suporte para GroupDocs.Parser?
 Visite o fórum de suporte[aqui](https://forum.groupdocs.com/c/parser/17).
### Que tipos de documentos o GroupDocs.Parser suporta?
GroupDocs.Parser oferece suporte a vários formatos de documentos, incluindo Word, PDF, Excel, PowerPoint e muito mais.