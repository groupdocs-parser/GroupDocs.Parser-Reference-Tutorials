---
title: Rechercher du texte par expression régulière (Regex)
linktitle: Rechercher du texte par expression régulière (Regex)
second_title: API GroupDocs.Parser .NET
description: Découvrez comment rechercher du texte à l'aide d'expressions régulières dans des documents à l'aide de GroupDocs.Parser pour .NET. Extrayez du contenu spécifique sans effort.
weight: 23
url: /fr/net/text-extraction/search-text-by-regex/
---

# Rechercher du texte par expression régulière (Regex)

## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Parser pour .NET pour rechercher du texte par expression régulière (Regex) dans des documents. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs d'extraire du texte et des métadonnées de divers formats de fichiers tels que PDF, DOCX, XLSX, etc. La recherche de texte à l'aide d'expressions régulières est particulièrement utile pour trouver efficacement des modèles ou du contenu spécifique dans des documents.
## Conditions préalables
Avant de plonger dans ce didacticiel, assurez-vous d'avoir les éléments suivants :
1. Visual Studio : installez Visual Studio IDE pour le développement .NET.
2.  GroupDocs.Parser pour .NET : téléchargez et installez GroupDocs.Parser pour .NET à partir de[ici](https://releases.groupdocs.com/parser/net/).
3. Exemple de fichier : préparez un exemple de document (PDF, DOCX, etc.) pour tester la fonctionnalité de recherche.

## Importer des espaces de noms
Tout d’abord, commencez par inclure les espaces de noms nécessaires dans votre code C# :
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance de la classe Parser
 Instancier le`Parser` class en fournissant le chemin d'accès à votre exemple de fichier :
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Le code va ici
}
```
 Remplacer`"YourSampleFile.pdf"` avec le chemin d'accès à votre fichier actuel.
## Étape 2 : Recherche à l'aide d'une expression régulière
Définissez et exécutez la recherche à l'aide d'un modèle d'expression régulière. Par exemple, pour rechercher des séquences numériques (par exemple des entiers) dans le document :
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 Dans cet exemple,`[0-9]+` est un modèle d'expression régulière qui correspond à un ou plusieurs chiffres.
## Étape 3 : Vérifiez le support de recherche
Vérifiez si l'opération de recherche est prise en charge pour le type de document :
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Étape 4 : Parcourir les résultats de recherche
Parcourez les résultats de la recherche et traitez chaque correspondance :
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Cette boucle imprimera la position et le texte correspondant trouvé dans le document.

## Conclusion
En conclusion, l'utilisation de GroupDocs.Parser pour .NET permet une recherche de texte efficace à l'aide d'expressions régulières dans différents formats de documents. En suivant ce guide, les développeurs peuvent intégrer de manière transparente l'analyse de documents et l'extraction de texte basée sur les expressions régulières dans leurs applications .NET.

## FAQ
### GroupDocs.Parser peut-il effectuer une recherche dans des documents cryptés ?
Non, GroupDocs.Parser ne peut pas effectuer de recherche dans des documents cryptés ou protégés par mot de passe.
### GroupDocs.Parser prend-il en charge l'OCR (reconnaissance optique de caractères) ?
Non, GroupDocs.Parser n'effectue pas d'OCR. Il repose sur l'extraction de texte de la structure interne du document.
### Puis-je rechercher des modèles complexes à l’aide d’expressions régulières ?
Oui, GroupDocs.Parser prend en charge les expressions régulières à part entière, permettant une correspondance de modèles complexes dans les documents.
### Quels formats de documents sont pris en charge pour l'extraction de texte ?
GroupDocs.Parser prend en charge une large gamme de formats, notamment PDF, DOCX, XLSX, PPTX, etc.
### GroupDocs.Parser est-il compatible avec .NET Core ?
Oui, GroupDocs.Parser est compatible avec .NET Core pour le développement multiplateforme.