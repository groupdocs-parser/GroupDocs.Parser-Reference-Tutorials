---
title: Extraire des images d'un PDF
linktitle: Extraire des images d'un PDF
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des images de documents PDF à l'aide de GroupDocs.Parser pour .NET. Guide étape par étape avec des exemples de code.
type: docs
weight: 12
url: /fr/net/pdf-processing/extract-images-from-pdf/
---
## Introduction
Dans ce didacticiel, nous explorerons comment utiliser GroupDocs.Parser pour .NET pour extraire des images de documents PDF. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs de travailler avec différents formats de documents, notamment PDF, DOCX, PPTX, etc., dans un environnement .NET. En suivant ces étapes, vous pourrez extraire des images de fichiers PDF sans effort.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
- Visual Studio installé sur votre système
- Connaissance de base de la programmation C#
-  Bibliothèque GroupDocs.Parser pour .NET (Télécharger[ici](https://releases.groupdocs.com/parser/net/))

## Importer des espaces de noms
Pour commencer, incluez les espaces de noms nécessaires dans votre fichier de code C#.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance de la classe Parser
 Tout d'abord, créez une instance de`Parser`classe en fournissant le chemin d’accès à votre exemple de fichier PDF.
```csharp
// Créer une instance de la classe Parser
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Le code pour extraire les images ira ici
}
```
## Étape 2 : Extraire les images du PDF
 Au sein du`using` bloquer, utilisez le`GetImages` méthode du`Parser` instance pour récupérer une collection d’images du document PDF.
```csharp
// Extraire des images du PDF
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Étape 3 : configurer les options d'enregistrement des images
Définissez les options pour spécifier comment les images extraites doivent être enregistrées. Ici, nous allons enregistrer les images au format PNG.
```csharp
// Créer des options pour enregistrer les images au format PNG
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Étape 4 : Parcourir les images extraites et enregistrer
 Parcourez chaque image dans le`images` collection et enregistrez-les dans des fichiers PNG de manière séquentielle.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Enregistrez l'image dans un fichier PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```

## Conclusion
Dans ce didacticiel, nous avons montré comment extraire des images de documents PDF à l'aide de GroupDocs.Parser pour .NET. En suivant ces étapes, vous pouvez intégrer de manière transparente la fonctionnalité d'extraction d'images dans vos applications .NET.

## FAQ
### GroupDocs.Parser est-il compatible avec d’autres formats de documents ?
Oui, GroupDocs.Parser prend en charge un large éventail de formats de documents, notamment PDF, DOCX, XLSX, PPTX, etc.
### Puis-je modifier les options d’extraction d’images ?
Absolument! GroupDocs.Parser propose diverses options pour personnaliser l'extraction d'images, telles que le format d'image et les paramètres de qualité.
### GroupDocs.Parser nécessite-t-il une licence pour une utilisation commerciale ?
 Oui, une licence commerciale est requise pour utiliser GroupDocs.Parser dans des environnements de production. Apprendre encore plus[ici](https://purchase.groupdocs.com/buy).
### Où puis-je trouver un soutien ou une assistance supplémentaire ?
 Visitez le GroupDocs.Parser[forum](https://forum.groupdocs.com/c/parser/17) pour le soutien et les conseils de la communauté.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez obtenir un essai gratuit auprès de[ici](https://releases.groupdocs.com/) pour explorer les fonctionnalités de GroupDocs.Parser.