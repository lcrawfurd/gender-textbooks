# Codebook: books.csv

One row per scored book; a book found more than once appears once (see search/v1/site/duplicates.csv in the repository). Licence: CC-BY 4.0, Center for Global Development.

| Column | Meaning |
|---|---|
| `id` | Stable book identifier: the paper corpus's id, or `s-` and the first 16 characters of the file's SHA-256 for a search book, or `c-` and the first 16 characters of the SHA-1 of the sorted ids of its files for a book that was published as chapter files and combined into one (see `parts`). |
| `file_sha256` | SHA-256 of the book's file (for some of the paper's books, of its text file, when no PDF was kept). Empty for a combined book, which has several files. |
| `title` | Title: as recorded at the source for search books; built from the archive path (country · grade · subject · file) for the paper's books, the `india-i4i` books and NGO collections. |
| `collection` | `national` (official English student textbooks: every headline result uses these only), `teacher-guides`, `readers`, `programme`, `excerpts` (files of a few pages from a source that posts only sample pages of each book, Lebanon's curriculum centre: not whole books, so in no headline or national result, whatever their kind), or an NGO collection. |
| `origin` | `paper-2024` (the 2024 paper's corpus), `india-i4i` (Indian state-board and NCERT textbooks, 2020-23 editions, from Lee Crawfurd's 2024 Ideas for India analysis, copied from an unofficial mirror, ncertbooks.guru: national textbooks, kept apart from the paper's in the check against the published paper), an NGO collection, or `search` (the systematic search, 2026). |
| `country` | Country name (World Bank naming). |
| `iso3` | ISO 3166-1 alpha-3 code. |
| `subnational` | The state or province whose own system the book belongs to (Texas, Sindh, Maharashtra...), empty for a national book. Such books are counted under their country in every result. For the paper's books, as the paper recorded it; for the `india-i4i` books, the state board (empty for NCERT, the national board); for search books, from the host that serves the file (search/v1/site/subnational.csv). |
| `region` | World Bank region. |
| `income_group` | World Bank income group. |
| `kind` | `student`, `teacher_guide` or `supplementary` for search books, as the search classified them (from the portal's label or the first pages of the file) unless the title names the kind. A title naming a teacher's guide makes any book a teacher guide (a "teacher guide (TG)" filed as a student book); a title naming a student book or a reader corrects a teacher guide, or a book with no kind (a "Student Textbook" filed as a teacher's guide is a student book); a title naming a supplementary, story or graded reader makes any book that is not a teacher guide supplementary, unless the title also names a student book, which wins. Four files whose titles contradict the files themselves follow the file. `student` for the paper's books; empty for the NGO collections. |
| `source_type` | `official` (a ministry or agency), `official_mirror`, `programme_repo` or `open_library`; `official` for the paper's books; `unofficial_mirror` for the `india-i4i` books; empty for the NGO collections. |
| `subject_raw` | Subject as labelled at the source. |
| `subject_group` | The paper's 13 subject groups; empty when unmapped. |
| `grade_raw` | Grade as labelled at the source. |
| `grade` | Grade, 1-13; empty when unknown. |
| `grade_band` | `primary` (grades 1-6), `lower` (7-9), `upper` (10-13) or `unknown`. |
| `year` | Publication year, where found in the book (its title or copyright page, or the PDF's metadata). Empty when unknown. |
| `words` | Words in the book's text. |
| `female` | Female gendered words (nouns and pronouns; the paper's word list, with "Ms" counted only when capitalised and "miss" excluded). |
| `male` | Male gendered words. |
| `female_share` | female / (female + male), rounded to 4 decimal places; empty when the book has no gendered words. |
| `child_female` | Female words referring to children. |
| `child_male` | Male words referring to children. |
| `adult_female` | Female words referring to adults. |
| `adult_male` | Male words referring to adults. |
| `female_subject` | Female words that are the grammatical subject of their sentence. |
| `female_object` | Female words that are a grammatical object. |
| `male_subject` | Male words that are the grammatical subject of their sentence. |
| `male_object` | Male words that are a grammatical object. |
| `occupations_json` | Occupations named near a gendered word, as JSON: term, category and female and male counts. |
| `source_url` | Where the book was found: a link to the file itself for search books and the Luminos collection; for the paper's books, the page of the country's source (not a link to the book); for the `india-i4i` books, the home page of the unofficial mirror they were copied from (ncertbooks.guru); empty where none is recorded. Books are never hosted here. |
| `parts` | Files the book was made of: 1 for a book that is one file; more for a book published as one file per chapter ("title: chapter 3"), whose chapters are combined into one row with their words and gendered words added, the title before the chapter marker, and the first file's link. A few sources post a book as one file per section or unit with titles that do not name the book (Ghana's Year 1 learner's materials, Taiwan's remedial English booklets, some of Sri Lanka's): their files are combined by grade and subject, titled "<subject>, <grade>" (or the paper's "country · grade · subject"). Separately published parts and volumes (Mathematics Part I and Part II) are not combined. |
