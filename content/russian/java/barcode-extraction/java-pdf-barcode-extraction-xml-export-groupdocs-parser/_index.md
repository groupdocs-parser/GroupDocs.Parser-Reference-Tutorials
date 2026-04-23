---
date: '2026-02-19'
description: Узнайте, как считывать QR‑коды в PDF‑документах на Java с помощью GroupDocs.Parser
  и экспортировать данные штрихкода в XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Как считывать QR‑коды в PDF‑файлах Java с помощью GroupDocs.Parser
type: docs
url: /ru/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Как считывать QR‑коды в PDF‑файлах Java с помощью GroupDocs.Parser

В современных бизнес‑процессах **как считывать QR**‑коды из PDF‑документов может стать разницей между узким местом ручного ввода данных и полностью автоматизированным конвейером. Независимо от того, обрабатываете ли вы транспортные накладные, розничные чеки или каталоги продукции, быстрое и надёжное извлечение информации из QR‑кодов является обязательным. В этом руководстве мы покажем, как использовать **GroupDocs.Parser for Java** для чтения QR‑кодов (и других штрихкодов) из PDF и экспорта результатов в чистый XML‑файл, который могут использовать downstream‑системы.

## Быстрые ответы
- **Что делает GroupDocs.Parser for Java?** Он читает PDF‑файлы и извлекает структурированные данные, такие как штрихкоды.  
- **Как извлечь QR‑коды?** Настроив `BarcodeOptions` с типом QR и вызвав `parser.getBarcodes()`.  
- **Можно ли считывать QR‑коды в Java?** Да — установите тип штрихкода `"QR"` в параметрах.  
- **Нужна ли лицензия?** Пробная версия подходит для тестирования; для продакшн‑использования требуется коммерческая лицензия.  
- **Какая версия Java требуется?** Рекомендуется Java 8 или выше.

## Что означает «как считывать QR» в контексте обработки PDF?
Считывание QR‑кодов из PDF означает сканирование каждой страницы в поисках графики, закодированной в QR, декодирование встроенных данных и возврат их в удобном для программы формате. GroupDocs.Parser абстрагирует низкоуровневый анализ изображений, позволяя сосредоточиться на бизнес‑логике, а не на работе с пикселями.

## Почему стоит использовать GroupDocs.Parser для извлечения QR?
- **Высокая точность:** Встроенные алгоритмы обработки изображений работают с низкокачественными сканами.  
- **Опции производительности:** Выберите `QualityMode.Low` для скорости или `QualityMode.High` для максимальной точности.  
- **Поддержка разных форматов:** Работает с PDF, изображениями и даже документами Office, позволяя переиспользовать один и тот же код для разных типов файлов.

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

### Прямая загрузка
Либо загрузите последнюю JAR‑файл с [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Шаги получения лицензии
- **Бесплатная пробная версия:** 30‑дневный пробный период с полным набором функций.  
- **Временная лицензия:** Запросите временный ключ для расширенной оценки.  
- **Покупка:** Приобретите коммерческую лицензию для продакшн‑развертываний.

### Базовая инициализация и настройка
Создайте экземпляр `Parser`, указывающий на PDF, который нужно проанализировать:

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

## Как считывать QR‑коды в PDF‑файлах Java с помощью GroupDocs.Parser
### Шаг 1: Проверка поддержки штрихкодов
Прежде чем пытаться извлечь, убедитесь, что формат документа поддерживает сканирование штрихкодов:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Explanation:* Эта проверка предотвращает ошибки выполнения при неподдерживаемых типах файлов.

### Шаг 2: Настройка параметров штрихкода (Read QR codes Java)
Установите качество сканирования и укажите, что вас интересуют QR‑коды:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Explanation:* `QualityMode.Low` ускоряет обработку; переключитесь на `High`, если нужна повышенная точность. Параметр `"QR"` указывает движку искать только штрихкоды типа QR.

### Шаг 3: Извлечение данных QR
Получите информацию о штрихкодах со всех страниц PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Explanation:* `parser.getBarcodes` возвращает итерируемую коллекцию объектов `PageBarcodeArea`, каждый из которых содержит декодированное значение QR и его расположение на странице.

## Экспорт извлечённых данных в XML
### Шаг 4: Инициализация XML‑экспортера
Создайте экспортёр, который преобразует коллекцию штрихкодов в хорошо структурированный XML‑файл:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Explanation:* `XmlExporter` осуществляет сериализацию объектов штрихкода в стандартный XML, готовый для интеграции с ERP‑ или системами учёта.

### Шаг 5: Запись XML‑файла
Сохраните извлечённую информацию QR на диск:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Explanation:* В результате `data.xml` содержит один элемент `<Barcode>` на каждый QR‑код, с атрибутами номера страницы, координат и декодированного значения.

## Практические применения
1. **Управление запасами:** Автоматическое заполнение баз данных запасов путём чтения QR‑меток в PDF‑файлах входящих поставок.  
2. **Видимость цепочки поставок:** Отслеживание посылок в реальном времени путём извлечения QR‑идентификаторов, встроенных в логистические документы.  
3. **Розничные чеки:** Получение рекламной или гарантийной информации из QR‑кодов, напечатанных на цифровых чеках.

## Соображения по производительности
- **Управление памятью:** Для очень больших PDF обрабатывайте страницы потоково, а не загружайте весь файл в память.  
- **Выбор QualityMode:** Используйте `Low` для массовой обработки; переключайтесь на `High`, когда работаете с низкокачественными сканами.  
- **Обновления библиотеки:** Держите GroupDocs.Parser в актуальном состоянии, чтобы получать последние улучшения производительности и исправления ошибок.

## Распространённые проблемы и устранение неполадок
| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Штрихкоды не возвращаются | Указан неверный тип штрихкода | Измените `"QR"` на соответствующий тип (например, `"CODE_128"`). |
| Ошибка Out‑of‑memory при больших PDF | Весь документ загружается сразу | Обрабатывайте страницы по отдельности или увеличьте размер кучи JVM (`-Xmx2g`). |
| Пустой XML‑файл | `exportBarcodes` вызван до извлечения | Убедитесь, что `parser.getBarcodes(options)` возвращает данные перед экспортом. |

## Часто задаваемые вопросы
**Q: Можно ли извлекать штрихкоды из файлов изображений с помощью GroupDocs.Parser?**  
A: Да, библиотека поддерживает извлечение штрихкодов из распространённых форматов изображений (PNG, JPEG, TIFF).

**Q: Какие форматы штрихкодов распознаются?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 и многие другие. Смотрите документацию API для полного списка.

**Q: Как обрабатывать PDF с паролем?**  
A: Передайте пароль в конструктор `Parser`: `new Parser(filePath, "password")`.

**Q: Достаточна ли пробная версия для тестирования в продакшн?**  
A: Пробная версия предоставляет полный функционал, но добавляет водяной знак к извлечённым данным. Для продакшн‑использования приобретите коммерческую лицензию.

**Q: Что делать, если мой PDF содержит как QR, так и линейные штрихкоды?**  
A: Создайте несколько экземпляров `BarcodeOptions` или передайте массив типов, чтобы сканировать все необходимые форматы за один проход.

---

**Последнее обновление:** 2026-02-19  
**Тестировано с:** GroupDocs.Parser 25.5  
**Автор:** GroupDocs  

## Ресурсы
- [Документация GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Справочник API](https://reference.groupdocs.com/parser/java)
- [Скачать GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Репозиторий GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Бесплатный форум поддержки](https://forum.groupdocs.com/c/parser)
- [Заявка на временную лицензию](https://purchase.groupdocs.com/temporary-license/)

---