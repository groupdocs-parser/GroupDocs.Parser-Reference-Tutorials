---
title: Extraire des images de la page du document
linktitle: Extraire des images de la page du document
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des images de documents à l'aide de GroupDocs.Parser pour .NET. Améliorez vos capacités de traitement de documents.
type: docs
weight: 12
url: /fr/net/image-extraction/extract-images-from-document-page/
---
## Introduction
Dans ce didacticiel, nous apprendrons comment extraire des images d'une page de document à l'aide de GroupDocs.Parser pour .NET. GroupDocs.Parser est une bibliothèque puissante qui vous permet d'extraire du texte, des métadonnées, des images et bien plus encore à partir de divers formats de documents tels que PDF, Microsoft Word, Excel, PowerPoint et autres. Nous passerons en revue les étapes nécessaires pour extraire des images d'une page de document à l'aide de cette bibliothèque.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio installé sur votre ordinateur.
- Compréhension de base de la programmation C# et .NET.
- GroupDocs.Parser pour la bibliothèque .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/parser/net/).

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires dans votre projet C# pour utiliser les fonctionnalités de GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance de la classe Parser
 Commencez par créer une instance de`Parser` class et spécifiez le chemin d’accès à votre exemple de document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Votre code ici
}
```
## Étape 2 : Vérifier le document pour la prise en charge de l'extraction d'images
 Ensuite, vérifiez si le document prend en charge l'extraction d'images à l'aide du`Features.Images` propriété.
```csharp
if (!parser.Features.Images)
{
    Console.WriteLine("Document doesn't support image extraction.");
    return;
}
```
## Étape 3 : obtenir des informations sur le document
 Récupérer des informations sur le document à l'aide de l'outil`GetDocumentInfo()` méthode.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Étape 4 : Parcourir les pages du document
Vérifiez si le document contient des pages, puis parcourez chaque page pour extraire des images.
```csharp
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Votre code pour extraire les images de la page
}
```
## Étape 5 : Extraire les images de chaque page
 Dans la boucle d'itération de page, utilisez le`GetImages(pageIndex)` méthode pour récupérer les images de chaque page.
```csharp
foreach (PageImageArea image in parser.GetImages(pageIndex))
{
    Console.WriteLine($"Rectangle: {image.Rectangle}, FileType: {image.FileType}");
    // Code supplémentaire pour enregistrer ou traiter l'image
}
```

## Conclusion
Dans ce didacticiel, nous avons exploré comment extraire des images d'une page de document à l'aide de GroupDocs.Parser pour .NET. Nous avons couvert des étapes essentielles telles que la création d'une instance d'analyseur, la vérification de la prise en charge de l'extraction d'images, la récupération des informations sur le document, l'itération sur les pages et l'extraction d'images de chaque page. Vous pouvez désormais intégrer efficacement la fonctionnalité d’extraction d’images dans vos applications .NET.

## FAQ
### GroupDocs.Parser peut-il extraire des images de documents PDF ?
Oui, GroupDocs.Parser prend en charge l'extraction d'images à partir de divers formats de documents, y compris PDF.
### GroupDocs.Parser est-il adapté au traitement par lots de documents ?
Absolument! Vous pouvez utiliser GroupDocs.Parser pour traiter par lots plusieurs documents et extraire efficacement le contenu souhaité.
### Où puis-je trouver plus de ressources et d’assistance pour GroupDocs.Parser ?
 Vous pouvez visiter le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) pour le soutien et les discussions de la communauté.
### Puis-je essayer GroupDocs.Parser avant d’acheter ?
 Oui, vous pouvez obtenir un[version d'essai gratuite](https://releases.groupdocs.com/) pour évaluer les capacités de la bibliothèque.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez acquérir un[permis temporaire](https://purchase.groupdocs.com/temporary-license/) à des fins de tests et de développement.