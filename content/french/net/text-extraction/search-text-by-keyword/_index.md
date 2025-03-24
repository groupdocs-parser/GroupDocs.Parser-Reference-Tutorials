---
title: Rechercher du texte par mot-clé
linktitle: Rechercher du texte par mot-clé
second_title: API GroupDocs.Parser .NET
description: Découvrez comment rechercher du texte par mot-clé dans des documents à l'aide de GroupDocs.Parser pour .NET. Extrayez efficacement et facilement le contenu pertinent.
weight: 21
url: /fr/net/text-extraction/search-text-by-keyword/
---
## Introduction
Dans ce didacticiel, nous allons explorer l'utilisation de GroupDocs.Parser pour .NET pour rechercher du texte par mot-clé dans les documents. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs d'extraire du texte, des métadonnées et d'autres informations à partir de divers formats de fichiers, tels que des PDF, des documents Microsoft Office, etc. La recherche de mots-clés spécifiques dans ces documents peut s'avérer essentielle pour les applications traitant de gros volumes de données textuelles.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir la configuration suivante :
1. Environnement de développement : Visual Studio ou tout autre IDE .NET préféré.
2.  GroupDocs.Parser pour .NET : téléchargez la bibliothèque depuis[ici](https://releases.groupdocs.com/parser/net/).
3. Accès aux exemples de fichiers : préparez un exemple de fichier (par exemple, PDF, DOCX) pour tester la fonctionnalité de recherche par mot clé.

## Importer des espaces de noms
Tout d'abord, vous devez inclure les espaces de noms nécessaires dans votre projet.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Étape 1 : instancier la classe Parser
 Commencez par créer une instance de`Parser` class et fournissez le chemin d’accès à votre exemple de fichier.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Rechercher un mot-clé
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Parcourir les résultats de recherche
    foreach (SearchResult result in searchResults)
    {
        //Imprimer l'index et le texte trouvé
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Étape 2 : Rechercher un mot-clé
 Au sein du`using` bloquer, appeler le`Search` méthode sur le`parser` objet, en passant le mot-clé souhaité comme argument.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Remplacer`"test"` avec le mot-clé que vous souhaitez rechercher dans le document.
## Étape 3 : Parcourir les résultats de recherche
 Ensuite, parcourez les résultats de recherche obtenus à partir du`Search` méthode utilisant un`foreach` boucle.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Pour chaque`SearchResult` objet`result` , vous pouvez accéder à son`Position` (indice) et`Text` (le texte trouvé).

## Conclusion
 Dans ce didacticiel, nous avons expliqué comment utiliser GroupDocs.Parser pour .NET pour rechercher sans effort du texte par mot-clé dans des documents. Tirer parti du`Search` méthode du`Parser` La classe permet une récupération efficace d'extraits de texte pertinents en fonction de termes de recherche spécifiques.

## FAQ
### GroupDocs.Parser est-il compatible avec différents formats de documents ?
Oui, GroupDocs.Parser prend en charge un large éventail de formats de fichiers, notamment PDF, DOCX, XLSX, PPTX, etc.
### Puis-je effectuer des opérations avancées d’extraction de texte à l’aide de GroupDocs.Parser ?
Absolument! Outre la recherche de texte, GroupDocs.Parser permet l'extraction de métadonnées, l'extraction de texte structuré, etc.
### Où puis-je trouver une documentation détaillée pour GroupDocs.Parser ?
Explorez la documentation complète[ici](https://tutorials.groupdocs.com/parser/net/).
### Comment puis-je obtenir de l'aide ou de l'assistance pour les requêtes liées à GroupDocs.Parser ?
 Visitez le forum GroupDocs pour obtenir de l'aide et des discussions[ici](https://forum.groupdocs.com/c/parser/17).
### Existe-t-il une version d'essai disponible pour évaluer GroupDocs.Parser avant d'acheter ?
 Oui, vous pouvez accéder à l'essai gratuit[ici](https://releases.groupdocs.com/).