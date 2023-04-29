English Translation:

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

In the data version, unique IDs are assigned to each item in the Core Curriculum to ensure accurate identification and to demonstrate the relationships between items. The IDs consist of alphanumeric characters and symbols.

The IDs are assigned as follows:

- Core Curriculum: CC
- Part: P[part number]
- Chapter: C[chapter number]
- Section: S[section number]
- Table: T[table number]

Examples of ID assignment:

- Core Curriculum ID: CC
- Part 1 ID: P1
- Chapter 1 ID: P1C1
- Section 1.1 ID: P1C1S1
- Table 1.1 ID: P1C1S1T1

## How to Use the Data

You can use the data in this repository for various purposes, such as data analysis, creating electronic syllabi, and developing evaluation systems. To do so, download the data in the desired file format (CSV, Markdown, or BibLaTeX) and import it into your preferred application.

Please note that when using this data, you should follow the terms specified in the [license](#license) section below.

## License

The data in this repository is licensed under the [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/), which allows you to:

- Share (copy and redistribute the material in any medium or format)
- Adapt (remix, transform, and build upon the material for any purpose, even commercially)

Under the following terms:

- Attribution (you must give appropriate credit, provide a link to the license, and indicate if changes were made)

Please refer to the [LICENSE](LICENSE) file for more information.

## Acknowledgments

This repository is the result of the efforts of the research team of the Japan Society for Medical Education, a general incorporated association, selected for the Ministry of Education, Culture, Sports, Science and Technology's "Research and Study on the Status of Medical Personnel Training in Universities" project. We would like to express our gratitude to everyone involved in the project and the creation of the Core Curriculum.
