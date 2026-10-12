---
date: '2026-10-12'
description: Узнайте, как извлечь QR из PDF в Java с использованием GroupDocs.Parser
  и экспортировать данные штрих‑кода в XML для последующей обработки.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Узнайте, как извлечь QR из PDF в Java с использованием GroupDocs.Parser
  и экспортировать данные штрих‑кода в XML для последующей обработки.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Как извлечь QR из PDF в Java с помощью GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: Как извлечь QR из PDF в Java с помощью GroupDocs.Parser
type: docs
url: /ru/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Как извлечь QR из PDF в Java с помощью GroupDocs.Parser

В современных бизнес‑процессах **извлечение QR из PDF** файлов может превратить узкое место ручного ввода данных в полностью автоматизированный конвейер. Независимо от того, работаете ли вы с транспортными накладными, розничными чеками или каталогами продукции, быстрое и надёжное получение информации из QR‑кодов имеет решающее значение для последующих систем. В этом руководстве мы покажем, как использовать **GroupDocs.Parser for Java** для чтения QR‑кодов (и других штрихкодов) из PDF и экспорта результатов в чистый XML‑файл, который может потреблять ваша ERP‑система, система учёта или аналитическая платформа.

## Быстрые ответы
- **Что делает GroupDocs.Parser for Java?** Он читает PDF‑файлы и извлекает структурированные данные, такие как штрихкоды, таблицы и текст.  
- **Как извлечь QR‑коды?** Настройте `BarcodeOptions` с типом QR и вызовите `parser.getBarcodes()`.  
- **Могу ли я читать QR‑коды в Java?** Да — установите тип штрихкода `"QR"` в параметрах.  
- **Нужна ли лицензия?** Пробная версия подходит для тестирования; для продакшна требуется коммерческая лицензия.  
- **Какая версия Java требуется?** Рекомендуется Java 8 или новее.

## Что означает «извлечение QR из PDF» в контексте обработки PDF?
Извлечение QR из PDF означает сканирование каждой страницы в поисках графики, закодированной QR, декодирование встроенных данных и возврат их в удобном для программы формате. GroupDocs.Parser абстрагирует низкоуровневый анализ изображений, позволяя сосредоточиться на бизнес‑логике, а не на работе с пикселями.

## Почему стоит использовать GroupDocs.Parser для извлечения QR?
GroupDocs.Parser поддерживает **более 30 форматов ввода** и может обрабатывать PDF до **500 МБ** без загрузки всего файла в память, обеспечивая высокую точность даже при сканировании с низким разрешением. Вы можете выбрать `QualityMode.Low` для скорости или `QualityMode.High` для максимальной точности, и тот же API работает с PDF, изображениями и документами Office, устраняя необходимость в нескольких библиотеках.

## Предварительные требования
- **GroupDocs.Parser for Java** (версия 25.5 или новее).  
- Maven или ручная загрузка JAR.  
- Среда разработки Java 8+ (IntelliJ IDEA, Eclipse или любой редактор).  

## Настройка GroupDocs.Parser для Java
### Использование Maven
Добавьте репозиторий GroupDocs и зависимость в ваш `pom.xml`:

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

### Прямая загрузка
В качестве альтернативы загрузите последнюю JAR‑файл с [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Шаги получения лицензии
- **Free trial:** 30‑дневная пробная версия с полным набором функций.  
- **Temporary license:** Запросите временный ключ для расширенной оценки.  
- **Purchase:** Приобретите коммерческую лицензию для продакшн‑развертываний.

### Базовая инициализация и настройка
Создайте экземпляр `Parser`, указывающий на PDF, который вы хотите проанализировать:

`Parser` — основной класс в GroupDocs.Parser, представляющий документ и предоставляющий методы для извлечения содержимого, такого как текст, таблицы и штрихкоды.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Как читать QR‑коды в PDF на Java с помощью GroupDocs.Parser
Чтение QR‑кодов в PDF на Java с помощью GroupDocs.Parser включает создание экземпляра парсера, настройку параметров штрихкода для поиска QR‑типов, вызов метода извлечения штрихкодов и последующую обработку возвращённых объектов штрихкода. Процесс прост, работает на любой странице PDF и возвращает декодированные значения вместе с метаданными позиции для дальнейшей обработки.

### Шаг 1: проверка поддержки штрихкода
Перед попыткой извлечения убедитесь, что формат документа поддерживает сканирование штрихкодов:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Объяснение:* Эта проверка предотвращает ошибки выполнения при работе с неподдерживаемыми типами файлов.

### Шаг 2: настройка параметров штрихкода (чтение QR‑кодов Java)
`BarcodeOptions` — объект конфигурации, позволяющий указать, какие символьные наборы штрихкодов обнаруживать, установить режим качества сканирования и точно настроить параметры, такие как пороги обнаружения, обеспечивая оптимальную производительность для целевых QR‑кодов.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Объяснение:* `QualityMode.Low` ускоряет обработку; переключитесь на `High`, если нужна повышенная точность. Аргумент `"QR"` указывает движку искать только штрихкоды типа QR.

### Шаг 3: извлечение данных QR
`parser.getBarcodes(options)` сканирует документ с использованием предоставленных `BarcodeOptions` и возвращает коллекцию объектов `PageBarcodeArea`, каждый из которых содержит декодированное значение QR, номер страницы и точные координаты штрихкода на странице, позволяя точно обрабатывать их в последующих системах.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Объяснение:* `parser.getBarcodes` возвращает итерируемую коллекцию объектов `PageBarcodeArea`, каждый из которых содержит декодированное значение QR и его расположение на странице.

## Экспорт извлечённых данных в XML
### Шаг 4: инициализация XML‑экспортера
`XmlExporter` — утилитный класс, преобразующий коллекцию объектов штрихкода в хорошо структурированный XML‑документ, автоматически создающий элементы для каждого штрихкода с атрибутами индекса страницы, позиции и декодированного значения, которые затем можно сохранить или передать другим системам.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Объяснение:* `XmlExporter` обрабатывает сериализацию объектов штрихкода в стандартный XML, готовый для интеграции с ERP‑ или системами учёта.

### Шаг 5: запись XML‑файла
Сохраните извлечённую информацию QR на диск:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Объяснение:* Полученный `data.xml` содержит один элемент `<Barcode>` на каждый QR‑код, с атрибутами номера страницы, координат и декодированного значения.

## Практические применения
1. **Управление запасами:** Автоматически заполнять базы данных запасов, считывая QR‑метки на входящих PDF‑накладных.  
2. **Видимость цепочки поставок:** Отслеживать посылки в реальном времени, извлекая QR‑идентификаторы, встроенные в логистические документы.  
3. **Розничные чеки:** Получать рекламную или гарантийную информацию из QR‑кодов, напечатанных на цифровых чеках.

## Соображения по производительности
- **Memory management:** Для очень больших PDF обрабатывайте страницы потоково, а не загружайте весь файл в память.  
- **QualityMode selection:** Используйте `Low` для массовой обработки; переключайтесь на `High`, когда работаете с сканами низкого разрешения.  
- **Library updates:** Обновляйте GroupDocs.Parser до последней версии, чтобы воспользоваться новейшими улучшениями производительности и исправлениями ошибок.

## Распространённые проблемы и устранение неполадок
| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Штрихкоды не возвращаются | Указан неверный тип штрихкода | Измените `"QR"` на соответствующий тип (например, `"CODE_128"`). |
| Ошибка Out‑of‑memory при больших PDF | Весь документ загружается сразу | Обрабатывайте страницы по отдельности или увеличьте размер кучи JVM (`-Xmx2g`). |
| Пустой XML‑файл | `exportBarcodes` вызван до извлечения | Убедитесь, что `parser.getBarcodes(options)` возвращает данные перед экспортом. |

## Часто задаваемые вопросы
**Q: Могу ли я извлекать штрихкоды из файлов изображений с помощью GroupDocs.Parser?**  
A: Да, библиотека поддерживает извлечение штрихкодов из распространённых форматов изображений (PNG, JPEG, TIFF).

**Q: Какие форматы штрихкодов распознаются?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 и многие другие. Обратитесь к документации API для полного списка.

**Q: Как обрабатывать PDF, защищённые паролем?**  
A: Передайте пароль в конструктор `Parser`: `new Parser(filePath, "password")`.

**Q: Достаточна ли пробная версия для тестирования в продакшн?**  
A: Пробная версия предоставляет полный набор функций, но добавляет водяной знак к извлечённым данным. Для продакшна приобретите коммерческую лицензию.

**Q: Что делать, если мой PDF содержит как QR, так и линейные штрихкоды?**  
A: Создайте несколько экземпляров `BarcodeOptions` или передайте массив типов, чтобы сканировать все необходимые форматы за один проход.

**Последнее обновление:** 2026-10-12  
**Тестировано с:** GroupDocs.Parser 25.5  
**Автор:** GroupDocs  

## Ресурсы
- [Документация GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Справочник API](https://reference.groupdocs.com/parser/java)
- [Скачать GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Репозиторий GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Форум бесплатной поддержки](https://forum.groupdocs.com/c/parser)
- [Заявка на временную лицензию](https://purchase.groupdocs.com/temporary-license/)

## Связанные руководства

- [Извлечение штрихкода PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Как загрузить PDF из URL с помощью GroupDocs.Parser for Java](/parser/java/document-loading/)
- [Извлечение данных формы PDF с помощью GroupDocs.Parser в Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)