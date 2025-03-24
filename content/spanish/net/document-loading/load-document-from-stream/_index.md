---
title: Cargar documento desde la secuencia
linktitle: Cargar documento desde la secuencia
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer texto de varios formatos de documentos en .NET usando GroupDocs.Parser. Guía paso a paso con ejemplos de código.
weight: 12
url: /es/net/document-loading/load-document-from-stream/
---

# Cargar documento desde la secuencia

## Introducción
En el ámbito del procesamiento de documentos en aplicaciones .NET, extraer texto de varios formatos de archivo es un requisito común. GroupDocs.Parser para .NET ofrece una potente solución para analizar y extraer texto sin problemas de una amplia gama de documentos. Este tutorial lo guiará a través del proceso de utilización de GroupDocs.Parser para extraer texto de documentos paso a paso.
## Requisitos previos
Antes de sumergirse en el uso de GroupDocs.Parser para .NET, asegúrese de tener la siguiente configuración:
- Entorno de desarrollo: Visual Studio o cualquier otro entorno de desarrollo .NET.
-  Paquete GroupDocs.Parser para .NET: descargue e instale la biblioteca GroupDocs.Parser para .NET desde[aquí](https://releases.groupdocs.com/parser/net/).
- Muestras de documentos: tenga documentos de muestra listos para la extracción de texto.
## Importando espacios de nombres
Comience importando los espacios de nombres necesarios a su proyecto .NET para acceder a las funcionalidades de GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Los siguientes pasos demuestran cómo extraer texto de un documento usando GroupDocs.Parser de una secuencia.
## Paso 1: cargar el documento desde la secuencia
```csharp
// Crear la transmisión
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Cree una instancia de la clase Parser con la secuencia
    using (Parser parser = new Parser(stream))
    {
        // Extraer texto en el lector.
        using (TextReader reader = parser.GetText())
        {
            // Imprimir texto del documento
            // Si no se admite la extracción de texto, el lector será nulo
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
En este ejemplo:
- Abrimos una secuencia de archivos para el archivo del documento (`YourSampleFile.docx`).
-  Inicializar un`Parser` instancia con la corriente.
-  Usar`parser.GetText()` para recuperar un`TextReader` que contiene el texto extraído.
- Imprima el texto extraído o un mensaje si la extracción de texto no es compatible con el formato del documento.
## Conclusión
GroupDocs.Parser para .NET simplifica la extracción de texto de varios formatos de documentos, lo que permite a los desarrolladores procesar y utilizar de manera eficiente contenido textual dentro de sus aplicaciones. Si sigue los pasos descritos en este tutorial, podrá integrar perfectamente las capacidades de extracción de texto de documentos en sus proyectos .NET.

## Preguntas frecuentes
### ¿Qué formatos de documentos admite GroupDocs.Parser para .NET?
GroupDocs.Parser admite una amplia gama de formatos de documentos, incluidos DOCX, PDF, XLSX, PPTX, EPUB y más.
### ¿Puede GroupDocs.Parser extraer imágenes o metadatos de documentos?
Sí, GroupDocs.Parser puede extraer imágenes, metadatos y texto de varios tipos de documentos.
### ¿GroupDocs.Parser es compatible con aplicaciones .NET Core?
Sí, GroupDocs.Parser es compatible con aplicaciones .NET Framework y .NET Core.
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Parser?
 Puede obtener una licencia temporal de[aquí](https://purchase.groupdocs.com/temporary-license/).
### ¿Dónde puedo encontrar más soporte o documentación para GroupDocs.Parser?
 Para obtener soporte adicional, visite el[Foro GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) o referirse a la[documentación](https://tutorials.groupdocs.com/parser/net/).
