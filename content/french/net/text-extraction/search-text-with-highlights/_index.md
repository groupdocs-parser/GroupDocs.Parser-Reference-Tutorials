---
title: Rechercher du texte avec des surbrillances
linktitle: Rechercher du texte avec des surbrillances
second_title: API GroupDocs.Parser .NET
description: Découvrez comment rechercher et surligner du texte dans des documents à l'aide de GroupDocs.Parser pour .NET. Extrayez efficacement des informations précieuses.
weight: 24
url: /fr/net/text-extraction/search-text-with-highlights/
---

# Rechercher du texte avec des surbrillances

## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Parser pour .NET pour rechercher du texte dans un document et mettre en évidence les résultats de la recherche. GroupDocs.Parser est une bibliothèque puissante qui vous permet de travailler avec différents formats de documents et d'extraire du texte, des métadonnées, etc.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  GroupDocs.Parser pour .NET : téléchargez et installez la bibliothèque à partir de[ici](https://releases.groupdocs.com/parser/net/).
2. IDE : utilisez Visual Studio ou tout autre IDE préféré pour le développement .NET.
3. Exemple de fichier : préparez un exemple de document (par exemple, PDF, DOCX) pour la recherche de texte.

## Importer des espaces de noms
Tout d’abord, commencez par importer les espaces de noms nécessaires dans votre projet .NET :
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance d'analyseur
 Commencez par instancier le`Parser` class avec le chemin d'accès à votre exemple de fichier :
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Votre code ici
}
```
## Étape 2 : Définir les options de surbrillance
 Spécifie le`HighlightOptions` pour configurer la façon dont les résultats de recherche doivent être mis en évidence. Par exemple, définir une fenêtre contextuelle de 15 caractères :
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Étape 3 : Rechercher du texte
Maintenant, effectuez une recherche de texte dans le document. Fournissez le mot-clé que vous souhaitez rechercher (par exemple, « lorem ») :
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Étape 4 : Traiter les résultats de la recherche
Parcourez les résultats de la recherche et affichez le texte trouvé ainsi que les surlignages :
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Conclusion
Dans ce didacticiel, vous avez appris à utiliser GroupDocs.Parser pour .NET pour rechercher du texte dans des documents et mettre en évidence les résultats de la recherche. Cette fonctionnalité peut être extrêmement utile pour l'extraction et l'analyse de texte dans vos applications .NET.

## FAQ
### GroupDocs.Parser est-il adapté au traitement de différents formats de documents ?
Oui, GroupDocs.Parser prend en charge un large éventail de formats de documents, notamment PDF, DOCX, XLSX, PPTX, etc.
### Puis-je utiliser GroupDocs.Parser pour extraire les métadonnées des documents ?
Absolument! GroupDocs.Parser vous permet d'extraire des métadonnées, du texte et des données structurées à partir de documents.
### Où puis-je trouver de l’aide ou poser des questions sur GroupDocs.Parser ?
 Vous pouvez visiter le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) pour toute question relative au support.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez accéder à un[essai gratuit](https://releases.groupdocs.com/) de GroupDocs.Parser pour évaluer ses fonctionnalités.
### Comment puis-je acheter une licence pour GroupDocs.Parser ?
 Vous pouvez acheter une licence auprès de[ici](https://purchase.groupdocs.com/buy) et également obtenir des licences temporaires[ici](https://purchase.groupdocs.com/temporary-license/).