# ReportMaker
## Описание
ReportMaker умеет создавать документы в форматах pdf, xlsx/xls, csv.

Для создания Pdf используется пакет [Dompdf](https://github.com/Dompdf/Dompdf)

Для создания Excel испольуется пакет [PhpSpreadsheet](https://github.com/PHPOffice/PhpSpreadsheet)

## Использование
### Создание Pdf
Пример создания можно посмотреть в examples/pdfExample/pdfExample.php

Чтобы создать Pdf, нужно создать шаблон twig.

Создаётся отдельная папка, в которой находятся все файлы,
связанные с шаблоном twig (css, fonts, images  и т.д.)

В конструкторе PDFReport можно указать имя twig-шаблона для генерации файла (По умолчанию имя шаблона - index.twig).

Можно создавать несколько шаблонов twig, использующих одни и те же стили, 
указывая нужный twig-шаблон в конструкторе PDFReport.

Метод generate возвращает содержимое созданного файла.

### Создание Excel
Примеры создания можно посмотреть в examples/excelExample/excelExample.php

Если нет excel-шаблона, на основе которого надо создать новый файл,
то можно передать массив с двумя полями: headers и data, 
и создастся таблица с заголовками из headers и данными из data

Если есть Excel-шаблон, то в нём производится только замена значений в конкретных ячейках.
Т.е. формулы, не пересчитываются.

Принято допущение, что в Excel-шаблонах не будет формул и элементов управления формами,
т.к. PhpSpreadsheet не пересчитывает автоматически формулы, 
переменные в которых связаны с заменяемыми ячейками, 
некорректно отображаются элементы управления формами.

Метод save сохраняет сгенерированный файл.

### Создание Csv
Для создания Csv надо передать массив данных, и разделитель (по умолчанию - ",")

Метод generate возвращает содержимое созданного файла.
