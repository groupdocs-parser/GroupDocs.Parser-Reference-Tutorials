---
title: Cargar documento desde el disco local
linktitle: Cargar documento desde el disco local
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer texto de varios formatos de documentos utilizando GroupDocs.Parser para .NET. Extracción de texto fácil y eficiente con C#.
weight: 11
url: /es/net/document-loading/load-document-from-local-disk/
---

# Cargar documento desde el disco local

## Introducción
En este tutorial, exploraremos cómo usar GroupDocs.Parser para .NET para extraer texto de documentos. GroupDocs.Parser es una poderosa biblioteca que permite a los desarrolladores analizar varios formatos de documentos y extraer contenido de texto mediante programación. Cubriremos los pasos necesarios para comenzar con la extracción de texto usando esta biblioteca.
## Requisitos previos
Antes de comenzar, asegúrese de tener instalados los siguientes requisitos previos:
- Visual Studio instalado en su sistema.
- Conocimientos básicos del lenguaje de programación C#.
-  Biblioteca GroupDocs.Parser para .NET instalada (descargar[aquí](https://releases.groupdocs.com/parser/net/)).

## Importar espacios de nombres
Primero, necesita importar los espacios de nombres necesarios a su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Paso 1: cargar el documento desde el disco local
 Comience cargando un documento desde su disco local. Reemplazar`"Your Sample File"` con la ruta al documento de destino.
```csharp
// Establecer la ruta del archivo
string filePath = "Your Sample File";
// Cree una instancia de la clase Parser con filePath
using (Parser parser = new Parser(filePath))
{
    // Extraer texto en el lector.
    using (TextReader reader = parser.GetText())
    {
        //Imprime el texto extraído del documento.
        // Si no se admite la extracción de texto, el lector será nulo
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Explicación de pasos
1. Configuración de la ruta del archivo: comience especificando la ruta al documento del que desea extraer el texto (`filePath` variable).
2.  Creación de una instancia de analizador: crear una instancia del`Parser` clase pasando el`filePath`.
3.  Extracción de texto: utilice el`GetText()` método de la`Parser` instancia para obtener un`TextReader` objeto que contiene el texto extraído del documento.
4.  Lectura de texto extraído: utilice el`ReadToEnd()` método de la`TextReader` para recuperar todo el contenido del texto extraído del documento.
5.  Manejo de formatos no admitidos: si el formato del documento no admite la extracción de texto, el`reader` objeto será`null`y podrá manejar este escenario en consecuencia.

## Conclusión
En este tutorial, cubrimos los pasos iniciales para extraer texto de un documento usando GroupDocs.Parser para .NET. Esta biblioteca ofrece amplias funciones para el análisis de documentos, lo que permite a los desarrolladores trabajar de manera eficiente con varios formatos de archivos dentro de sus aplicaciones.

## Preguntas frecuentes
### ¿GroupDocs.Parser es compatible con todos los formatos de documentos?
GroupDocs.Parser admite una amplia gama de formatos, incluidos PDF, documentos de Microsoft Office (Word, Excel, PowerPoint) y más.
### ¿Puedo extraer metadatos junto con texto usando GroupDocs.Parser?
Sí, GroupDocs.Parser permite la extracción tanto de contenido de texto como de metadatos de formatos de documentos compatibles.
### ¿Dónde puedo encontrar más recursos y soporte para GroupDocs.Parser?
 Visita el[Documentación de GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) para obtener una referencia API detallada y explorar el[Foro de GroupDocs](https://forum.groupdocs.com/c/parser/17) para el apoyo de la comunidad.
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Parser?
 Puedes solicitar un[licencia temporal](https://purchase.groupdocs.com/temporary-license/) para fines de evaluación y prueba.
### ¿Existe una prueba gratuita disponible para GroupDocs.Parser?
 Sí, puedes descargar un[prueba gratis](https://releases.groupdocs.com/) versión de GroupDocs.Parser.