---
title: Extraer texto formateado de la página del documento
linktitle: Extraer texto formateado de la página del documento
second_title: API GroupDocs.Parser .NET
description: Extraiga texto formateado de páginas de documentos utilizando GroupDocs.Parser para .NET. Solución de extracción de texto eficiente y confiable.
type: docs
weight: 11
url: /es/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## Introducción
En este tutorial, lo guiaremos a través del proceso de extracción de texto formateado de páginas de documentos usando GroupDocs.Parser para .NET. Esta biblioteca le permite analizar y extraer texto de manera eficiente desde varios formatos de documentos como PDF, Word, Excel y más.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Visual Studio instalado en su sistema.
- Conocimientos básicos de programación en C#.
-  GroupDocs.Parser para la biblioteca .NET. Puedes descargarlo[aquí](https://releases.groupdocs.com/parser/net/).

## Importar espacios de nombres
Primero, comience importando los espacios de nombres necesarios a su proyecto C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Paso 1: crear una instancia de la clase Parser
 Comience creando una instancia de`Parser` class proporcionando la ruta a su archivo de muestra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // El código irá aquí
}
```
## Paso 2: compruebe si se admite la extracción de texto formateado
Antes de continuar con la extracción de texto, verifique si el documento admite la extracción de texto formateado.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Paso 3: Obtenga información del documento
Recupera información sobre el documento, como el número de páginas.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Paso 4: iterar sobre las páginas del documento y extraer texto formateado
Itere a través de cada página del documento y extraiga texto formateado usando opciones específicas (por ejemplo, formato Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusión
Ahora ya sabe cómo extraer texto formateado de páginas de documentos utilizando GroupDocs.Parser para .NET. Esta biblioteca proporciona una solución potente y fácil de usar para la extracción de texto de varios formatos de archivo.

## Preguntas frecuentes
### ¿Puede GroupDocs.Parser manejar diferentes formatos de archivo?
Sí, GroupDocs.Parser admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, XLSX, PPTX y más.
### ¿GroupDocs.Parser es compatible con .NET Core?
Sí, GroupDocs.Parser es compatible con .NET Core y .NET Framework.
### ¿GroupDocs.Parser conserva el formato del texto durante la extracción?
Sí, GroupDocs.Parser puede conservar formatos como estilos y fuentes al extraer texto.
### ¿Puedo extraer imágenes y metadatos usando GroupDocs.Parser?
Sí, GroupDocs.Parser permite la extracción de imágenes, metadatos y texto de documentos.
### ¿Cómo puedo obtener soporte para GroupDocs.Parser?
 Puede obtener apoyo del[Foro GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).