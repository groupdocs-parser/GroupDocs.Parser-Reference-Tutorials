---
title: Extraiga texto de una página en PDF en modo sin formato
linktitle: Extraiga texto de una página en PDF en modo sin formato
second_title: API GroupDocs.Parser .NET
description: Extraiga texto de archivos PDF utilizando GroupDocs.Parser en C#. Aprenda a extraer texto PDF de forma eficiente con esta potente biblioteca .NET.
weight: 16
url: /es/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
type: docs
---
# Extraiga texto de una página en PDF en modo sin formato

## Introducción
En este tutorial, exploraremos cómo usar GroupDocs.Parser para .NET para extraer texto de páginas en documentos PDF usando el modo sin formato. GroupDocs.Parser es una poderosa herramienta que permite a los desarrolladores trabajar con varios formatos de documentos mediante programación.
## Requisitos previos
Antes de comenzar este tutorial, asegúrese de tener lo siguiente:
- Visual Studio instalado en su máquina.
- Conocimientos básicos de programación en C#.
- Biblioteca GroupDocs.Parser para .NET, que puede[descarga aquí](https://releases.groupdocs.com/parser/net/).
- Un archivo PDF de muestra para fines de prueba.

## Importar espacios de nombres
Primero, asegúrese de importar los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Paso 1: crear una instancia de la clase Parser
 Para comenzar, cree una instancia del`Parser`class proporcionando la ruta a su archivo PDF de muestra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Tu código va aquí
}
```
## Paso 2: obtener información del documento e iterar sobre las páginas
A continuación, recupere la información del documento y repita cada página para extraer el texto.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Su código para la extracción de texto va aquí
}
```
## Paso 3: extraiga el texto de cada página
 Dentro del bucle, utilice el`GetText` Método para extraer texto de cada página e imprimirlo.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusión
 En este tutorial, aprendimos cómo extraer texto de páginas PDF en modo sin formato usando GroupDocs.Parser para .NET. Este proceso implica la creación de un`Parser` Por ejemplo, obtener información del documento, iterar sobre cada página y extraer texto utilizando el`GetText` método.

## Preguntas frecuentes
### ¿Qué es GroupDocs.Parser para .NET?
GroupDocs.Parser para .NET es una API de análisis de documentos que permite a los desarrolladores extraer texto, metadatos y otra información de varios formatos de archivos mediante programación.
### ¿Cómo descargo GroupDocs.Parser para .NET?
 Puedes descargar la biblioteca desde[Sitio web de GroupDocs](https://releases.groupdocs.com/parser/net/).
### ¿Hay una prueba gratuita disponible?
 Sí, puede acceder a una prueba gratuita de GroupDocs.Parser para .NET desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar soporte para GroupDocs.Parser para .NET?
 Para asistencia técnica y apoyo comunitario, visite el[Foro de documentos de grupo](https://forum.groupdocs.com/c/parser/17).
### ¿Cómo puedo adquirir una licencia de GroupDocs.Parser para .NET?
 Puede adquirir una licencia en el[pagina de compra](https://purchase.groupdocs.com/buy) o adquirir una licencia temporal[aquí](https://purchase.groupdocs.com/temporary-license/).