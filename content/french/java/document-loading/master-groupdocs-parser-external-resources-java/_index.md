---
date: '2025-12-29'
description: Apprenez à extraire des images à partir de documents et à filtrer les
  ressources à l'aide de GroupDocs.Parser pour Java. Ce guide couvre la configuration,
  les gestionnaires personnalisés et des exemples pratiques.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: Extraire des images des documents avec GroupDocs.Parser Java – Un guide
type: docs
url: /fr/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Extraire des images de documents et filtrer les ressources avec GroupDocs.Parser Java

Extraire des images de documents est une exigence courante lors de la construction de pipelines de traitement de documents. Dans ce tutoriel, vous découvrirez **comment extraire des images de documents** à l’aide de GroupDocs.Parser pour Java, et vous apprendrez également **comment filtrer les ressources** afin que seuls les fichiers nécessaires soient chargés. Nous parcourrons la configuration de la bibliothèque, la création d’un `ExternalResourceHandler` personnalisé, et l’application d’une logique de filtrage pour garder votre application rapide et sécurisée.

## Réponses rapides
- **Que fait GroupDocs.Parser ?** Il analyse un large éventail de formats de documents et vous donne accès au texte, aux images et aux autres ressources intégrées.  
- **Puis‑je ignorer les images indésirables ?** Oui—en implémentant un `ExternalResourceHandler` personnalisé, vous pouvez décider quelles ressources charger.  
- **Quelle version Maven est requise ?** Utilisez GroupDocs.Parser Java 25.5 ou plus récent.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit fonctionne pour l’évaluation ; une licence permanente est requise pour la production.  
- **Cette approche est‑elle thread‑safe ?** Les objets de parsing ne sont pas partagés entre les threads ; créez une nouvelle instance de `Parser` par thread.

## Qu’entend‑on par « extraire des images de documents » ?
Lorsqu’un document contient des images, des graphiques ou d’autres médias intégrés, « extraire des images de documents » signifie récupérer programmétiquement ces fichiers binaires afin de les stocker, les afficher ou les traiter davantage en dehors du fichier original.

## Pourquoi filtrer les ressources lors de l’extraction d’images ?
Le filtrage des ressources vous aide à :
- Réduire la consommation de mémoire en ignorant les fichiers volumineux ou non pertinents.  
- Améliorer la sécurité en empêchant le chargement de contenus potentiellement dangereux.  
- Accélérer le traitement, notamment avec de gros documents contenant de nombreux objets intégrés.

## Prérequis

- **Java Development Kit (JDK)** – version 8 ou supérieure.  
- **Maven** – pour la gestion des dépendances.  
- Familiarité de base avec les I/O Java et la gestion des exceptions.

## Configuration de GroupDocs.Parser pour Java

Ajoutez le dépôt GroupDocs et la dépendance du parser à votre `pom.xml` :

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

Vous pouvez également télécharger la dernière version depuis [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Acquisition de licence
- **Essai gratuit** – explorez les fonctionnalités de base sans frais.  
- **Licence temporaire** – débloquez l’ensemble des fonctionnalités pendant l’évaluation.  
- **Licence achetée** – requise pour le déploiement commercial.

## Comment filtrer les ressources lors de l’extraction d’images

### Étape 1 : Créer un gestionnaire personnalisé
Définissez une classe qui étend `ExternalResourceHandler`. Dans la méthode `onLoading`, décidez quelles ressources conserver.

```java
import com.groupdocs.parser.options.ExternalResourceHandler;
import com.groupdocs.parser.data.ExternalResourceLoadingArgs;

class Handler extends ExternalResourceHandler {
    @Override
    public void onLoading(ExternalResourceLoadingArgs args) {
        if (!args.getUri().endsWith("installation.png")) {
            args.setSkipped(true);
        }
        super.onLoading(args);
    }
}
```

### Étape 2 : Configurer `ParserSettings` avec le gestionnaire
Passez votre instance de `Handler` à `ParserSettings` et utilisez‑la lors de l’ouverture d’un document.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.IOException;
import com.groupdocs.parser.options.ParserSettings;

public class LoadExternalResources {
    public static void run() throws IOException {
        ParserSettings settings = new ParserSettings(new Handler());
        
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
            Iterable<PageImageArea> images = parser.getImages();
            
            for (PageImageArea image : images) {
                System.out.println(image.getFileType());
            }
        }
    }
}
```

### Étape 3 : Affiner la logique de filtrage
Si vous avez besoin de règles plus sophistiquées—par exemple filtrer par taille d’image, format ou motif d’URI—étendez la méthode `onLoading` en conséquence :

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Applications pratiques

1. **Systèmes de gestion de documents** – Extraire uniquement les images nécessaires de contrats numérisés pour générer des miniatures.  
2. **Services d’extraction de données** – Ignorer les graphiques décoratifs et se concentrer sur les diagrammes contenant des données précieuses.  
3. **Outils de scraping web** – Filtrer les pixels de suivi tout en récupérant les médias pertinents de documents basés sur HTML.

## Considérations de performance
- **Filtrer tôt** : Appliquez votre gestionnaire personnalisé avant d’itérer sur les ressources afin d’éviter le chargement de données indésirables en mémoire.  
- **Libérer rapidement** : Utilisez le try‑with‑resources (`try (Parser parser = …)`) pour libérer les ressources natives.  
- **Traitement asynchrone** : Pour de gros lots, traitez les documents en flux parallèles tout en maintenant chaque instance de `Parser` confinée à un seul thread.

## Problèmes courants & solutions
| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Aucun image renvoyée | Le gestionnaire ignore toutes les ressources par inadvertance | Vérifiez laif` et assurez‑vous que `args.setSkipped(true)` n’est appelé que pour les URI indésirables. |
| `IOException` sur de gros fichiers | Mémoire heap insuffisante | Augmentez la heap JVM (`-Xmx2g`) ou traitez les pages par morceaux plus petits. |
| Licence non reconnue | Utilisation du DLL d’essai avec du code de production | Appliquez le bon chemin de fichier de licence via `License.setLicense("path/to/license")`. |

## Foire aux questions

**Q : Quel est le principal avantage d’utiliser un `ExternalResourceHandler` personnalisé ?**  
R : Il vous permet de contrôler quelles ressources externes sont chargées, améliorant ainsi la sécurité et les performances en filtrant les fichiers inutiles.

**Q : Puis‑je utiliser GroupDocs.Parser pour Java sans licence ?**  
R : Oui, un essai gratuit est disponible, mais certaines fonctionnalités avancées peuvent être limitées jusqu’à l’obtention d’une licence temporaire ou achetée.

**Q : Comment gérer les exceptions lors du parsing avec GroupDocs.Parser ?**  
R : Enveloppez les appels de parsing dans des blocs try‑catch pour `IOException` et d’autres exceptions spécifiques afin de gérer les erreurs de façon élégante.

**Q : Quels sont les pièges courants lors du filtrage des ressources ?**  
R : Des vérifications d’URI incorrectes peuvent ignorer des fichiers nécessaires ; utilisez la journalisation ou des points d’arrêt pour valider vos conditions.

**Q : Est‑il possible d’analyser des documents non‑HTML avec GroupDocs.Parser pour Java ?**  
R : Absolument—GroupDocs.Parser prend en charge les PDF, Word, Excel, PowerPoint et de nombreux autres formats.

## Prochain étapes
Explorez davantage la bibliothèque en consultant la [Référence API](https://reference.groupdocs.com/parser/java) ou expérimentez avec des paramètres supplémentaires tels que `ParserSettings.setDetectTables(true)` pour l’extraction de tableaux.

---

**Dernière mise à jour :** 2025-12-29  
**Testé avec :** GroupDocs.Parser 25.5 pour Java  
**Auteur :** GroupDocs  

**Ressources**  
- **Documentation :** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **Référence API :** [API Details](https://reference.groupdocs.com/parser/java)  
- **Téléchargements :** [Latest Versions](https://releases.groupdocs.com/parser/java/)