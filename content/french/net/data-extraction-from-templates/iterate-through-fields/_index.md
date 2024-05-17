---
title: Parcourir les champs
linktitle: Parcourir les champs
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des données structurées à partir de documents à l'aide de GroupDocs.Parser pour .NET. Améliorez vos applications .NET avec des capacités d'extraction de données documentaires.
type: docs
weight: 11
url: /fr/net/data-extraction-from-templates/iterate-through-fields/
---
## Introduction
GroupDocs.Parser pour .NET est une bibliothèque puissante qui permet aux développeurs d'extraire des données de divers formats de documents tels que PDF, Microsoft Word, Excel et PowerPoint. Ce didacticiel vous guidera tout au long du processus d'utilisation de GroupDocs.Parser pour parcourir les champs du document et extraire des données spécifiques à l'aide de modèles. À la fin de ce didacticiel, vous serez en mesure d'extraire efficacement des données structurées à partir de documents dans vos applications .NET.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir configuré les conditions préalables suivantes :
- Connaissance de base de la programmation C#.
- Visual Studio installé sur votre ordinateur.
- Bibliothèque GroupDocs.Parser pour .NET installée et référencée dans votre projet.

## Importer des espaces de noms
Pour commencer, ajoutez les espaces de noms nécessaires à votre fichier C# :
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Décomposons le processus en instructions étape par étape.
## Étape 1 : Définir les champs du modèle
Tout d'abord, définissez les champs que vous souhaitez extraire du document à l'aide d'expressions régulières.
```csharp
// Définir un champ "prix"
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Définir un champ "email"
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Créer un modèle avec des champs définis
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
Dans cette étape, nous avons défini deux champs : un pour extraire les prix (identifiés par le signe dollar et les chiffres) et un autre pour extraire les adresses e-mail.
## Étape 2 : analyser le document
 Ensuite, utilisez le`Parser` classe pour analyser le document à l’aide du modèle défini.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analyser le document par le modèle
    DocumentData data = parser.ParseByTemplate(template);
    // Parcourez les données extraites
    for (int i = 0; i < data.Count; i++)
    {
        // Imprimer le nom du champ
        Console.Write(data[i].Name + ": ");
        // Vérifiez si la zone extraite est du texte
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Ici, nous initialisons le`Parser` avec le chemin d'accès à votre exemple de document, puis analysez le document à l'aide du modèle défini. Nous parcourons ensuite les données extraites et imprimons les noms de champs avec le texte extrait.
## Conclusion
Dans ce didacticiel, nous avons expliqué comment utiliser GroupDocs.Parser pour .NET pour extraire des données spécifiques de documents à l'aide de modèles. En tirant parti des expressions régulières et des modèles, vous pouvez extraire efficacement des informations structurées à partir de différents formats de documents. Expérimentez avec différents modèles et types de documents pour répondre à vos besoins d'extraction spécifiques.

## FAQ
### GroupDocs.Parser peut-il extraire des données de documents numérisés ?
Oui, GroupDocs.Parser peut extraire du texte et des métadonnées à partir de documents PDF numérisés et consultables.
### GroupDocs.Parser est-il compatible avec les applications .NET Core ?
Oui, GroupDocs.Parser prend en charge .NET Core avec .NET Framework.
### Quels formats de documents sont pris en charge par GroupDocs.Parser ?
GroupDocs.Parser prend en charge un large éventail de formats, notamment PDF, Microsoft Word, Excel, PowerPoint, etc.
### Comment puis-je gérer des documents volumineux avec GroupDocs.Parser ?
GroupDocs.Parser fournit des options pour extraire des données de pages ou de sections spécifiques de documents volumineux, garantissant ainsi un traitement efficace.
### Puis-je utiliser GroupDocs.Parser uniquement pour l’extraction de texte ?
Oui, vous pouvez extraire le contenu en texte brut des documents à l'aide de GroupDocs.Parser sans avoir besoin d'un formatage complexe.