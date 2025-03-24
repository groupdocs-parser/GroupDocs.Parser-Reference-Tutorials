---
title: Extraia texto formatado do documento
linktitle: Extraia texto formatado do documento
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto formatado de documentos usando GroupDocs.Parser for .NET. Extração de texto simples e eficiente para suas aplicações.
weight: 10
url: /pt/net/formatted-text-extraction/extract-formatted-text-from-document/
---

# Extraia texto formatado do documento

## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para extrair texto formatado de vários tipos de documentos. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores trabalhar com documentos de maneira simplificada e eficiente. Ao final deste guia, você será capaz de integrar perfeitamente recursos de extração de texto em seus aplicativos .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
- Visual Studio: certifique-se de ter o Visual Studio instalado em seu sistema.
-  GroupDocs.Parser for .NET: Baixe e instale a biblioteca GroupDocs.Parser em[aqui](https://releases.groupdocs.com/parser/net/).
- Amostras de documentos: Prepare documentos de amostra (por exemplo, PDF, DOCX) para extração de texto.
## Importar namespaces
Primeiro, inclua os namespaces necessários em seu código C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Etapa 1: crie uma instância da classe analisador
 Comece inicializando um`Parser` objeto pelo caminho para seu documento de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // O código de extração de texto vai aqui
}
```
 Substituir`"YourSampleFile.pdf"` com o caminho para o arquivo do seu documento.

## Etapa 2: extrair texto formatado
 Dentro do`using` bloco, use o`GetFormattedText` método para extrair texto formatado do documento. Especifique o formato de saída desejado (por exemplo, HTML) usando`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extraia texto formatado para o leitor
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Verifique se a extração é suportada
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Ler e exibir o texto extraído
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Conclusão
Parabéns! Você aprendeu como extrair texto formatado de documentos usando GroupDocs.Parser for .NET. Esta biblioteca versátil abre possibilidades para processamento e análise de texto em seus aplicativos.

## Perguntas frequentes
### P: O GroupDocs.Parser pode extrair texto de documentos protegidos por senha?
R: Sim, GroupDocs.Parser oferece suporte à extração de texto de documentos protegidos por senha.
### P: Quais formatos de documento são suportados pelo GroupDocs.Parser?
R: GroupDocs.Parser oferece suporte a uma ampla variedade de formatos, incluindo PDF, DOCX, XLSX, PPTX e muito mais.
### P: Como posso obter uma licença temporária do GroupDocs.Parser?
 R: Você pode obter uma licença temporária em[aqui](https://purchase.groupdocs.com/temporary-license/).
### P: O GroupDocs.Parser oferece suporte para extração de imagens de documentos?
R: Sim, GroupDocs.Parser oferece suporte à extração de imagens junto com a extração de texto.
### P: Onde posso encontrar suporte adicional ou fazer perguntas sobre GroupDocs.Parser?
 R: Visite o[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)para apoio e discussões.