---
title: Travailler avec des champs à des positions liées dans des modèles
linktitle: Travailler avec des champs à des positions liées dans des modèles
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire efficacement des données de documents à l'aide de GroupDocs.Parser pour .NET. Tutoriel étape par étape avec des exemples de code.
weight: 12
url: /fr/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
type: docs
---
# Travailler avec des champs à des positions liées dans des modèles

## Introduction
GroupDocs.Parser pour .NET est une bibliothèque robuste conçue pour faciliter les tâches d'analyse de documents et d'extraction de données. Il prend en charge un large éventail de formats de fichiers, notamment PDF, DOCX, XLSX, etc. L'une de ses fonctionnalités clés est l'extraction de données basée sur des modèles, qui vous permet de définir des champs dans un document et d'extraire des données spécifiques en fonction de ces modèles prédéfinis.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Compréhension de base de la programmation C#
- Visual Studio installé sur votre système
-  Bibliothèque GroupDocs.Parser pour .NET (téléchargement depuis[ici](https://releases.groupdocs.com/parser/net/))
- Exemples de fichiers de documents avec lesquels travailler

## Importation d'espaces de noms
Commencez par inclure les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Étape 1 : Définir les champs du modèle
Tout d'abord, définissez les champs du modèle à l'aide d'expressions régulières et de positions liées :
```csharp
// Définir un champ avec une expression régulière
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Définir un champ lié avec des paramètres de position spécifiques
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Étape 2 : créer un modèle
Créez ensuite un modèle contenant les champs définis :
```csharp
// Créer un modèle avec les champs définis
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Étape 3 : Analyser le document avec le modèle
 Maintenant, initialisez le`Parser` classe et analysez le document à l'aide du modèle :
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analyser le document par le modèle
    DocumentData data = parser.ParseByTemplate(template);
    // Parcourez les données extraites et imprimez les résultats
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusion
GroupDocs.Parser pour .NET simplifie le processus d'extraction de données structurées à partir de documents à l'aide de modèles. En définissant des champs et en appliquant des modèles, vous pouvez extraire efficacement les informations pertinentes, améliorant ainsi l'automatisation et la productivité des tâches de traitement des documents.

## FAQ
### GroupDocs.Parser peut-il extraire des données de fichiers PDF cryptés ?
Oui, GroupDocs.Parser prend en charge l'analyse des fichiers PDF cryptés en fournissant le mot de passe lors de l'analyse.
### Quels formats de fichiers sont pris en charge pour l'extraction basée sur un modèle ?
GroupDocs.Parser prend en charge une large gamme de formats de fichiers, notamment PDF, DOCX, XLSX, PPTX, TXT, etc.
### Existe-t-il une version d’essai disponible pour GroupDocs.Parser ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).
### Puis-je utiliser GroupDocs.Parser pour le traitement par lots de documents ?
Oui, GroupDocs.Parser permet le traitement par lots pour analyser plusieurs documents simultanément.
### Où puis-je obtenir une assistance technique pour GroupDocs.Parser ?
 Vous pouvez demander une assistance technique et interagir avec la communauté à[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17).