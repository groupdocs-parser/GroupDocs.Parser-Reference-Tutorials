---
title: Extraire le texte formaté du document
linktitle: Extraire le texte formaté du document
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire du texte formaté à partir de documents à l'aide de GroupDocs.Parser pour .NET. Extraction de texte simple et efficace pour vos applications.
weight: 10
url: /fr/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Parser pour .NET pour extraire du texte formaté à partir de différents types de documents. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs de travailler avec des documents de manière simplifiée et efficace. À la fin de ce guide, vous serez en mesure d'intégrer de manière transparente des fonctionnalités d'extraction de texte dans vos applications .NET.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio : assurez-vous que Visual Studio est installé sur votre système.
-  GroupDocs.Parser pour .NET : téléchargez et installez la bibliothèque GroupDocs.Parser à partir de[ici](https://releases.groupdocs.com/parser/net/).
- Exemples de documents : préparez des exemples de documents (par exemple, PDF, DOCX) pour l'extraction de texte.
## Importer des espaces de noms
Tout d’abord, incluez les espaces de noms nécessaires dans votre code C# :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance de la classe Parser
 Commencez par initialiser un`Parser` objet avec le chemin d’accès à votre exemple de document.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Le code d'extraction de texte va ici
}
```
 Remplacer`"YourSampleFile.pdf"` avec le chemin d'accès à votre fichier de document.

## Étape 2 : Extraire le texte formaté
 Au sein du`using` bloquer, utilisez le`GetFormattedText` méthode pour extraire le texte formaté du document. Spécifiez le format de sortie souhaité (par exemple, HTML) en utilisant`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extraire le texte formaté dans le lecteur
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Vérifiez si l'extraction est prise en charge
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Lire et afficher le texte extrait
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Conclusion
Toutes nos félicitations! Vous avez appris à extraire du texte formaté à partir de documents à l'aide de GroupDocs.Parser pour .NET. Cette bibliothèque polyvalente ouvre des possibilités de traitement et d'analyse de texte au sein de vos applications.

## FAQ
### Q : GroupDocs.Parser peut-il extraire du texte à partir de documents protégés par mot de passe ?
R : Oui, GroupDocs.Parser prend en charge l'extraction de texte à partir de documents protégés par mot de passe.
### Q : Quels formats de documents sont pris en charge par GroupDocs.Parser ?
R : GroupDocs.Parser prend en charge un large éventail de formats, notamment PDF, DOCX, XLSX, PPTX, etc.
### Q : Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 R : Vous pouvez obtenir une licence temporaire auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
### Q : GroupDocs.Parser prend-il en charge l'extraction d'images à partir de documents ?
R : Oui, GroupDocs.Parser prend en charge l’extraction d’images ainsi que l’extraction de texte.
### Q : Où puis-je trouver une assistance supplémentaire ou poser des questions sur GroupDocs.Parser ?
 R : Visitez le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)pour du soutien et des discussions.