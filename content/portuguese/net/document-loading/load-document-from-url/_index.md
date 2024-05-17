---
title: Carregar documento do URL
linktitle: Carregar documento do URL
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto de documentos usando GroupDocs.Parser for .NET. Este tutorial aborda o carregamento de um documento de uma URL e a extração de texto passo a passo.
type: docs
weight: 13
url: /pt/net/document-loading/load-document-from-url/
---
## Introdução
Neste tutorial, exploraremos como utilizar GroupDocs.Parser for .NET para extrair texto de documentos. GroupDocs.Parser é uma ferramenta poderosa para extrair texto, metadados e outras informações de vários formatos de documentos, como PDF, Word, Excel e muito mais. Abordaremos o processo de carregamento de um documento de uma URL e extração de seu conteúdo de texto passo a passo.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos configurados:
1. Visual Studio: instale o Visual Studio em seu sistema.
2.  GroupDocs.Parser for .NET: Baixe e instale GroupDocs.Parser for .NET a partir do[página de download](https://releases.groupdocs.com/parser/net/).
3. Compreensão básica de C#: Familiaridade com a linguagem de programação C#.

## Importar namespaces
Comece incluindo os namespaces necessários em seu código C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Primeiro, demonstraremos como carregar um documento de uma URL e extrair seu conteúdo de texto.
## Etapa 1: especifique o URL do documento
Especifique o URL do documento do qual deseja extrair o texto:
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## Etapa 2: criar uma instância do analisador
 Instancie o`Parser` classe com o URL do documento:
```csharp
using (Parser parser = new Parser(uri))
{
    // Seu código vai aqui
}
```
## Etapa 3: extrair texto do documento
 Dentro de`using`bloquear, usar`parser.GetText()` para extrair texto do documento:
```csharp
using (TextReader reader = parser.GetText())
{
    // Seu código vai aqui
}
```
## Etapa 4: exibir o texto extraído
Leia e imprima o texto extraído do documento:
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## Conclusão
Neste tutorial, cobrimos os fundamentos da extração de texto de um documento usando GroupDocs.Parser for .NET. Seguindo essas etapas, você pode integrar facilmente recursos de extração de texto de documentos em seus aplicativos C#.

## Perguntas frequentes
### O GroupDocs.Parser é compatível com vários formatos de documentos?
Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muito mais.
### Posso extrair metadados junto com texto usando GroupDocs.Parser?
Sim, GroupDocs.Parser permite extrair metadados, texto e outras informações de documentos.
### Existe uma versão de teste disponível para GroupDocs.Parser?
 Sim, você pode obter uma versão de avaliação gratuita do GroupDocs.Parser em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar documentação para GroupDocs.Parser?
 Documentação detalhada para GroupDocs.Parser está disponível[aqui](https://reference.groupdocs.com/parser/net/).
### Como posso obter suporte técnico para GroupDocs.Parser?
Você pode procurar suporte técnico e fazer perguntas no fórum GroupDocs.Parser[aqui](https://forum.groupdocs.com/c/parser/17).