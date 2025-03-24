---
title: Extraire le texte d'un document Word au format HTML
linktitle: Extraire le texte d'un document Word au format HTML
second_title: API GroupDocs.Parser .NET
description: Découvrez comment utiliser GroupDocs.Parser pour .NET pour extraire du texte de documents Word et l'enregistrer au format HTML. Tutoriel étape par étape avec des exemples de code.
weight: 16
url: /fr/net/word-document-processing/extract-text-from-word-document-as-html/
---

# Extraire le texte d'un document Word au format HTML

## Introduction
GroupDocs.Parser pour .NET est une puissante bibliothèque d'analyse de documents qui permet aux développeurs d'extraire de manière transparente du texte et des métadonnées à partir de divers formats de fichiers. Dans ce didacticiel, nous nous concentrerons sur l'utilisation de GroupDocs.Parser pour extraire du texte de documents Word et l'enregistrer au format HTML. Ce processus est essentiel pour des tâches telles que l'analyse de contenu, l'indexation ou la conversion de documents dans des formats adaptés au Web. À la fin de ce guide, vous comprendrez clairement comment utiliser efficacement GroupDocs.Parser dans vos applications .NET.
## Conditions préalables
Avant de vous lancer dans ce didacticiel, assurez-vous d'avoir les prérequis suivants :
- Connaissance de base de la programmation C#.
- Visual Studio installé sur votre machine de développement.
-  GroupDocs.Parser pour la bibliothèque .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/parser/net/).
- Accès à un exemple de document Word à des fins de test.
## Importer des espaces de noms
Pour commencer, vous devez importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Suivez ces étapes détaillées pour extraire le texte d'un document Word et l'enregistrer au format HTML à l'aide de GroupDocs.Parser pour .NET :
## Étape 1 : Créer une instance de la classe Parser
 Tout d'abord, créez une instance de`Parser` classe en fournissant le chemin d’accès à votre exemple de document Word :
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Passez à l'étape 2...
}
```
 Remplacer`"YourSampleFile.docx"`avec le chemin d'accès à votre document Word.
## Étape 2 : Extraire le texte formaté au format HTML
 Ensuite, utilisez le`GetFormattedText` méthode avec`FormattedTextOptions`pour extraire le texte au format HTML :
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraire un texte formaté dans le lecteur
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Passez à l'étape 3...
    }
}
```
## Étape 3 : Lire et afficher le code HTML extrait
 Enfin, lisez le contenu HTML extrait du`TextReader` et imprimez-le sur la console :
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraire un texte formaté dans le lecteur
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Imprimer le texte formaté au format HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Conclusion
Dans ce didacticiel, nous avons expliqué comment utiliser GroupDocs.Parser pour .NET pour extraire le texte d'un document Word et l'enregistrer au format HTML. Cette bibliothèque offre un moyen simple et efficace d'analyser le contenu d'un document, ce qui en fait un outil précieux pour les tâches de traitement de documents dans les applications .NET.

## FAQ
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez demander une licence temporaire auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je trouver plus de documentation pour GroupDocs.Parser ?
 Une documentation détaillée est disponible[ici](https://tutorials.groupdocs.com/parser/net/).
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez accéder à la version d'essai gratuite[ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l’assistance pour GroupDocs.Parser ?
 Visitez le forum d'assistance[ici](https://forum.groupdocs.com/c/parser/17).
### Quels types de documents GroupDocs.Parser prend-il en charge ?
GroupDocs.Parser prend en charge divers formats de documents, notamment Word, PDF, Excel, PowerPoint, etc.