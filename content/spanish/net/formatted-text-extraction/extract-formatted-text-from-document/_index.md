---
title: Extraer texto formateado del documento
linktitle: Extraer texto formateado del documento
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer texto formateado de documentos usando GroupDocs.Parser para .NET. Extracción de texto simple y eficiente para sus aplicaciones.
weight: 10
url: /es/net/formatted-text-extraction/extract-formatted-text-from-document/
type: docs
---
# Extraer texto formateado del documento

## Introducción
En este tutorial, exploraremos cómo usar GroupDocs.Parser para .NET para extraer texto formateado de varios tipos de documentos. GroupDocs.Parser es una potente biblioteca que permite a los desarrolladores trabajar con documentos de forma simplificada y eficiente. Al final de esta guía, podrá integrar perfectamente capacidades de extracción de texto en sus aplicaciones .NET.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Visual Studio: asegúrese de tener Visual Studio instalado en su sistema.
-  GroupDocs.Parser para .NET: descargue e instale la biblioteca GroupDocs.Parser desde[aquí](https://releases.groupdocs.com/parser/net/).
- Muestras de documentos: prepare documentos de muestra (p. ej., PDF, DOCX) para la extracción de texto.
## Importar espacios de nombres
Primero, incluya los espacios de nombres necesarios en su código C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Paso 1: crear una instancia de la clase Parser
 Comience por inicializar un`Parser` objeto con la ruta a su documento de muestra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // El código de extracción de texto va aquí
}
```
 Reemplazar`"YourSampleFile.pdf"` con la ruta a su archivo de documento.

## Paso 2: extraer texto formateado
 Dentro de`using` bloquear, utilice el`GetFormattedText` Método para extraer texto formateado del documento. Especifique el formato de salida deseado (por ejemplo, HTML) usando`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extraer texto formateado en el lector.
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Compruebe si se admite la extracción
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Leer y mostrar el texto extraído.
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Conclusión
¡Felicidades! Ha aprendido a extraer texto formateado de documentos utilizando GroupDocs.Parser para .NET. Esta biblioteca versátil abre posibilidades para el procesamiento y análisis de texto dentro de sus aplicaciones.

## Preguntas frecuentes
### P: ¿Puede GroupDocs.Parser extraer texto de documentos protegidos con contraseña?
R: Sí, GroupDocs.Parser admite la extracción de texto de documentos protegidos con contraseña.
### P: ¿Qué formatos de documentos admite GroupDocs.Parser?
R: GroupDocs.Parser admite una amplia gama de formatos, incluidos PDF, DOCX, XLSX, PPTX y más.
### P: ¿Cómo puedo obtener una licencia temporal para GroupDocs.Parser?
 R: Puede obtener una licencia temporal de[aquí](https://purchase.groupdocs.com/temporary-license/).
### P: ¿GroupDocs.Parser proporciona soporte para la extracción de imágenes de documentos?
R: Sí, GroupDocs.Parser admite la extracción de imágenes junto con la extracción de texto.
### P: ¿Dónde puedo encontrar soporte adicional o hacer preguntas sobre GroupDocs.Parser?
 R: Visita el[Foro GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)para apoyo y discusiones.