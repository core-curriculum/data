# Medical Education Model Core Curriculum

Electronic data of the [Medical Education Model Core Curriculum (Revised Edition of 2023)](https://www.mext.go.jp/b_menu/shingi/chousa/koutou/116/toushin/mext_01280.html).

## Contents Published in This Repository

This repository contains data created by the research team of the Japan Society for Medical Education, a general incorporated association, which was selected for the Ministry of Education, Culture, Sports, Science and Technology's "Research and Study on the Status of Medical Personnel Training in Universities" project. The data is based on the [Medical Education Model Core Curriculum (Revised Edition of 2023)](https://www.mext.go.jp/b_menu/shingi/chousa/koutou/116/toushin/mext_01280.html) (hereinafter referred to as "Core Curriculum").

The content published as the [Core Curriculum](https://www.mext.go.jp/b_menu/shingi/chousa/koutou/116/toushin/mext_01280.html) (PDF version) is made available in more accessible formats (data versions), such as CSV and Markdown.

Currently, only parts equivalent to Chapters 1 and 2 of the PDF version are posted, but other chapters will be added in the future.

## Why is this project necessary?

PDF is an excellent format for producing print materials with high reproducibility and readability. However, extracting data from PDFs for use in statistical processing and research is challenging.

To utilize the Core Curriculum in the following areas, a file format that is more easily processed as data is necessary. Distributing the data in formats such as CSV and Markdown, which are compatible with data processing, enables the following applications:

- Collection and analysis of education program information at each university ([Institutional Research](https://doi.org/10.24489/jjphe.2018-012))
- Development of electronic syllabi and evaluation systems
- Creation of electronic books and websites for the dissemination of the Core Curriculum

## File Formats

The data in this repository is primarily distributed in the following file formats. Unless otherwise stated, the character encoding is UTF-8 (without BOM), except for CSV files, which are UTF-8 (with BOM) for compatibility with Excel.

| File Format | Character Encoding | Content |
|-------------|--------------------|---------|
| CSV         | UTF-8 (with BOM)   | Tabular data (mainly Chapters 1 and 2) |
| Markdown (.md) | UTF-8 (without BOM) | Document format data (other than above) |
| BibLaTeX (.bib) | UTF-8 (without BOM) | References |

## Differences between the PDF version and the data version

Due to the following reasons, there are differences between the PDF version and the data version in this repository:

- Ensuring strict data accuracy
- Maintaining the same data structure for both the English and Japanese versions
- Preventing errors caused by Japanese characters in certain applications
- Differences due to data formats

These differences include:

- CSV column names consist entirely of alphanumeric characters and some symbols
- [IDs](#indexes-and-ids) not mentioned in the PDF version are assigned to all items
    - To uniquely identify each item
    - To strictly demonstrate the relationships between items
- Changes have been made due to differences in data formats, such as:
    - In CSV files, slashes and boldface are expressed using Markdown formatting
    - In "Chapter 2: Qualities and Abilities," references to tables are written using the [Pandoc Markdown format](https://pandoc-doc-ja.readthedocs.io/ja/latest/users-guide.html#tables) for easier processing.

Despite these differences, the content of the data version is consistent with the content of the PDF version.

## Indexes and IDs

In the PDF version, **indexes** such as PR-01-02 and GE-02-01-01 are assigned at the beginning of Chapter 1 and Chapter 2 for qualities and abilities. Indexes are assigned sequentially for each item, corresponding to pages in a book.

In the data version, **IDs** are assigned to the qualities and abilities in Chapter 1 and Chapter 2, as well as to the separate tables and documents. IDs are unique identifiers expressed as URL-safe strings of a-zA-Z_- characters, generated from Unix timestamps (elapsed time since January 1, 1970, with 10-millisecond accuracy) at the time of item creation.

Indexes are relatively easy to understand since they are sequential, but if items are deleted or added in the future, the items that indexes point to may change. IDs will always point to the same item, even if items are deleted or added in the future. It is recommended to use IDs instead of indexes for precise data analysis and system creation.

| | Indexes | IDs |
|--|--|--|
| Listed in the PDF version | Yes | No |
| Assigned to | Qualities & Abilities | Qualities & Abilities, Separate Tables, Documents |
| May change due to revisions | Yes | No |
| Readability | ○ | × |

## Data Formats

### Qualities & Abilities (Chapter 1 & Chapter 2)

In the Core Curriculum, qualities and abilities are hierarchically represented from the largest first layer to the smallest and most detailed fourth layer. Qualities and abilities are stored in [outcomes](outcomes).

| File | Contents |
|-|-|
| [layer1.csv](outcomes/layer1.csv) | First layer of outcomes |
| [layer2.csv](outcomes/layer2.csv) | Second layer of outcomes |
| [layer3.csv](outcomes/layer3.csv) | Third layer of outcomes |
| [layer4.csv](outcomes/layer4.csv) | Fourth layer of outcomes |

The columns in each CSV file are as follows:

| Column | Existing Layer | Contents |
|-|-|-|
| index | First to Fourth layer | [Indexes](#indexes-and-ids) same as the PDF version |
| id | First to Fourth layer | Unique [IDs](#indexes-and-ids) for each item |
| spell | First layer | Correspondence between two-letter alphabets and qualities & abilities names |
| item | First to Fourth layer | Contents of the relevant item |
| description | First and Second layer | Overview of qualities & abilities |
| parent | Second and Third layer | Parent layer's [ID](#indexes-and-ids) (Second layer has First layer, Third layer has Second layer) |

### Separate Tables (Chapter 1 & Chapter 2)

In Chapter 1 and Chapter 2, some content is extracted as separate tables. These tables are referenced in the [layer3.csv](outcomes/layer3.csv) or [layer4.csv](outcomes/layer4.csv) files in the format of [@TBL:TBLxxxx]. The table data is stored in [tables](tables).

The list of tables and the data for each table are expressed in the [index.csv](tables/index.csv) file in the above folder as follows:

| Column | Contents |
|-|-|
| id | [ID](#indexes-and-ids) for the table itself |
| index | [Index](#indexes-and-ids) for the table itself (not listed in the PDF version) |
| item | Table name |
| file | Filename where the table data is stored |
| legend | Explanation of the table |
| number | Table number |
| columns | Correspondence between the column names in the PDF version |
| main | Column name for the main item in the table |

The table data is stored in the [tables](tables) folder with the specified filename. Unlike the PDF version, each item in the table is assigned an [index](#indexes-and-ids) and an [ID](#indexes-and-ids). The column names are alphanumeric. The correspondence between the column names in the PDF version is listed in the columns column. For example, in [TBL0202.csv](tables/TBL0202.csv), there are columns for category and item in addition to index and ID. The [index.csv](tables/index.csv) file lists "category:Classification,item:Items" in the columns column, so it can be understood that category corresponds to the classification in the PDF version and item corresponds to the item name in the PDF version.

### Other Data

- [2016 Core Curriculum (平成28年版コアカリ)](2016)
- [Correspondence between the 2016 Core Curriculum and the 2022 Core Curriculum (令和4年版コアカリ)](relations/y2016_to_y2022/)

## License

When using the contents of this repository, please use them in accordance with the "Ministry of Education, Culture, Sports, Science and Technology Website Terms of Use" (https://www.mext.go.jp/b_menu/1351168.htm). ([License](./LICENSE))
