---
title: Extraire les hyperliens de la page du document
linktitle: Extraire les hyperliens de la page du document
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des hyperliens à partir de documents à l’aide de GroupDocs.Parser pour .NET. Guide étape par étape pour l’extraction de liens hypertexte en C#.
type: docs
weight: 11
url: /fr/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Parser pour .NET pour extraire étape par étape des hyperliens à partir de documents. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs d'analyser divers formats de documents et d'extraire du texte, des métadonnées et d'autres éléments.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio : installez Visual Studio sur votre machine de développement.
-  Bibliothèque GroupDocs.Parser : téléchargez et référencez la bibliothèque GroupDocs.Parser. Vous pouvez l'obtenir de[ici](https://releases.groupdocs.com/parser/net/).
- Exemple de document : préparez un exemple de document (par exemple, DOCX, PDF) contenant des hyperliens pour les tests.

## Importer des espaces de noms
Tout d’abord, incluez les espaces de noms nécessaires pour utiliser les fonctionnalités de GroupDocs.Parser :
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance d'analyseur
 Instancier le`Parser` class avec le chemin d’accès à votre exemple de document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Le code va ici...
}
```
## Étape 2 : Vérifiez la prise en charge de l’extraction de liens hypertexte
Assurez-vous que le document prend en charge l’extraction de liens hypertexte avant de continuer.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Étape 3 : Récupérer les informations du document
Obtenez des informations de base sur le document et vérifiez s'il contient des pages.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Étape 4 : Parcourir les pages du document
Parcourez chaque page du document.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extraire les hyperliens de la page actuelle
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Itérer sur les hyperliens extraits
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Ligne vierge pour plus de lisibilité
    }
}
```

## Conclusion
Dans ce didacticiel, nous avons couvert les bases de l'utilisation de GroupDocs.Parser pour .NET pour extraire des hyperliens à partir de documents. Vous avez appris à initialiser l'analyseur, à vérifier la prise en charge des hyperliens, à récupérer des informations sur le document et à parcourir les pages du document pour extraire efficacement les hyperliens.

## FAQ
### Puis-je extraire des hyperliens à partir de différents formats de documents ?
Oui, GroupDocs.Parser prend en charge divers formats tels que DOCX, PDF, PPTX, etc., pour l'extraction de liens hypertexte.
### GroupDocs.Parser est-il facile à intégrer dans les applications .NET existantes ?
Absolument, GroupDocs.Parser est conçu pour être simple et peut être facilement intégré à vos projets .NET.
### Puis-je extraire d’autres métadonnées ainsi que des hyperliens à l’aide de GroupDocs.Parser ?
Oui, outre les hyperliens, vous pouvez extraire du texte, des images et des métadonnées de documents à l'aide de cette bibliothèque.
### GroupDocs.Parser gère-t-il les documents chiffrés ou protégés par mot de passe ?
GroupDocs.Parser peut analyser les documents protégés par mot de passe si le mot de passe est fourni.
### Existe-t-il une version d'essai disponible pour tester avant d'acheter ?
 Oui, vous pouvez télécharger une version d'essai gratuite[ici](https://releases.groupdocs.com/).