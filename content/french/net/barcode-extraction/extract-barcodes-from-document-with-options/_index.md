---
title: Extraire les codes-barres du document avec des options
linktitle: Extraire les codes-barres du document avec des options
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des codes-barres de documents à l'aide de GroupDocs.Parser pour .NET. Tutoriel complet avec des exemples de code et des FAQ.
type: docs
weight: 14
url: /fr/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## Introduction
Dans ce didacticiel, nous allons parcourir le processus d'extraction de codes-barres d'un document à l'aide de GroupDocs.Parser pour .NET. GroupDocs.Parser est une bibliothèque puissante qui vous permet d'extraire du texte, des métadonnées et des codes-barres à partir de divers formats de documents tels que PDF, Microsoft Word, Excel, etc.
## Conditions préalables
Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
1. Environnement de développement : assurez-vous que Visual Studio est installé sur votre ordinateur.
2.  Bibliothèque GroupDocs.Parser : téléchargez et installez la bibliothèque GroupDocs.Parser pour .NET à partir de[ici](https://releases.groupdocs.com/parser/net/).
3. Exemple de document : préparez un exemple de document (par exemple, PDF, DOCX) contenant des codes-barres pour l'extraction.

## Importer des espaces de noms
Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre projet C# pour utiliser les fonctionnalités GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Étape 1 : Créer une instance de la classe Parser
 Pour commencer, créez une instance de`Parser` classe en transmettant le chemin d’accès à votre exemple de document.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code à ajouter dans les prochaines étapes
}
```
## Étape 2 : Vérifiez la prise en charge de l'extraction de codes-barres
 Ensuite, vérifiez si le document prend en charge l'extraction de codes-barres à l'aide du`Features` propriété du`Parser` exemple.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Étape 3 : Définir les options d'extraction de codes-barres
 Maintenant, spécifiez les options d'extraction des codes-barres en utilisant`BarcodeOptions`. Vous pouvez définir des paramètres tels que les modes de qualité et les types de codes-barres.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Étape 4 : Extraire les codes-barres du document
 Utilisez le`GetBarcodes` méthode du`Parser` classe pour extraire les codes-barres en fonction des options définies.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Étape 5 : Itérer et afficher les codes-barres extraits
Enfin, parcourez les codes-barres extraits et affichez leur index de page et leurs valeurs.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Conclusion
 Dans ce didacticiel, nous avons appris à extraire les codes-barres d'un document à l'aide de GroupDocs.Parser pour .NET. Ce processus consiste à créer un`Parser` par exemple, en définissant les options d'extraction et en parcourant les codes-barres extraits. GroupDocs.Parser simplifie la tâche d'extraction de codes-barres à partir de divers formats de documents, permettant un traitement efficace des documents au sein de vos applications .NET.

## FAQ
### GroupDocs.Parser peut-il extraire les codes-barres des documents PDF ?
Oui, GroupDocs.Parser prend en charge l'extraction de codes-barres à partir de documents PDF ainsi que d'autres formats tels que DOCX, XLSX, etc.
### Quels types de codes-barres GroupDocs.Parser prend-il en charge ?
GroupDocs.Parser prend en charge différents types de codes-barres, notamment les codes QR, le code 39, le code 128, etc.
### GroupDocs.Parser nécessite-t-il une licence pour une utilisation commerciale ?
 Oui, une licence valide est requise pour une utilisation commerciale. Vous pouvez obtenir une licence auprès de[ici](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser est-il adapté au traitement par lots de documents ?
Oui, GroupDocs.Parser peut gérer efficacement le traitement par lots de documents pour l'extraction de texte, la récupération de métadonnées et l'extraction de codes-barres.
### Où puis-je trouver une assistance technique pour GroupDocs.Parser ?
 Vous pouvez obtenir une assistance technique ou poser des questions sur le[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17).