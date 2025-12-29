---
date: '2025-12-29'
description: Узнайте, как извлекать изображения из документов и фильтровать ресурсы
  с помощью GroupDocs.Parser для Java. В этом руководстве рассматриваются настройка,
  пользовательские обработчики и практические примеры.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: Извлечение изображений из документов с помощью GroupDocs.Parser Java – руководство
type: docs
url: /ru/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Извлечение изображений из документов и фильтрация ресурсов с GroupDocs.Parser Java

Извлечение изображений из документов — распространённая задача при построении конвейеров обработки документов. В этом руководстве вы узнаете **как извлекать изображения из документов** с помощью GroupDocs.Parser для Java, а также **как фильтровать ресурсы**, чтобы загружались только нужные файлы. Мы пройдём настройку библиотеки, создание пользовательского `ExternalResourceHandler` и применение логики фильтрации для повышения скорости и безопасности вашего приложения.

## Быстрые ответы
- **Что делает GroupDocs.Parser?** Он парсит широкий спектр форматов документов и предоставляет доступ к тексту, изображениям и другим встроенным ресурсам.  
- **Можно ли пропустить нежелательные изображения?** Да — реализовав собственный `ExternalResourceHandler`, вы можете решить, какие ресурсы загружать.  
- **Какая версия Maven требуется?** Используйте GroupDocs.Parser Java 25.5 или новее.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для оценки; для продакшена требуется постоянная лицензия.  
- **Безопасен ли этот подход в многопоточном окружении?** Объекты парсинга не разделяются между потоками; создавайте новый экземпляр `Parser` для каждого потока.

## Что означает «извлечение изображений из документов»?
Когда документ содержит встроенные картинки, диаграммы или другие медиа‑файлы, «извлечение изображений из документов» подразумевает программное получение этих бинарных файлов, чтобы вы могли сохранять, отображать или дальше обрабатывать их вне оригинального файла.

## Почему стоит фильтровать ресурсы при извлечении изображений?
Фильтрация ресурсов помогает:
- Снизить потребление памяти, игнорируя большие или несущественные файлы.  
- Повысить безопасность, предотвращая загрузку потенциально опасного контента.  
- Ускорить обработку, особенно больших документов с множеством встроенных объектов.

## Предварительные требования

- **Java Development Kit (JDK)** — версия 8 или выше.  
- **Maven** — для управления зависимостями.  
- Базовое знакомство с Java I/O и обработкой исключений.

## Настройка GroupDocs.Parser для Java

Добавьте репозиторий GroupDocs и зависимость parser в ваш `pom.xml`:

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

Или скачайте последнюю версию с [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Получение лицензии
- **Free Trial** — исследуйте основные возможности бесплатно.  
- **Temporary License** — разблокируйте полный функционал во время оценки.  
- **Purchased License** — требуется для коммерческого развертывания.

## Как фильтровать ресурсы при извлечении изображений

### Шаг 1: Создайте пользовательский обработчик
Определите класс, наследующий `ExternalResourceHandler`. В методе `onLoading` решайте, какие ресурсы сохранять.

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

### Шаг 2: Настройте `ParserSettings` с обработчиком
Передайте ваш экземпляр `Handler` в `ParserSettings` и используйте его при открытии документа.

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

### Шаг 3: Тонкая настройка логики фильтрации
Если нужны более сложные правила — например, фильтрация по размеру изображения, формату или шаблону URI — расширьте метод `onLoading` соответствующим образом:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Практические применения

1. **Document Management Systems** — извлекайте только необходимые изображения из отсканированных контрактов для создания миниатюр.  
2. **Data Extraction Services** — пропускайте декоративную графику и сосредотачивайтесь на диаграммах, содержащих ценные данные.  
3. **Web Scraping Tools** — фильтруйте трекинговые пиксели, получая значимые медиа‑файлы из HTML‑документов.

## Соображения по производительности
- **Фильтровать рано**: применяйте ваш пользовательский обработчик до перебора ресурсов, чтобы избежать загрузки ненужных данных в память.  
- **Своевременно освобождать**: используйте try‑with‑resources (`try (Parser parser = …)`) для освобождения нативных ресурсов.  
- **Асинхронная обработка**: для больших партий обрабатывайте документы в параллельных потоках, удерживая каждый экземпляр `Parser` в одном потоке.

## Распространённые проблемы и решения
| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| Не возвращаются изображения | Обработчик по ошибке пропускает все ресурсы | Проверьте условие `if` и убедитесь, что `args.setSkipped(true)` вызывается только для нежелательных URI. |
| `IOException` при больших файлах | Недостаточно памяти кучи | Увеличьте размер кучи JVM (`-Xmx2g`) или обрабатывайте страницы небольшими порциями. |
| Лицензия не расп | Используется пробочная DLL в продакшн‑коде | Укажите правильный путь к файлу лицензии через `License.setLicense("path/to/license")`. |

## Часто задаваемые вопросы

**В: Какова основная цель использования пользовательского `ExternalResourceHandler`?**  
О: Он позволяет контролировать, какие внешние ресурсы загружаются, повышая безопасность и производительность за счёт фильтрации ненужных файлов.

**В: Можно ли использовать GroupDocs.Parser для Java без лицензии?**  
О: Да, доступна бесплатная пробная версия, но некоторые продвинутые функции могут быть ограничены до получения временной или полной лицензии.

**В: Как обрабатывать исключения при парсинге с GroupDocs.Parser?**  
О: Оборачивайте вызовы парсинга в блоки try‑catch для `IOException` и других специфических исключений, чтобы корректно реагировать на ошибки.

**В: Какие типичные подводные камни при фильтрации ресурсов?**  
О: Неправильные проверки URI могут пропустить нужные файлы; используйте логирование или точки останова для проверки условий.

**В: Можно ли парсить не‑HTML документы с помощью GroupDocs.Parser для Java?**  
О: Конечно — GroupDocs.Parser поддерживает PDF, Word, Excel, PowerPoint и многие другие форматы.

## Следующие шаги
Углубитесь в библиотеку, изучив [API Reference](https://reference.groupdocs.com/parser/java) или поэкспериментируйте с дополнительными настройками, такими как `ParserSettings.setDetectTables(true)` для извлечения таблиц.

---

**Последнее обновление:** 2025-12-29  
**Тестировано с:** GroupDocs.Parser 25.5 for Java  
**:** GroupDocs  

**Ресурсы**  
- **Documentation:** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API Reference:** [API Details](https://reference.groupdocs.com/parser/java)  
- **Downloads:** [Latest Versions](https://releases.groupdocs.com/parser/java/)