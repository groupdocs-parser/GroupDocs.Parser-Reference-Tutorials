---
date: '2026-08-05'
description: Apprenez comment extraire des images de documents Word à l'aide de GroupDocs.Parser
  pour Java et enregistrer les images Word au format PNG efficacement.
keywords:
- extract images from word
- how to extract images
- extract images from docx
- extract pictures from word
- convert word images png
lastmod: '2026-08-05'
og_description: Extraire des images de documents Word avec GroupDocs.Parser pour Java.
  Apprenez étape par étape comment extraire les images et enregistrer les images Word
  au format PNG efficacement.
og_image_alt: Code example showing image extraction from a Word document using GroupDocs.Parser
  for Java
og_title: Extraire des images de Word à l'aide de GroupDocs.Parser pour Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to extract images from word documents using GroupDocs.Parser
    for Java and save word images png efficiently.
  headline: Extract images from word using GroupDocs.Parser for Java
  type: TechArticle
- description: Learn how to extract images from word documents using GroupDocs.Parser
    for Java and save word images png efficiently.
  name: Extract images from word using GroupDocs.Parser for Java
  steps:
  - name: initialize the parser
    text: The `Parser` class is the entry point for reading a document. It loads the
      file into memory and prepares all content streams for extraction.
  - name: extract images
    text: '`PageImageArea` objects represent each picture found in the document, regardless
      of whether the image is inline, floating, or part of a shape.'
  - name: configure image options
    text: '`ImageOptions` lets you specify the output format, resolution, and other
      rendering settings before saving each picture.'
  - name: save each image
    text: '`ImageFormat` enum defines the output image format such as PNG, JPEG, or
      BMP. The `save` method writes the binary image data to a file on disk. By passing
      `ImageFormat.Png`, you satisfy the **save word images png** requirement.'
  - name: define helper methods for paths
    text: Utility methods simplify path handling and keep the main extraction logic
      clean and maintainable. Replace `YOUR_DOCUMENT_DIRECTORY` and `YOUR_OUTPUT_DIRECTORY`
      with the actual file system locations you intend to use.
  type: HowTo
- questions:
  - answer: It handles DOC, DOCX, PDF, PPT, PPTX, and many other formats, exposing
      images via the same `getImages()` method.
    question: What file formats does GroupDocs.Parser support for image extraction?
  - answer: Yes—pass the password to the `Parser` constructor, and the library will
      decrypt the document before extraction.
    question: Can I extract images from password‑protected Word files?
  - answer: After retrieving `PageImageArea` objects, inspect `image.getFormat()`
      and filter accordingly before saving.
    question: Is there a way to extract only specific image types (e.g., JPEG only)?
  - answer: While the core API is synchronous, you can wrap the extraction logic in
      a separate thread or use Java’s `CompletableFuture` for parallel processing.
    question: Does the library support asynchronous processing?
  - answer: A free trial is fine for evaluation, but a paid license is required for
      commercial deployments.
    question: Do I need a commercial license for production use?
  type: FAQPage
tags:
- extract images
- GroupDocs.Parser
- Java document processing
title: Extraire des images de Word à l'aide de GroupDocs.Parser pour Java
type: docs
url: /fr/java/image-extraction/extract-images-word-docs-groupdocs-parser-java/
weight: 1
---

# Extraire des images de Word avec GroupDocs.Parser pour Java

Extraire des images des fichiers Word manuellement prend du temps et est sujet aux erreurs. Dans ce tutoriel, vous découvrirez **comment extraire des images de Word** automatiquement avec GroupDocs.Parser pour Java, puis **enregistrer les images Word au format PNG** pour le traitement en aval. Vous obtiendrez une vue d'ensemble claire des raisons pour lesquelles la bibliothèque est rapide, comment la configurer, et des conseils de bonnes pratiques qui vous permettent d'intégrer l'extraction d'images dans n'importe quelle application Java.

## Réponses rapides
- **Que fait la bibliothèque ?** Elle analyse Word, PDF et de nombreux autres formats pour exposer le texte, les tableaux et les images.  
- **Combien de lignes de code ?** Environ 30 lignes de Java, plus quelques lignes de configuration.  
- **Ai-je besoin d'une licence ?** Un essai gratuit suffit pour le développement ; une licence complète est requise pour la production.  
- **Puis-je extraire les images intégrées ?** Oui – la méthode `getImages()` renvoie chaque image intégrée.  
- **Format de sortie pris en charge ?** PNG est le format par défaut, mais d'autres formats sont disponibles via `ImageFormat`.

## Qu’est‑ce que « extraire des images de Word » ?
Extraire des images de Word désigne la récupération programmatique de tous les fichiers image intégrés dans un document Microsoft Word. GroupDocs.Parser lit la structure binaire d'un fichier DOCX ou DOC et expose chaque image sous forme d'un objet `PageImageArea`, vous permettant d'extraire chaque image sans ouvrir le document dans Microsoft Word. Cette approche élimine le copier‑coller manuel, réduit les erreurs humaines et s'adapte à des milliers de fichiers dans des traitements par lots.

## Pourquoi utiliser GroupDocs.Parser pour Java ?
Vous pouvez extraire des images de documents Word avec **rapidité**, **fiabilité** et **flexibilité multiplateforme**. GroupDocs.Parser traite un DOCX de 200 pages en moins de 2 secondes sur un serveur standard à 2 CPU, et il fonctionne sous Windows, Linux et macOS sans nécessiter Microsoft Office. La bibliothèque tolère également les fichiers corrompus, renvoyant les images encore accessibles, ce qui la rend idéale pour les projets de migration à grande échelle.

## Prérequis
- **GroupDocs.Parser for Java** (version 25.5 ou plus récente)  
- **JDK 8+** installé sur votre machine de développement  
- Un IDE tel qu'IntelliJ IDEA, Eclipse ou NetBeans pour éditer et exécuter le code  

## Configuration de GroupDocs.Parser pour Java
Ajoutez la bibliothèque à votre projet Maven :

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/parser/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-parser</artifactId>
      <version>25.5</version>
   </dependency>
</dependencies>
```

Sinon, téléchargez la dernière version directement depuis [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Étapes d'obtention de licence
- **Free trial:** Commencez avec un essai gratuit pour explorer les fonctionnalités.  
- **Temporary license:** Obtenez une licence temporaire pour des tests prolongés si nécessaire.  
- **Purchase:** Acquérez une licence complète pour les déploiements en production.

## Guide d'implémentation
Voici le code Java complet, prêt à l'exécution, qui **extrait des images de Word** des documents et les enregistre au format PNG.

### Étape 1 : initialiser le parser
La classe `Parser` est le point d'entrée pour lire un document. Elle charge le fichier en mémoire et prépare tous les flux de contenu pour l'extraction.

```java
// Initialize the Parser with the document path.
try (Parser parser = new Parser(documentPath)) {
    // Proceed with image extraction...
}
```

### Étape 2 : extraire les images
Les objets `PageImageArea` représentent chaque image trouvée dans le document, qu'elle soit en ligne, flottante ou faisant partie d'une forme.

```java
// Extract images from the document.
Iterable<PageImageArea> images = parser.getImages();
```

### Étape 3 : configurer les options d'image
`ImageOptions` vous permet de spécifier le format de sortie, la résolution et d'autres paramètres de rendu avant d'enregistrer chaque image.

```java
// Set options to save images in PNG format.
ImageOptions options = new ImageOptions(ImageFormat.Png);
```

### Étape 4 : enregistrer chaque image
L'énumération `ImageFormat` définit le format d'image de sortie tel que PNG, JPEG ou BMP.  
La méthode `save` écrit les données binaires de l'image dans un fichier sur le disque. En passant `ImageFormat.Png`, vous remplissez l'exigence **enregistrer les images Word au format PNG**.

```java
int imageNumber = 0;
for (PageImageArea image : images) {
    String outputPath = YOUR_OUTPUT_DIRECTORY + "/" + imageNumber + ".png";
    image.save(outputPath, options);
    imageNumber++;
}
```

### Étape 5 : définir les méthodes d'assistance pour les chemins
Les méthodes utilitaires simplifient la gestion des chemins et maintiennent la logique principale d'extraction claire et maintenable.

```java
public static String getDocumentDirectory() {
    return YOUR_DOCUMENT_DIRECTORY;
}

public static String getOutputDirectory() {
    return YOUR_OUTPUT_DIRECTORY;
}
```

Remplacez `YOUR_DOCUMENT_DIRECTORY` et `YOUR_OUTPUT_DIRECTORY` par les emplacements réels du système de fichiers que vous souhaitez utiliser.

## Comment extraire les images intégrées d'un docx ?
La méthode `getImages()` renvoie une collection d'objets `PageImageArea` représentant chaque image intégrée.  
Chargez le DOCX avec `new Parser("input.docx")` et appelez `parser.getImages()` – la méthode renvoie automatiquement chaque image intégrée, y compris les images en ligne, les formes flottantes et les dessins VML. Aucun appel d'API supplémentaire n'est requis, vous pouvez donc parcourir la collection renvoyée et traiter chaque `PageImageArea` directement.

## Comment extraire des images d'un docx et les enregistrer au format PNG ?
Créez une instance `ImageOptions`, définissez `options.setImageFormat(ImageFormat.Png)`, et passez‑la à `image.save(outputPath, options)`. Cette configuration garantit que chaque image extraite est enregistrée en fichier PNG, répondant à l'objectif **enregistrer les images Word au format PNG** tout en préservant la résolution et la profondeur de couleur d'origine.

## Applications pratiques
1. **Content management** : Extraire les images des fichiers Word hérités pour une bibliothèque d'actifs numériques.  
2. **Data migration** : Déplacer les graphiques intégrés vers un nouveau CMS sans copier‑coller manuel.  
3. **Document archiving** : Stocker les images séparément pour réduire la taille de l'archive et améliorer la recherche.  
4. **Automated publishing** : Alimenter les PNG extraits directement dans les générateurs de pages web ou les modèles d'e‑mail.

## Considérations de performance
- **Memory usage** : Allouez au moins `-Xmx2g` lors du traitement de gros documents ; le parser diffuse les données pour garder une empreinte mémoire faible.  
- **Batch processing** : Réutilisez une seule instance `Parser` par document dans une boucle pour minimiser la surcharge de création d'objets.  
- **File handles** : Le bloc try‑with‑resources garantit que le parser est fermé rapidement, évitant les fuites de descripteurs.

## Problèmes courants et solutions
| Problème | Solution |
|----------|----------|
| **OutOfMemoryError** sur de très gros fichiers DOCX | Augmentez la mémoire du JVM ou traitez le document par lots plus petits. |
| **Aucune image renvoyée** | Vérifiez que le document contient réellement des images intégrées ; certaines « pictures » sont des dessins VML non exposés en tant qu'images. |
| **Orientation d'image incorrecte** | Certaines images DOCX stockent la rotation EXIF ; post‑traitez avec une bibliothèque d'images si nécessaire. |

## Questions fréquentes

**Q : Quels formats de fichiers GroupDocs.Parser prend‑en charge pour l'extraction d'images ?**  
R : Il gère DOC, DOCX, PDF, PPT, PPTX et de nombreux autres formats, exposant les images via la même méthode `getImages()`.

**Q : Puis‑je extraire des images de fichiers Word protégés par mot de passe ?**  
R : Oui — transmettez le mot de passe au constructeur `Parser`, et la bibliothèque déchiffrera le document avant l'extraction.

**Q : Existe‑t‑il un moyen d'extraire uniquement des types d'images spécifiques (par ex., JPEG uniquement) ?**  
R : Après avoir récupéré les objets `PageImageArea`, inspectez `image.getFormat()` et filtrez en conséquence avant l'enregistrement.

**Q : La bibliothèque prend‑elle en charge le traitement asynchrone ?**  
R : Bien que l'API principale soit synchrone, vous pouvez encapsuler la logique d'extraction dans un thread séparé ou utiliser `CompletableFuture` de Java pour le traitement parallèle.

**Q : Ai‑je besoin d'une licence commerciale pour une utilisation en production ?**  
R : Un essai gratuit suffit pour l'évaluation, mais une licence payante est requise pour les déploiements commerciaux.

---

**Dernière mise à jour** : 2026-08-05  
**Testé avec** : GroupDocs.Parser 25.5  
**Auteur** : GroupDocs  

**Ressources**  
- **Documentation** : [Documentation GroupDocs Parser Java](https://docs.groupdocs.com/parser/java/)  
- **Référence API** : [Référence API GroupDocs](https://reference.groupdocs.com/parser/java)  
- **Téléchargement** : [Latest Release](https://releases.groupdocs.com/parser/java/)  
- **GitHub** : [Source code on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- **Support gratuit** : [GroupDocs Forum](https://forum.groupdocs.com/c/parser)  
- **Licence temporaire** : [Obtain a temporary license](https://purchase.groupdocs.com/temporary-license/)

## Tutoriels associés

- [Comment enregistrer des images avec GroupDocs.Parser pour Java](/parser/java/image-extraction/extract-images-groupdocs-parser-java/)
- [Comment extraire des images d'un PDF avec GroupDocs.Parser en Java : guide étape par étape](/parser/java/image-extraction/extract-images-pdf-groupdocs-parser-java/)
- [Comment extraire du texte de documents Word avec GroupDocs.Parser en Java](/parser/java/text-extraction/extract-text-word-docs-groupdocs-parser-java/)