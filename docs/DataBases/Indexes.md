<sub>[Главная](../../index.md) / [Базы данных](README.md) / **Индексы** </sub>

# **Индексы SQL**

В SQL **индекс** - это структура данных, которая увеличивает скорость операций поиска данных в таблице базы данных за счет дополнительных записей и пространства памяти для поддержания структуры данных индекса. Индекс позволяет системе управления базами данных (СУБД) находить и извлекать определенные строки в таблице быстрее, чем при сканировании всей таблицы. Индексы могут быть созданы для одного или нескольких столбцов таблицы, причем для одной таблицы может быть создано несколько индексов. Различные типы индексов, такие как кластерные и некластерные индексы, могут использоваться в зависимости от конкретных потребностей базы данных и выполняемых в ней запросов.

**Кластеризованный индекс** - это тип индекса, который определяет физический порядок данных в таблице. Другими словами, строки данных таблицы хранятся на диске в том же порядке, что и строки в кластеризованном индексе. Для каждой таблицы может существовать только один кластеризованный индекс, поскольку строки данных могут быть физически отсортированы только одним способом.

С другой стороны, **некластеризованный индекс** - это тип индекса, который хранит копию индексируемых столбцов в отдельной структуре данных (с указателем на фактическую строку), а не сортирует фактические строки данных таблицы. Поскольку строки данных не сортируются, вы можете создать несколько некластеризованных индексов для одной таблицы.

Основное различие между кластеризованным и некластеризованным индексом заключается в способе хранения и извлечения данных. Кластеризованный индекс физически сортирует строки данных в таблице, что ускоряет поиск данных для запросов, использующих индексированные столбцы. Однако для хранения индекса требуется больше дискового пространства, а для обновления индексированных столбцов требуется больше дисковых операций ввода-вывода. Неклассифицированный индекс хранит копию индексированных столбцов отдельно и использует указатель для ссылки на фактические строки данных, что занимает меньше дискового пространства и более эффективно при записи. Однако он требует больше дискового ввода-вывода для извлечения данных, поскольку необходимо найти указатель в индексе, а затем найти фактическую строку данных.

Типы индексов:
- **Кластеризованный индекс**: Это единственный индекс, который может быть создан для каждой таблицы, и он определяет физический порядок данных в таблице.
- **Некластеризованный индекс**: хранит копию индексируемых столбцов отдельно и использует указатель для связи с фактическими строками данных.
- **Неуникальный некластеризованный индекс**: аналогичен некластеризованному индексу, но допускает дублирование значений в индексируемых столбцах.
- **Уникальный некластеризованный индекс**: аналогичен некластеризованному индексу, но не допускает дублирования значений в индексируемых столбцах.
- **Полнотекстовый индекс**: используется для операций текстового поиска и позволяет осуществлять быстрый полнотекстовый поиск в больших текстовых колонках.
- **Пространственный индекс**: используется для пространственных данных и позволяет быстро выполнять пространственные запросы.
- **XML-индекс**: используется для XML-данных и позволяет быстро выполнять XML-запросы.
- **Покрывающий индекс**: Это не конкретный тип индекса, а способ совместного использования нескольких индексов для повышения производительности запросов. Покрывающий индекс это набор индексов, которые вместе содержат все столбцы, необходимые для выполнения запроса, поэтому запрос может быть выполнен без обращения к основной таблице.
- **Частичные индексы**: индексы, которые создаются на подмножестве строк таблицы. Они могут быть полезны для индексирования столбцов с редким поиском или для индексирования только определенных условий столбца.

Другие типы индексов, характерные для определенных систем управления базами данных, включают растровые индексы, хэш-индексы и инвертированные индексы.
