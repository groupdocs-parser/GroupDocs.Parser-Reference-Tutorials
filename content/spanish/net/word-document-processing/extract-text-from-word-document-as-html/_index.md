---
title: Extraer texto de un documento de Word como HTML
linktitle: Extraer texto de un documento de Word como HTML
second_title: API GroupDocs.Parser .NET
description: Aprenda a utilizar GroupDocs.Parser para .NET para extraer texto de documentos de Word y guardarlo como HTML. Tutorial paso a paso con ejemplos de código.
type: docs
weight: 16
url: /es/net/word-document-processing/extract-text-from-word-document-as-html/
---
## Introducción
GroupDocs.Parser para .NET es una poderosa biblioteca de análisis de documentos que permite a los desarrolladores extraer texto y metadatos de varios formatos de archivos sin problemas. En este tutorial, nos centraremos en aprovechar GroupDocs.Parser para extraer texto de documentos de Word y guardarlo como HTML. Este proceso es esencial para tareas como análisis de contenido, indexación o conversión de documentos a formatos compatibles con la web. Al final de esta guía, comprenderá claramente cómo utilizar GroupDocs.Parser de manera eficiente en sus aplicaciones .NET.
## Requisitos previos
Antes de sumergirse en este tutorial, asegúrese de tener los siguientes requisitos previos:
- Conocimientos básicos de programación en C#.
- Visual Studio instalado en su máquina de desarrollo.
-  GroupDocs.Parser para la biblioteca .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/parser/net/).
- Acceso a un documento de Word de muestra para fines de prueba.
## Importar espacios de nombres
Para comenzar, necesita importar los espacios de nombres necesarios a su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Siga estos pasos detallados para extraer texto de un documento de Word y guardarlo como HTML usando GroupDocs.Parser para .NET:
## Paso 1: crear una instancia de la clase Parser
 Primero, cree una instancia del`Parser` clase proporcionando la ruta a su documento de Word de muestra:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Continúe con el Paso 2...
}
```
 Reemplazar`"YourSampleFile.docx"`con la ruta a su documento de Word.
## Paso 2: extraiga el texto formateado como HTML
 A continuación, utilice el`GetFormattedText` método junto con`FormattedTextOptions`para extraer el texto en formato HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraer un texto formateado en el lector.
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Continúe con el Paso 3...
    }
}
```
## Paso 3: leer y generar el HTML extraído
 Finalmente, lea el contenido HTML extraído del`TextReader` e imprimirlo en la consola:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraer un texto formateado en el lector.
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Imprima el texto formateado como HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Conclusión
En este tutorial, exploramos cómo usar GroupDocs.Parser para .NET para extraer texto de un documento de Word y guardarlo como HTML. Esta biblioteca ofrece una manera sencilla y eficiente de analizar el contenido de documentos, lo que la convierte en una herramienta invaluable para tareas de procesamiento de documentos en aplicaciones .NET.

## Preguntas frecuentes
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Parser?
 Puede solicitar una licencia temporal a[aquí](https://purchase.groupdocs.com/temporary-license/).
### ¿Dónde puedo encontrar más documentación para GroupDocs.Parser?
 La documentación detallada está disponible.[aquí](https://reference.groupdocs.com/parser/net/).
### ¿Existe una prueba gratuita disponible para GroupDocs.Parser?
 Sí, puedes acceder a la versión de prueba gratuita.[aquí](https://releases.groupdocs.com/).
### ¿Cómo obtengo soporte para GroupDocs.Parser?
 Visita el foro de soporte[aquí](https://forum.groupdocs.com/c/parser/17).
### ¿Qué tipos de documentos admite GroupDocs.Parser?
GroupDocs.Parser admite varios formatos de documentos, incluidos Word, PDF, Excel, PowerPoint y más.