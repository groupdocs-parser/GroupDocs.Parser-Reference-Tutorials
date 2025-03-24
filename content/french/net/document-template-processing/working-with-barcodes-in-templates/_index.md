---
title: Travailler avec des codes-barres dans des modèles
linktitle: Travailler avec des codes-barres dans des modèles
second_title: API GroupDocs.Parser .NET
description: Découvrez comment utiliser GroupDocs.Parser pour .NET pour extraire des données structurées de documents à l'aide de modèles. Simplifiez l'extraction de données avec des champs de codes-barres.
weight: 10
url: /fr/net/document-template-processing/working-with-barcodes-in-templates/
---

# Travailler avec des codes-barres dans des modèles

## Introduction
Dans ce didacticiel, nous explorerons comment extraire efficacement des données de documents à l'aide de modèles avec GroupDocs.Parser pour .NET. GroupDocs.Parser simplifie le processus d'extraction de données en vous permettant de définir des modèles pour des types de données spécifiques, tels que les codes-barres, puis d'analyser les documents en fonction de ces modèles.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir la configuration suivante :
-  GroupDocs.Parser pour .NET : vous pouvez télécharger la bibliothèque à partir de[ici](https://releases.groupdocs.com/parser/net/).
- Exemple de document : préparez un exemple de fichier (par exemple, PDF, DOCX) contenant les données que vous souhaitez extraire.

## Importer des espaces de noms
Tout d’abord, incluez les espaces de noms nécessaires dans votre code C# :
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
using System;
```
## Étape 1 : Définir un champ de code-barres
Définissez un champ de code-barres dans un modèle. Cet exemple configure un champ de code QR :
```csharp
TemplateBarcode barcode = new TemplateBarcode(
    new Rectangle(new Point(590, 80), new Size(150, 150)),
    "QR");
```
 Ici,`Rectangle` définit la position et la taille du champ du code-barres sur le document.
## Étape 2 : créer un modèle
Créez un modèle et ajoutez-y le champ du code-barres :
```csharp
Template template = new Template(new TemplateItem[] { barcode });
```
## Étape 3 : analyser le document à l'aide du modèle
 Instancier le`Parser` class avec le chemin du fichier de votre document et analysez le document à l'aide du modèle défini :
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Imprimer les données extraites
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageBarcodeArea area = data[i].PageArea as PageBarcodeArea;
        Console.WriteLine(area == null ? "Not a template barcode field" : area.Value);
    }
}
```
Cet extrait de code ouvre le document, applique le modèle et extrait les données en fonction du champ de code-barres défini. Il imprime ensuite les données extraites.

## Conclusion
L'utilisation de GroupDocs.Parser pour .NET avec des modèles simplifie l'extraction de données structurées à partir de documents, en particulier lorsqu'il s'agit de types de données spécifiques tels que les codes-barres. En suivant ce guide, vous pouvez intégrer efficacement les capacités d'analyse de documents dans vos applications .NET.

## FAQ
### Q : Puis-je extraire plusieurs champs de codes-barres d’un seul document ?
R : Oui, vous pouvez définir plusieurs champs de codes-barres dans un modèle et extraire les données correspondantes d'un document.
### Q : Quels formats de documents sont pris en charge pour l'analyse ?
R : GroupDocs.Parser prend en charge un large éventail de formats de documents, notamment PDF, DOCX, XLSX, PPTX, etc.
### Q : Existe-t-il une version d'essai disponible ?
 R : Oui, vous pouvez obtenir un essai gratuit de GroupDocs.Parser auprès de[ici](https://releases.groupdocs.com/).
### Q : Comment puis-je obtenir une assistance technique ?
 R : Pour obtenir une assistance technique, visitez le[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Q : Où puis-je acheter une licence ?
 R : Vous pouvez acheter une licence pour GroupDocs.Parser auprès de[ici](https://purchase.groupdocs.com/buy).