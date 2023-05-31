# The Model Core Curriculum for Medical Education

Electronic data of [the Model Core Curriculum for Medical Education (Revised Edition of 2023)](https://www.mext.go.jp/b_menu/shingi/chousa/koutou/116/toushin/mext_01280.html).

## Contents shared in this repository

This repository contains data created by the Model Core Curriculum Expert Research Committee of the Japan Society for Medical Education, which was selected for research and study commission project by the Ministry of Education, Culture, Sports, Science and Technology. The data is based on the [the Model Core Curriculum for Medical Education (Revised Edition of 2023)](https://www.mext.go.jp/b_menu/shingi/chousa/koutou/116/toushin/mext_01280.html) (hereinafter referred to as "Core Curriculum").

The content shared as [the Model Core Curriculum (PDF version) ](https://www.mext.go.jp/b_menu/shingi/chousa/koutou/116/toushin/mext_01280.html) (PDF version) is available in accessible formats (data versions), such as CSV and Markdown.

Currently, the contents includes the parts corresponding to Chapter 1 and Chapter 2 in the PDF version. However, we plan to add the other chapters in the future.

## Why is this project necessary?

PDF is an excellent format for producing print materials with high reproducibility and readability. However, extracting data from PDFs for use in statistical processing and research is challenging.

To utilize the Model Core Curriculum for the following aims, a file format that is more easily processed as data is necessary. Distributing the data in formats such as CSV and Markdown, which are compatible with data processing, enables the following applications:

- Collection and analysis of information about education program in each university ([Institutional Research](https://doi.org/10.24489/jjphe.2018-012))
- Development of electronic syllabi and evaluation systems
- Creation of electronic books and websites for the dissemination of the Model Core Curriculum

## Formats of file

The data in this repository is primarily distributed in the following formats. If there are no specific instructions, the character encoding is UTF-8 (without BOM), except for CSV files, which are UTF-8 (with BOM) for compatibility with Excel.

| Formats of file | Character Encoding  | Content                                 |
| --------------- | ------------------- | --------------------------------------- |
| CSV             | UTF-8 (with BOM)    | Table data (mainly Chapters 1 and 2)    |
| Markdown (.md)  | UTF-8 (without BOM) | Document format data (other than above) |
| BibLaTeX (.bib) | UTF-8 (without BOM) | References                              |

## Differences between the PDF version and the data version

- Ensuring strict data accuracy
- Maintaining the same data structure for both the English and Japanese versions
- Preventing errors caused by Japanese characters in certain applications
- Differences due to data formats

Due to these reasons, there are differences between the PDF version and the data version in this repository. These differences include:

- CSV column names consist entirely of alphanumeric characters and some symbols
- [ids](#indexes-and-ids) not mentioned in the PDF version are assigned to all items
    - To uniquely identify each item
    - To strictly demonstrate the relationships between items
- Changes have been made due to differences in data formats, such as:
    - In CSV files, slashes and boldface are expressed using Markdown formatting
    - In "Chapter 2: Learning Objectives," references to tables are written using the [Pandoc Markdown format](https://pandoc.org/MANUAL.html#pandocs-markdown) for easier processing.
    - The reference citations are not directly included in the document but are referenced from the contents of the "citations.bib" file instead. 
    - In Markdown, elements such as boxed or framed text cannot be directly expressed are converted into different formats.


## Indexes and ids

In the PDF version, indexes such as PR-01-02 and GE-02-01-01 are assigned at the beginning of Chapter 1 and Chapter 2 for learning objectives. Indexes are assigned sequentially for each item, corresponding to pages in a book.

In the data version, **ids** are assigned to the learning objectives in Chapter 1 and Chapter 2, as well as to the tables and documents. ids are unique identifiers expressed as URL-safe strings of a-zA-Z_- characters, generated from Unix timestamps (elapsed time since January 1, 1970, with 10-millisecond accuracy) at the time of item creation.

Indexes are relatively easy to understand since they are sequential, however, if items are deleted or added in the future, the items that indexes correspond may change. ids will always correspond the same items, even if items are deleted or added in the future. It is **recommended to use ids** instead of indexes for precise data analysis and system creation.

|                                           | Indexes             | ids                                   |
| ----------------------------------------- | ------------------- | ------------------------------------- |
| Listed in the PDF version                 | Yes                 | No                                    |
| Assigned items                            | Learning objectives | Learning objectives,Tables, Documents |
| Possibilities for change due to revisions | Yes                 | No                                    |
| Readability                               | good                | poor                                  |

## Data Formats

### Basic Qualities and Abilities, and Learning objectives (Chapter 1 & Chapter 2)

In the Model Core Curriculum, Learning objectives are hierarchically represented from the largest first layer to the smallest and most detailed fourth layer. Learning objectives are stored in [outcomes](outcomes).

| File                              | Contents                            |
| --------------------------------- | ----------------------------------- |
| [layer1.csv](outcomes/layer1.csv) | First layer of Learning objectives  |
| [layer2.csv](outcomes/layer2.csv) | Second layer of Learning objectives |
| [layer3.csv](outcomes/layer3.csv) | Third layer of Learning objectives  |
| [layer4.csv](outcomes/layer4.csv) | Fourth layer of Learning objectives |

The columns in each CSV file are as follows:

| Column      | Existing Layer         | Contents                                                                                                                           |
| ----------- | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| index       | First to Fourth layer  | [Indexes](#indexes-and-ids) same as the PDF version                                                                                |
| id          | First to Fourth layer  | Unique [ids](#indexes-and-ids) for each item                                                                                       |
| spell       | First layer            | Correspondence between two-letter alphabets and names of Basic Qualities and Abilities                                             |
| item        | First to Fourth layer  | Contents of the relevant item                                                                                                      |
| description | First and Second layer | Overview of Basic Qualities and Abilities                                                                                          |
| parent      | Second to Force layer  | Parent layer's [id](#indexes-and-ids) (Second layer for First layer, Third layer fo Second layer, and Forth layer for Third layer) |

### Separate Tables (Chapter 1 & Chapter 2)

In Chapter 1 and Chapter 2, some content is extracted as tables. These tables are referenced in the [layer3.csv](outcomes/layer3.csv) or [layer4.csv](outcomes/layer4.csv) files in the format of [@TBL:TBLxxxx]. The table data is stored in [tables](tables).

The list of Tables and the data for each table are expressed in the [index.csv](tables/index.csv) file in the above folder as follows:

| Column  | Contents                                                                       |
| ------- | ------------------------------------------------------------------------------ |
| id      | [id](#indexes-and-ids) for the table itself                                    |
| index   | [Index](#indexes-and-ids) for the table itself (not listed in the PDF version) |
| item    | Name of table                                                                  |
| file    | Name of file where the table data is stored                                    |
| legend  | Explanation of the table                                                       |
| number  | Table number                                                                   |
| columns | Correspondence between the names of column in the PDF version                  |
| main    | Name of column for the main item in the table                                  |

The table data is stored in the [tables](tables) folder with the specified filename. Unlike the PDF version, each item is assigned an [index](#indexes-and-ids) and an [id](#indexes-and-ids). The names of column are alphanumeric. The correspondence between the names of column in the PDF version is listed in the columns columns. For example, in [TBL0202.csv](tables/TBL0202.csv), there are columns for category and item in addition to index and id. The [index.csv](tables/index.csv) file lists "category:Classification,item:Items" in the columns, so it can be understood that category corresponds to the classification in the PDF version and item corresponds to the name of item in the PDF version.

## License

When using the contents of this repository, please follow the "Terms of Use in Ministry of Education, Culture, Sports, Science and Technology Website" (https://www.mext.go.jp/b_menu/1351168.htm). ([License](./LICENSE))
