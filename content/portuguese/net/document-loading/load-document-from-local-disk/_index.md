---
title: Carregar documento do disco local
linktitle: Carregar documento do disco local
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair texto de vários formatos de documentos usando GroupDocs.Parser for .NET. Extração de texto fácil e eficiente com C#.
weight: 11
url: /pt/net/document-loading/load-document-from-local-disk/
---

# Carregar documento do disco local

## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para extrair texto de documentos. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores analisar vários formatos de documentos e extrair conteúdo de texto programaticamente. Abordaremos as etapas necessárias para começar a extrair texto usando esta biblioteca.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos instalados:
- Visual Studio instalado em seu sistema.
- Conhecimento básico da linguagem de programação C#.
-  Biblioteca GroupDocs.Parser for .NET instalada (download[aqui](https://releases.groupdocs.com/parser/net/)).

## Importar namespaces
Primeiro, você precisa importar os namespaces necessários para o seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Etapa 1: carregar o documento do disco local
 Comece carregando um documento do seu disco local. Substituir`"Your Sample File"` com o caminho para o seu documento de destino.
```csharp
// Defina o caminho do arquivo
string filePath = "Your Sample File";
// Crie uma instância da classe Parser com o filePath
using (Parser parser = new Parser(filePath))
{
    // Extraia o texto para o leitor
    using (TextReader reader = parser.GetText())
    {
        //Imprima o texto extraído do documento
        // Se a extração de texto não for compatível, o leitor será nulo
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Explicação das etapas
1. Configurando o caminho do arquivo: comece especificando o caminho para o documento do qual deseja extrair o texto (`filePath` variável).
2.  Criando instância do analisador: instancie o`Parser` aula, passando no`filePath`.
3.  Extraindo Texto: Use o`GetText()` método do`Parser` instância para obter um`TextReader` objeto que contém o texto extraído do documento.
4.  Lendo texto extraído: utilize o`ReadToEnd()` método do`TextReader` para recuperar todo o conteúdo do texto extraído do documento.
5.  Tratamento de formatos não suportados: se o formato do documento não suportar extração de texto, o`reader` objeto será`null`, e você pode lidar com esse cenário adequadamente.

## Conclusão
Neste tutorial, cobrimos as etapas iniciais para extrair texto de um documento usando GroupDocs.Parser for .NET. Esta biblioteca oferece recursos abrangentes para análise de documentos, permitindo que os desenvolvedores trabalhem de forma eficiente com vários formatos de arquivo em seus aplicativos.

## Perguntas frequentes
### O GroupDocs.Parser é compatível com todos os formatos de documento?
GroupDocs.Parser oferece suporte a uma ampla variedade de formatos, incluindo PDF, documentos do Microsoft Office (Word, Excel, PowerPoint) e muito mais.
### Posso extrair metadados junto com texto usando GroupDocs.Parser?
Sim, GroupDocs.Parser permite a extração de conteúdo de texto e metadados de formatos de documentos suportados.
### Onde posso encontrar mais recursos e suporte para GroupDocs.Parser?
 Visite a[Documentação GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) para obter referência detalhada da API e explorar o[Fórum GroupDocs](https://forum.groupdocs.com/c/parser/17) para apoio comunitário.
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode solicitar um[licença temporária](https://purchase.groupdocs.com/temporary-license/) para fins de avaliação e teste.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode baixar um[teste grátis](https://releases.groupdocs.com/) versão do GroupDocs.Parser.