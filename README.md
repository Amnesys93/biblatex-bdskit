# biblatex-bdskit

**A BDS-inspired BibLaTeX citation and bibliography style for Bulgarian academic documents.**

`biblatex-bdskit` is a custom BibLaTeX style designed to provide a numeric citation and bibliography format inspired by Bulgarian bibliographic conventions and BDS requirements.

The project was developed primarily for use with **LaTeX, BibLaTeX, Biber and TeXworks**, with particular attention to academic documents written in Bulgarian and containing both Cyrillic and Latin bibliographic sources.

## Features

* Numeric citations in square brackets:

  ```text
  [1]
  ```

* Automatic sorting of multiple citations:

  ```text
  [5, 6, 11, 12, 13, 14]
  ```

* Automatic compression of consecutive citation numbers:

  ```text
  [5, 6, 11–14]
  ```

* Bibliography based on the `numeric-comp` BibLaTeX style.

* Biber backend support.

* Family-name-first author formatting.

* Bulgarian quotation marks for titles:

  ```text
  „Заглавие“
  ```

* Page formatting:

  ```text
  С. 353–400
  ```

* URL formatting:

  ```text
  URL: https://example.com
  ```

* DOI formatting:

  ```text
  DOI: 10.xxxx/xxxxx
  ```

* Designed for bibliographies containing both Cyrillic and Latin sources.

## Motivation

When preparing Bulgarian academic documents with LaTeX and BibLaTeX, finding a bibliography style that corresponds well to Bulgarian bibliographic conventions can be difficult.

Existing numeric bibliography styles do not always provide the desired formatting for Bulgarian academic documents. In particular, bibliographies containing both Cyrillic and Latin sources may require additional configuration to obtain the desired ordering and presentation.

`biblatex-bdskit` was created as a practical, open-source solution based on BibLaTeX and Biber.

The project is intended to provide a simple starting point that can be further developed and refined according to specific Bulgarian bibliographic requirements.

## Citation format

The citation style is based on `numeric-comp`.

A single citation:

```latex
\cite{reference1}
```

produces:

```text
[1]
```

Multiple citations:

```latex
\cite{reference5,reference6,reference11,reference12,reference13,reference14}
```

are sorted and compressed:

```text
[5, 6, 11–14]
```

The exact output depends on the bibliography database and the order in which references are assigned numbers.

## Installation

### Local project installation

The simplest way to use `biblatex-bdskit` is to place the following files in the same directory as your main `.tex` document:

```text
bdskit.bbx
bdskit.cbx
```

For example:

```text
my-project/
├── main.tex
├── references.bib
├── bdskit.bbx
└── bdskit.cbx
```

No system-wide installation is required.

## Usage

Load the style in the LaTeX preamble:

```latex
\usepackage[
    backend=biber,
    style=bdskit
]{biblatex}

\addbibresource{references.bib}
```

Cite sources normally:

```latex
\cite{reference1}
```

and print the bibliography:

```latex
\printbibliography
```

## Minimal example

```latex
\documentclass[a4paper,12pt]{article}

\usepackage[T2A]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[bulgarian,english]{babel}

\usepackage[
    backend=biber,
    style=bdskit
]{biblatex}

\addbibresource{example.bib}

\begin{document}

Това е пример за единично цитиране \cite{reference1}.

Това е пример за множество цитирания
\cite{reference5,reference6,reference11,reference12,reference13,reference14}.

\printbibliography

\end{document}
```

Compile using:

```text
LaTeX → Biber → LaTeX → LaTeX
```

When using TeXworks, make sure that **Biber** is used as the bibliography backend.

## Repository structure

```text
biblatex-bdskit/
│
├── bdskit.bbx
├── bdskit.cbx
├── README.md
├── LICENSE
├── CHANGELOG.md
│
└── examples/
    ├── example.tex
    └── example.bib
```

### Main files

| File           | Description             |
| -------------- | ----------------------- |
| `bdskit.bbx`   | Bibliography formatting |
| `bdskit.cbx`   | Citation formatting     |
| `README.md`    | Project documentation   |
| `CHANGELOG.md` | Version history         |
| `LICENSE`      | GNU GPL license         |
| `examples/`    | Example LaTeX project   |

## Current bibliography formatting

The current version provides the following basic formatting:

| Element            | Format             |
| ------------------ | ------------------ |
| Citation           | `[1]`              |
| Multiple citations | `[1, 2, 5–7]`      |
| Author             | `Фамилия И.`       |
| Title              | `„Заглавие“`       |
| Pages              | `С. 353–400`       |
| URL                | `URL: https://...` |
| DOI                | `DOI: 10.xxxx/...` |

## BDS compliance

This project should currently be considered **BDS-inspired** or **BDS-like**, rather than an official implementation of a Bulgarian State Standard.

The style represents a practical interpretation of Bulgarian bibliographic conventions. It has not been certified, approved or endorsed by the Bulgarian Institute for Standardization.

Users should verify the final bibliography against the requirements of their university, institution, publisher, journal or applicable BDS standard.

## Development status

The project is currently in an early development stage.

The initial release focuses on:

* numeric citations;
* citation sorting;
* citation compression;
* basic bibliography formatting;
* Cyrillic and Latin bibliographic data;
* integration with BibLaTeX and Biber.

Additional bibliographic entry types and more detailed BDS-specific formatting rules may be added in future releases.

## Roadmap

Planned improvements include:

* [ ] Books
* [ ] Journal articles
* [ ] Conference proceedings
* [ ] Standards
* [ ] Theses and dissertations
* [ ] Technical reports
* [ ] Online sources
* [ ] Edited books
* [ ] Chapters in edited books
* [ ] Institutional authors
* [ ] Multiple-author formatting
* [ ] Improved Cyrillic/Latin sorting
* [ ] Access-date formatting
* [ ] ISBN and ISSN formatting
* [ ] More precise DOI handling
* [ ] Additional BDS-specific formatting rules
* [ ] Extended test bibliography
* [ ] Automated regression tests

## Contributing

Contributions and corrections are welcome.

When reporting a formatting issue, please provide:

1. The relevant `.bib` entry.
2. The LaTeX command used for citation.
3. The actual output.
4. The expected output.
5. The relevant bibliographic requirement or standard, if applicable.

This information helps distinguish implementation errors from differences in interpretation of bibliographic requirements.

## License

`biblatex-bdskit` is released under the **GNU General Public License v3.0 or later (GPL-3.0-or-later)**.

See the [`LICENSE`](LICENSE) file for the complete license text.

## Citation

If `biblatex-bdskit` is used in an academic publication, thesis, dissertation or other scholarly work, please cite the project.

Suggested citation:

```text
Hristov, V. (2026). biblatex-bdskit: A BDS-inspired BibLaTeX citation
and bibliography style for Bulgarian academic documents.
GitHub repository.
```

## Disclaimer

This project is provided without warranty.

The author does not guarantee that the generated bibliography will satisfy every interpretation or implementation of Bulgarian bibliographic standards.

Users are responsible for checking the final bibliographic output against the requirements applicable to their specific institution, publisher, journal or academic work.
