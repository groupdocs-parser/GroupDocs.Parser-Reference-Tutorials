---
title: Travailler avec des champs à des positions fixes dans les modèles
linktitle: Travailler avec des champs à des positions fixes dans les modèles
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des données de documents à l'aide de GroupDocs.Parser pour .NET. Tutoriel complet avec des exemples de code.
weight: 11
url: /fr/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---

# Travailler avec des champs à des positions fixes dans les modèles

## Introduction
Dans ce didacticiel, nous explorerons comment travailler avec des champs à des positions fixes dans des modèles à l'aide de GroupDocs.Parser pour .NET. GroupDocs.Parser est une puissante bibliothèque d'analyse de documents qui permet aux développeurs d'extraire des données de divers formats de documents tels que PDF, Word, Excel, etc. Plus précisément, nous nous concentrerons sur la définition et l'utilisation de champs modèles pour extraire des informations ciblées en fonction de leurs positions fixes.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Compréhension de base du développement C# et .NET.
- Visual Studio installé sur votre système.
- GroupDocs.Parser pour la bibliothèque .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/parser/net/).
- Exemples de fichiers de documents à tester.

## Importer des espaces de noms
Commencez par inclure les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Étape 1 : définir un champ de modèle
Tout d’abord, définissez un champ avec une position fixe dans un modèle. Ce champ représente la zone à partir de laquelle les données seront extraites.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Ici:
- `Rectangle` spécifie la position et la taille du champ.
- `Point(35, 135)` représente les coordonnées du coin supérieur gauche.
- `Size(100, 10)` définit la largeur et la hauteur du champ.
- `"FromCompany"` est le nom attribué à ce champ.
## Étape 2 : créer un modèle
Construisez un modèle en utilisant le champ défini.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 Le`Template` L'objet contient les champs définis.
## Étape 3 : analyser le document à l'aide du modèle
 Instancier le`Parser` classe avec le chemin du document cible, puis analysez le document à l'aide du modèle créé.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Parcourez les données extraites
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Ici:
- `Parser` est initialisé avec le chemin du fichier d’exemple de document.
- `ParseByTemplate` La méthode est utilisée pour extraire des données sur la base du modèle fourni.
-  Les données extraites sont accessibles en utilisant`DocumentData`où chaque élément correspond à un champ défini.

## Conclusion
Dans ce didacticiel, nous avons couvert le processus de travail avec des champs à des positions fixes dans des modèles à l'aide de GroupDocs.Parser pour .NET. En définissant des modèles avec des positions de champ spécifiques, les développeurs peuvent extraire avec précision des données ciblées à partir de différents formats de documents.

## FAQ
### GroupDocs.Parser est-il compatible avec tous les formats de documents ?
 GroupDocs.Parser prend en charge un large éventail de formats de fichiers, notamment PDF, Microsoft Word, Excel, PowerPoint, etc. Se référer au[Documentation](https://tutorials.groupdocs.com/parser/net/) pour une liste détaillée.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez obtenir une licence temporaire à des fins de test auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je trouver de l’assistance pour GroupDocs.Parser ?
 Pour une assistance technique et des discussions, visitez le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Puis-je essayer GroupDocs.Parser avant d’acheter ?
 Oui, vous pouvez explorer la bibliothèque avec un essai gratuit disponible[ici](https://releases.groupdocs.com/).
### Comment acheter une licence pour GroupDocs.Parser ?
 Pour acheter une licence, visitez le[page d'achat](https://purchase.groupdocs.com/buy).