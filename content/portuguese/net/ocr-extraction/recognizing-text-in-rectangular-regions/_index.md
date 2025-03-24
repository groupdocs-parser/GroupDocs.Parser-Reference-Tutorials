---
title: Reconhecendo texto em regiões retangulares
linktitle: Reconhecendo texto em regiões retangulares
second_title: API GroupDocs.Parser .NET
description: Aprenda como reconhecer texto em regiões específicas de documentos usando GroupDocs.Parser for .NET com recursos de OCR.
weight: 14
url: /pt/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para reconhecer texto em regiões retangulares específicas de documentos. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores extrair texto, metadados e muito mais de vários formatos de arquivo, incluindo PDF, Word, Excel e PowerPoint.
## Pré-requisitos
Antes de começarmos, certifique-se de ter a seguinte configuração:
-  GroupDocs.Parser for .NET: Baixe e instale a biblioteca de[aqui](https://releases.groupdocs.com/parser/net/).
- Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE .NET.
- Documento de amostra: Tenha um arquivo de amostra (por exemplo, PDF, DOCX) que contenha texto a ser reconhecido.

## Importar namespaces
Primeiro, você precisará importar os namespaces necessários para seu código C#:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: inicializar as configurações do analisador
 Comece configurando o`ParserSettings` com o conector OCR. Aqui, usaremos o conector local Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Etapa 2: criar uma instância do analisador
 A seguir, instancie o`Parser` class com as configurações definidas anteriormente:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // O código continua aqui
}
```
 Substituir`"YourSampleFile.pdf"` com o caminho para o seu documento.
## Etapa 3: Definir retângulo de OCR
 Defina um retângulo dentro do documento onde será realizado o reconhecimento do texto. Por exemplo, um retângulo começando em`(0, 0)` com largura`400` e altura`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Etapa 4: configurar opções de reconhecimento de texto
 Criar`TextOptions` para especificar o uso de OCR junto com o retângulo definido:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Etapa 5: extrair texto usando OCR
 Use o`GetText` método do`Parser` instância com o configurado`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Leia o texto extraído ou trate o caso 'não suportado'
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Conclusão
Neste tutorial, demonstramos como aproveitar o GroupDocs.Parser for .NET para extrair texto de regiões retangulares específicas em documentos usando OCR. Este processo pode ser ainda mais personalizado e integrado em vários aplicativos para tarefas automatizadas de extração de texto.

## Perguntas frequentes
### O GroupDocs.Parser pode extrair texto de documentos digitalizados?
Sim, GroupDocs.Parser suporta OCR (Optical Character Recognition) para extrair texto de documentos digitalizados.
### Quais formatos de arquivo o GroupDocs.Parser suporta?
GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de arquivo, incluindo PDF, DOCX, XLSX, PPTX e muito mais.
### Como posso lidar com documentos que não são compatíveis com extração de texto?
 Você pode verificar se a extração de texto é suportada usando`TextReader` instância retornada por`parser.GetText(options)`.
### O GroupDocs.Parser é adequado para tarefas de extração de texto em grande escala?
Sim, GroupDocs.Parser foi projetado para lidar com tarefas de extração de texto em grande escala com eficiência.
### Onde posso obter suporte para problemas relacionados ao GroupDocs.Parser?
 Para suporte e discussões, visite o[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).