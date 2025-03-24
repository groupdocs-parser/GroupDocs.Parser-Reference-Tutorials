---
title: Extraire le texte d'un document Excel au format HTML
linktitle: Extraire le texte d'un document Excel au format HTML
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire du texte de documents Excel et le convertir en HTML à l'aide de GroupDocs.Parser pour .NET.
weight: 13
url: /fr/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## Introduction
Dans ce didacticiel, nous allons explorer comment utiliser GroupDocs.Parser pour .NET pour extraire le texte d'un document Excel et le convertir au format HTML. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs de travailler avec différents formats de documents, en extrayant efficacement le texte et les métadonnées.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir la configuration suivante :
- Visual Studio installé sur votre système.
- Compréhension de base de la programmation C#.
-  Bibliothèque GroupDocs.Parser pour .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/parser/net/).
## Importer des espaces de noms
Commencez par inclure les espaces de noms nécessaires dans votre projet C# pour accéder aux fonctionnalités GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance de la classe Parser
 Tout d’abord, instanciez le`Parser` classe en fournissant le chemin d’accès à votre document Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // D'autres codes iront ici
}
```
 Remplacer`"YourSampleFile.xlsx"` avec le chemin d'accès à votre fichier Excel.
## Étape 2 : Extraire le texte au format HTML
 Au sein du`using` bloc du`Parser` par exemple, utilisez le`GetFormattedText` méthode pour extraire du texte formaté en mode HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // D'autres codes iront ici
    }
}
```
## Étape 3 : Lire et imprimer le texte HTML extrait
 Ensuite, lisez le texte HTML extrait du`TextReader` et imprimez-le sur la console.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Une fois exécuté, ce code extraira le texte du document Excel et l'affichera au format HTML dans la console.
## Conclusion
Dans ce didacticiel, nous avons appris à utiliser GroupDocs.Parser pour .NET pour extraire le texte d'un document Excel et le convertir au format HTML. Cette bibliothèque offre un moyen simple de travailler avec différents formats de documents, permettant aux développeurs de gérer efficacement les tâches d'extraction de texte dans leurs applications.

## FAQ
### GroupDocs.Parser peut-il gérer d’autres formats de documents qu’Excel ?
Oui, GroupDocs.Parser prend en charge un large éventail de formats de fichiers, notamment PDF, Word, PowerPoint, etc.
### GroupDocs.Parser est-il compatible avec .NET Core ?
Oui, GroupDocs.Parser est compatible avec .NET Framework et .NET Core.
### GroupDocs.Parser préserve-t-il le formatage lors de l'extraction de texte ?
Oui, GroupDocs.Parser peut conserver le formatage tel que les polices, les styles et la mise en page lors de l'extraction de texte.
### Puis-je extraire des métadonnées de documents à l’aide de GroupDocs.Parser ?
Oui, GroupDocs.Parser permet d'extraire des métadonnées telles que l'auteur, la date de création, etc. à partir des types de documents pris en charge.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez télécharger un essai gratuit à partir de[ici](https://releases.groupdocs.com/).