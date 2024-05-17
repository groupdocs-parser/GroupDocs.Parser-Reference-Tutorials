---
title: Carregar documento do stream
linktitle: Carregar documento do stream
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto de vários formatos de documentos em .NET usando GroupDocs.Parser. Guia passo a passo com exemplos de código.
type: docs
weight: 12
url: /pt/net/document-loading/load-document-from-stream/
---
## Introdução
No domínio do processamento de documentos em aplicativos .NET, extrair texto de vários formatos de arquivo é um requisito comum. GroupDocs.Parser for .NET oferece uma solução poderosa para analisar e extrair texto de uma ampla variedade de documentos. Este tutorial irá guiá-lo através do processo de utilização do GroupDocs.Parser para extrair texto de documentos passo a passo.
## Pré-requisitos
Antes de começar a usar GroupDocs.Parser for .NET, certifique-se de ter a seguinte configuração:
- Ambiente de Desenvolvimento: Visual Studio ou qualquer outro ambiente de desenvolvimento .NET.
-  Pacote GroupDocs.Parser for .NET: Baixe e instale a biblioteca GroupDocs.Parser for .NET em[aqui](https://releases.groupdocs.com/parser/net/).
- Amostras de documentos: tenha documentos de amostra prontos para extração de texto.
## Importando Namespaces
Comece importando os namespaces necessários para seu projeto .NET para acessar as funcionalidades do GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

As etapas a seguir demonstram como extrair texto de um documento usando GroupDocs.Parser de um fluxo.
## Etapa 1: carregar o documento do stream
```csharp
// Crie o fluxo
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Crie uma instância da classe Parser com o stream
    using (Parser parser = new Parser(stream))
    {
        // Extraia o texto para o leitor
        using (TextReader reader = parser.GetText())
        {
            // Imprimir texto do documento
            // Se a extração de texto não for compatível, o leitor será nulo
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
Neste exemplo:
- Abrimos um fluxo de arquivo para o arquivo do documento (`YourSampleFile.docx`).
-  Inicialize um`Parser` instância com o fluxo.
-  Usar`parser.GetText()` para recuperar um`TextReader` contendo o texto extraído.
- Imprima o texto extraído ou uma mensagem se a extração de texto não for compatível com o formato do documento.
## Conclusão
GroupDocs.Parser for .NET simplifica a extração de texto de vários formatos de documentos, permitindo que os desenvolvedores processem e utilizem com eficiência o conteúdo textual em seus aplicativos. Seguindo as etapas descritas neste tutorial, você pode integrar perfeitamente os recursos de extração de texto de documentos em seus projetos .NET.

## Perguntas frequentes
### Quais formatos de documento são suportados pelo GroupDocs.Parser for .NET?
GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo DOCX, PDF, XLSX, PPTX, EPUB e muito mais.
### O GroupDocs.Parser pode extrair imagens ou metadados de documentos?
Sim, GroupDocs.Parser pode extrair imagens, metadados e texto de vários tipos de documentos.
### O GroupDocs.Parser é compatível com aplicativos .NET Core?
Sim, GroupDocs.Parser é compatível com aplicativos .NET Framework e .NET Core.
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode obter uma licença temporária em[aqui](https://purchase.groupdocs.com/temporary-license/).
### Onde posso encontrar mais suporte ou documentação para GroupDocs.Parser?
 Para suporte adicional, visite o[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) ou consulte o[documentação](https://reference.groupdocs.com/parser/net/).
