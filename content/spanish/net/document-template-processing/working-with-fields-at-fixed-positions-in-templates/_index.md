---
title: Trabajar con campos en posiciones fijas en plantillas
linktitle: Trabajar con campos en posiciones fijas en plantillas
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer datos de documentos utilizando GroupDocs.Parser para .NET. Tutorial completo con ejemplos de código.
type: docs
weight: 11
url: /es/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## Introducción
En este tutorial, exploraremos cómo trabajar con campos en posiciones fijas dentro de plantillas usando GroupDocs.Parser para .NET. GroupDocs.Parser es una potente biblioteca de análisis de documentos que permite a los desarrolladores extraer datos de varios formatos de documentos, como PDF, Word, Excel y más. Específicamente, nos centraremos en definir y utilizar campos de plantilla para extraer información específica en función de sus posiciones fijas.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Conocimientos básicos del desarrollo de C# y .NET.
- Visual Studio instalado en su sistema.
- Biblioteca GroupDocs.Parser para .NET instalada. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/parser/net/).
- Archivos de documentos de muestra para pruebas.

## Importar espacios de nombres
Comience por incluir los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Paso 1: definir un campo de plantilla
Primero, defina un campo con una posición fija dentro de una plantilla. Este campo representa el área de la cual se extraerán los datos.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Aquí:
- `Rectangle` especifica la posición y el tamaño del campo.
- `Point(35, 135)` representa las coordenadas de la esquina superior izquierda.
- `Size(100, 10)` define el ancho y alto del campo.
- `"FromCompany"` es el nombre asignado a este campo.
## Paso 2: crea una plantilla
Construya una plantilla utilizando el campo definido.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 El`Template` El objeto contiene los campos definidos.
## Paso 3: analizar el documento usando la plantilla
 Instanciar el`Parser` class con la ruta del documento de destino y luego analiza el documento usando la plantilla creada.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Iterar a través de los datos extraídos
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Aquí:
- `Parser` se inicializa con la ruta del archivo del documento de muestra.
- `ParseByTemplate` El método se utiliza para extraer datos según la plantilla proporcionada.
-  Se accede a los datos extraídos mediante`DocumentData`donde cada elemento corresponde a un campo definido.

## Conclusión
En este tutorial, cubrimos el proceso de trabajar con campos en posiciones fijas en plantillas usando GroupDocs.Parser para .NET. Al definir plantillas con posiciones de campo específicas, los desarrolladores pueden extraer con precisión datos específicos de varios formatos de documentos.

## Preguntas frecuentes
### ¿GroupDocs.Parser es compatible con todos los formatos de documentos?
 GroupDocs.Parser admite una amplia gama de formatos de archivo, incluidos PDF, Microsoft Word, Excel, PowerPoint y más. Referirse a[documentación](https://reference.groupdocs.com/parser/net/) para obtener una lista detallada.
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Parser?
 Puede obtener una licencia temporal para fines de prueba en[aquí](https://purchase.groupdocs.com/temporary-license/).
### ¿Dónde puedo encontrar soporte para GroupDocs.Parser?
 Para obtener asistencia técnica y debates, visite el[Foro GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### ¿Puedo probar GroupDocs.Parser antes de comprarlo?
 Sí, puedes explorar la biblioteca con una prueba gratuita disponible.[aquí](https://releases.groupdocs.com/).
### ¿Cómo compro una licencia para GroupDocs.Parser?
 Para comprar una licencia, visite el[pagina de compra](https://purchase.groupdocs.com/buy).