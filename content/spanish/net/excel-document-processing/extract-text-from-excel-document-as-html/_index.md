---
title: Extraer texto de un documento de Excel como HTML
linktitle: Extraer texto de un documento de Excel como HTML
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer texto de documentos de Excel y convertirlo a HTML usando GroupDocs.Parser para .NET.
weight: 13
url: /es/net/excel-document-processing/extract-text-from-excel-document-as-html/
type: docs
---
# Extraer texto de un documento de Excel como HTML

## Introducción
En este tutorial, exploraremos cómo usar GroupDocs.Parser para .NET para extraer texto de un documento de Excel y convertirlo a formato HTML. GroupDocs.Parser es una poderosa biblioteca que permite a los desarrolladores trabajar con varios formatos de documentos, extrayendo texto y metadatos de manera eficiente.
## Requisitos previos
Antes de comenzar, asegúrese de tener la siguiente configuración:
- Visual Studio instalado en su sistema.
- Conocimientos básicos de programación en C#.
-  Biblioteca GroupDocs.Parser para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/parser/net/).
## Importar espacios de nombres
Comience por incluir los espacios de nombres necesarios en su proyecto C# para acceder a las funcionalidades de GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Paso 1: crear una instancia de la clase Parser
 Primero, cree una instancia del`Parser` clase proporcionando la ruta a su documento de Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Más código irá aquí
}
```
 Reemplazar`"YourSampleFile.xlsx"` con la ruta a su archivo de Excel.
## Paso 2: extraiga el texto como HTML
 Dentro de`using` bloque de la`Parser` ejemplo, utilice el`GetFormattedText` Método para extraer texto formateado en modo HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Más código irá aquí
    }
}
```
## Paso 3: leer e imprimir texto HTML extraído
 A continuación, lea el texto HTML extraído del`TextReader` e imprimirlo en la consola.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Una vez ejecutado, este código extraerá el texto del documento de Excel y lo mostrará en formato HTML en la consola.
## Conclusión
En este tutorial, aprendimos cómo usar GroupDocs.Parser para .NET para extraer texto de un documento de Excel y convertirlo a formato HTML. Esta biblioteca proporciona una forma sencilla de trabajar con varios formatos de documentos, lo que permite a los desarrolladores manejar de manera eficiente las tareas de extracción de texto en sus aplicaciones.

## Preguntas frecuentes
### ¿Puede GroupDocs.Parser manejar otros formatos de documentos además de Excel?
Sí, GroupDocs.Parser admite una amplia gama de formatos de archivo, incluidos PDF, Word, PowerPoint y más.
### ¿GroupDocs.Parser es compatible con .NET Core?
Sí, GroupDocs.Parser es compatible tanto con .NET Framework como con .NET Core.
### ¿GroupDocs.Parser conserva el formato durante la extracción de texto?
Sí, GroupDocs.Parser puede conservar formatos como fuentes, estilos y diseño durante la extracción de texto.
### ¿Puedo extraer metadatos de documentos usando GroupDocs.Parser?
Sí, GroupDocs.Parser permite extraer metadatos como autor, fecha de creación y más de los tipos de documentos admitidos.
### ¿Existe una prueba gratuita disponible para GroupDocs.Parser?
 Sí, puedes descargar una prueba gratuita desde[aquí](https://releases.groupdocs.com/).