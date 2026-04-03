---
date: '2026-02-06'
description: Apprenez à prévisualiser les fichiers Excel et à convertir les xlsx en
  png en utilisant GroupDocs.Parser pour Java. Ce tutoriel couvre la configuration,
  l’implémentation et les applications pratiques.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Comment prévisualiser les fichiers Excel avec GroupDocs.Parser en Java
type: docs
url: /fr/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Comment prévisualiser les fichiers Excel avec GroupDocs.Parser en Java

Si vous cherchez **comment prévisualiser Excel** les feuilles de calcul de manière programmatique, vous êtes au bon endroit. Dans ce guide, nous parcourrons la création d’aperçus d’image (PNG) à partir de classeurs `.xlsx` en utilisant GroupDocs.Parser pour Java — parfait pour générer rapidement des miniatures, partager des instantanés ou créer une fonctionnalité d’aperçu de documents dans votre application.

## Réponses rapides
- **Que signifie « preview Excel » ?** Génération de fichiers image (par ex., PNG) qui représentent chaque page de feuille de calcul.  
- **Quel format est recommandé ?** PNG offre une qualité sans perte et fonctionne bien pour les miniatures web.  
- **Ai-je besoin d’une licence ?** Un essai gratuit fonctionne pour le développement ; une licence commerciale est requise pour la production.  
- **Puis-je changer la résolution de l’image ?** Oui — ajustez le DPI dans `PreviewOptions`.  
- **Est‑il possible de prévisualiser d’autres formats ?** GroupDocs.Parser prend également en charge PDF, Word et de nombreux types d’image.

## Qu’est‑ce que « comment prévisualiser Excel » avec GroupDocs.Parser ?
GroupDocs.Parser lit les classeurs Excel, rend chaque feuille sous forme de page visuelle, et vous permet de diffuser ces pages vers des fichiers image. Cela élimine le besoin d’interopérabilité Office ou de convertisseurs tiers.

## Pourquoi utiliser GroupDocs.Parser pour les aperçus Excel ?
- **Aucune installation d’Office requise** – fonctionne sur n’importe quel environnement Java côté serveur.  
- **Prend en charge les gros fichiers** – diffuse les pages une par une, maintenant une faible utilisation de la mémoire.  
- **Sortie haute qualité** – contrôle du DPI, du format et des options de rendu.  
- **Flexibilité multi‑format** – la même API fonctionne pour les PDF, les documents Word, et plus encore.

## Prérequis
- **Java Development Kit** (8 +).  
- **IDE** tel qu’IntelliJ IDEA ou Eclipse.  
- **GroupDocs.Parser for Java SDK** – téléchargez depuis [here](https://releases.groupdocs.com/parser/java/).  
- **Fichier Excel d’exemple** (`.xlsx`) que vous souhaitez prévisualiser.  
- **Maven ou Gradle** (optionnel) pour la gestion des dépendances.

## Importer les packages
Ces imports vous donnent accès au parser, aux options de prévisualisation et aux utilitaires de gestion de flux.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## Guide étape par étape pour générer des aperçus de pages de feuille de calcul

### Étape 1 : Initialiser l’instance du Parser
Créez un objet `Parser` pointant vers votre classeur Excel. Le bloc *try‑with‑resources* garantit que le parser est fermé automatiquement.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Astuce :** Utilisez un chemin absolu ou configurez un dossier de ressources pour éviter `FileNotFoundException`.

### Étape 2 : Préparer vos options de prévisualisation
Définissez comment chaque page sera enregistrée. L’implémentation `ICreatePageStream` renvoie un nouveau `FileOutputStream` pour chaque page de feuille de calcul.

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> Cette étape est celle où vous **convertissez xlsx en png** — le flux écrit les données PNG sur le disque.

### Étape 3 : Attacher un délégué pour capturer les informations de rendu
Si vous avez besoin de détails sur chaque feuille rendue (par ex., dimensions, nom de la feuille), enregistrez un rappel.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Étape 4 : Spécifier le format de sortie et le DPI
Sélectionnez PNG comme format d’image et définissez un DPI qui équilibre qualité et taille du fichier.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Ajustez le DPI si vous avez besoin de miniatures plus petites (par ex., 96) ou d’impressions haute résolution (par ex., 300).

### Étape 5 : Générer les aperçus
Une fois tout configuré, appelez `generatePreview`. Le SDK parcourra chaque feuille de calcul et invoquera le flux que vous avez fourni.

```java
parser.generatePreview(previewOptions);
```

### Étape 6 : Définir l’aide‑mémoire `getOutputPath()`
Cette méthode construit un nom de fichier basé sur le numéro de page (feuille). N’hésitez pas à personnaliser la structure du dossier.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Erreur courante :** Oublier de créer le répertoire `output` au préalable entraînera une `IOException`. Créez‑le programmaticalement ou assurez‑vous qu’il existe.

## Exemple complet fonctionnel (simplifié)

Ci‑dessous se trouve une version compacte qui assemble tous les éléments. Elle démontre le flux de travail **create excel page preview** du début à la fin.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

Exécutez cet extrait, et vous trouverez une série de fichiers `preview_page_1.png`, `preview_page_2.png`, … dans le dossier `output` — chacun représentant une feuille du classeur Excel original.

## Problèmes courants et solutions

| Problème | Cause | Solution |
|----------|-------|----------|
| **Aucune image générée** | `getOutputPath` renvoie un répertoire invalide | Assurez‑vous que le dossier cible existe ou créez‑le avec `new File("output").mkdirs();` |
| **Erreur de mémoire insuffisante sur de gros fichiers** | Chargement du classeur complet en une fois | Utilisez l’approche de diffusion (comme montré) et traitez les pages une à la fois |
| **DPI incorrect** | `setDpi` non appelé ou réglé sur la valeur par défaut (96) | Appelez `previewOptions.setDpi(votreValeurSouhaitée);` avant `generatePreview` |
| **Format non pris en charge** | Tentative de prévisualiser un `.xlsx` corrompu | Validez le fichier avec Excel ou utilisez `Parser.isSupported` avant le traitement |

## Questions fréquentes

**Q : Puis‑je générer des aperçus pour les PDF et les images avec GroupDocs.Parser ?**  
R : Oui, la même API fonctionne pour les PDF, les documents Word et de nombreux formats d’image.

**Q : Comment changer le format d’image de sortie ?**  
R : Appelez `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (ou `Gif`, `Bmp`, etc.).

**Q : La performance est‑elle un problème avec des classeurs très volumineux ?**  
R : Le SDK diffuse les pages, ce qui maintient une faible consommation de mémoire. Pour des fichiers massifs, envisagez de traiter les pages en lots parallèles.

**Q : Comment gérer les erreurs lors de la génération d’aperçus ?**  
R : Enveloppez le code dans des blocs try‑catch (comme montré) et consignez les détails de l’exception. Assurez‑vous que les flux sont fermés dans le bloc `finally` si vous n’utilisez pas try‑with‑resources.

**Q : La bibliothèque nécessite‑t‑elle l’installation de Microsoft Office ?**  
R : Non. GroupDocs.Parser est une solution pure Java et fonctionne sur toute plateforme supportant Java 8+.

## Conclusion
Vous disposez maintenant d’une méthode complète, prête pour la production, pour **comment prévisualiser Excel** les classeurs et **convertir xlsx en png** en utilisant GroupDocs.Parser. Ajustez le DPI, le dossier de sortie ou le format d’image pour répondre aux besoins de votre projet, et intégrez cet extrait dans des flux de travail de gestion de documents plus larges.

Prêt pour l’étape suivante ? Explorez la [documentation](https://docs.groupdocs.com/parser/java/) officielle pour des options de rendu avancées, les fichiers protégés par mot de passe et les techniques de traitement par lots.

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Parser 23.11 (latest at time of writing)  
**Author:** GroupDocs